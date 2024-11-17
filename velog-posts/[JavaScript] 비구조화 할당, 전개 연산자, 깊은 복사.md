<h2 id="1-비구조화-할당"><strong>1. 비구조화 할당</strong></h2>
<h3 id="배열의-비구조화-할당"><strong>배열의 비구조화 할당</strong></h3>
<p>배열의 비구조화 할당은 배열의 요소를 개별 변수로 쉽게 추출하거나, 나머지 요소를 새로운 배열로 저장할 수 있도록 도와줍니다.</p>
<pre><code class="language-jsx">// 기본적인 배열 비구조화 할당
const numbers = [1, 2, 3, 4, 5];
const [first, second, ...rest] = numbers;

console.log(first);  // 출력: 1
console.log(second); // 출력: 2
console.log(rest);   // 출력: [3, 4, 5]

// 기본값 설정
const [a, b, c = 3] = [1, 2];
console.log(a, b, c); // 출력: 1 2 3

// 변수 교환
let x = 1;
let y = 2;
[x, y] = [y, x];
console.log(x, y); // 출력: 2 1</code></pre>
<h3 id="객체의-비구조화-할당"><strong>객체의 비구조화 할당</strong></h3>
<p>객체의 비구조화 할당은 객체 속성을 개별 변수로 추출할 수 있게 해줍니다. 변수 이름 변경(맵핑)이나 기본값 설정도 가능합니다.</p>
<pre><code class="language-jsx">// 기본적인 객체 비구조화 할당
const person = { name: '홍길동', age: 30 };
const { name, age } = person;

console.log(name); // 출력: '홍길동'
console.log(age);  // 출력: 30

// 변수 이름 변경(맵핑)과 기본값 설정
const { name: personName, job = '개발자' } = person;
console.log(personName); // 출력: '홍길동'
console.log(job);        // 출력: '개발자'</code></pre>
<h3 id="중첩-객체-비구조화-할당"><strong>중첩 객체 비구조화 할당</strong></h3>
<p>중첩된 객체의 속성을 추출할 때도 비구조화 할당을 활용할 수 있습니다.</p>
<pre><code class="language-jsx">const user = {
  id: 42,
  name: '이영희',
  address: {
    city: '서울',
    country: '대한민국'
  }
};

const { name, address: { city, country } } = user;

console.log(name);    // 출력: '이영희'
console.log(city);    // 출력: '서울'
console.log(country); // 출력: '대한민국'</code></pre>
<h3 id="함수에서-객체-비구조화-활용"><strong>함수에서 객체 비구조화 활용</strong></h3>
<p>함수 매개변수에서도 비구조화 할당을 사용하면 코드 가독성이 높아집니다.</p>
<pre><code class="language-jsx">function printPersonInfo({ name, age, job = '무직' }) {
  console.log(`이름: ${name}, 나이: ${age}, 직업: ${job}`);
}

const person = { name: '김철수', age: 25 };
printPersonInfo(person); // 출력: 이름: 김철수, 나이: 25, 직업: 무직</code></pre>
<h2 id="2-전개-연산자-spread-operator"><strong>2. 전개 연산자 (Spread Operator)</strong></h2>
<p>전개 연산자는 배열이나 객체를 개별 요소로 펼치거나 복사하는 데 유용합니다.</p>
<h3 id="배열에서의-사용"><strong>배열에서의 사용</strong></h3>
<pre><code class="language-jsx">// 배열 복사와 결합
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];

console.log(arr2); // 출력: [1, 2, 3, 4, 5</code></pre>
<h3 id="객체에서의-사용"><strong>객체에서의 사용</strong></h3>
<pre><code class="language-jsx">// 객체 복사와 속성 덮어쓰기
const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj1, b: 3 };

console.log(obj2); // 출력: { a: 1, b: 3 }</code></pre>
<h3 id="함수-호출-시-사용"><strong>함수 호출 시 사용</strong></h3>
<p>전개 연산자를 사용하면 배열을 함수의 개별 인자로 전달할 수 있습니다.</p>
<pre><code class="language-jsx">function sum(...numbers) {
  return numbers.reduce((total, num) =&gt; total + num, 0);
}

console.log(sum(1, 2, 3, 4)); // 출력: 10</code></pre>
<h2 id="3-깊은-복사-deep-copy"><strong>3. 깊은 복사 (Deep Copy)</strong></h2>
<h3 id="json-활용"><strong>JSON 활용</strong></h3>
<p><code>JSON.stringify()</code>와 <code>JSON.parse()</code>를 조합하여 객체나 배열의 깊은 복사를 수행할 수 있습니다.</p>
<pre><code class="language-jsx">// 객체 깊은 복사
const originalObj = { a: 1, b: { c: 2 } };
const deepCopyObj = JSON.parse(JSON.stringify(originalObj));

console.log(deepCopyObj); // 출력: { a: 1, b: { c: 2 } }
console.log(originalObj.b === deepCopyObj.b); // 출력: false

// 배열 깊은 복사
const originalArray = [1, [2, 3], { d: 4 }];
const deepCopyArray = JSON.parse(JSON.stringify(originalArray));

console.log(deepCopyArray); // 출력: [1, [2, 3], { d: 4 }]
console.log(originalArray[1] === deepCopyArray[1]); // 출력: false
console.log(originalArray[2] === deepCopyArray[2]); // 출력: false</code></pre>
<blockquote>
<p>주의:</p>
<ul>
<li>이 방법은 <code>undefined</code>, 함수, <code>Symbol</code> 같은 데이터는 복사하지 못합니다.</li>
<li>순환 참조가 있는 객체는 에러를 발생시킬 수 있습니다.</li>
</ul>
</blockquote>
<h3 id="jsonstringify와-jsonparse의-역할"><strong>JSON.stringify()와 JSON.parse()의 역할</strong></h3>
<p><strong><code>JSON.stringify(originalObj)</code></strong></p>
<ul>
<li>객체를 <strong>JSON 문자열</strong>로 변환합니다.</li>
<li>JSON 문자열은 단순 텍스트 형식이므로 객체의 구조를 표현하되, 참조를 끊어냅니다.</li>
</ul>
<pre><code class="language-jsx">const originalObj = { a: 1, b: { c: 2 } };
const jsonString = JSON.stringify(originalObj);

console.log(jsonString); // 출력: '{&quot;a&quot;:1,&quot;b&quot;:{&quot;c&quot;:2}}'</code></pre>
<p><strong><code>JSON.parse(jsonString)</code></strong></p>
<ul>
<li>JSON 문자열을 다시 <strong>JavaScript 객체</strong>로 변환합니다.</li>
<li>이 과정에서 새로운 객체가 생성되며 원본 객체와 독립적인 새로운 데이터 구조를 갖게 됩니다.</li>
</ul>
<pre><code class="language-jsx">const jsonString = '{&quot;a&quot;:1,&quot;b&quot;:{&quot;c&quot;:2}}';
const newObject = JSON.parse(jsonString);

console.log(newObject); // 출력: { a: 1, b: { c: 2 } }</code></pre>