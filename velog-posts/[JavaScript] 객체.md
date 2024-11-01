<h2 id="객체-정의">객체 정의</h2>
<p><strong><code>객체</code></strong>: 키와 값으로 구성된 속성들의 집합</p>
<p>키(key)와 값(value)을 합쳐서 프로퍼티(property, 속성)라고 함</p>
<h3 id="객체-문법">객체 문법</h3>
<p>중괄호 선언</p>
<pre><code class="language-jsx">const person = {
  name: &quot;철수&quot;,
  age: 18
};</code></pre>
<h3 id="객체의-다양한-속성-값">객체의 다양한 속성 값</h3>
<p>객체의 속성 값으로 다양한 데이터 타입 포함 가능. 문자열, 숫자, 불리언, 배열, 다른 객체 등 모두 가능.</p>
<p>예시</p>
<pre><code class="language-jsx">const user = {
  name: {
    korean: &quot;리쿠&quot;,
    japanese: &quot;リク&quot;
  },
  age: 20,
  languages: [&quot;한국어&quot;, &quot;일본어&quot;],
  address: {
    city: &quot;후쿠이현&quot;,
    country: &quot;일본&quot;
  }
};

console.log(user.name.korean); // &quot;리쿠&quot;
console.log(user.name.japanese); // &quot;リク&quot;
console.log(user.languages[0]); // &quot;한국어&quot;
console.log(user.address.city); // &quot;후쿠이현&quot;</code></pre>
<h2 id="객체-생성-방법">객체 생성 방법</h2>
<ol>
<li><p><strong>객체 리터럴 사용</strong> (가장 일반적인 방법)</p>
<pre><code class="language-jsx"> const person = {
   name: &quot;철수&quot;,
   age: 18
 };

 console.log(person); // { name: &quot;철수&quot;, age: 18 } 출력됨</code></pre>
</li>
<li><p><strong>new Object() 생성자 함수 사용</strong>
빈 객체 생성 후 속성 추가</p>
<pre><code class="language-jsx"> const person = new Object();
 person.name = &quot;철수&quot;;
 person.age = 18;

 console.log(person); // { name: &quot;철수&quot;, age: 18 } 출력됨</code></pre>
</li>
<li><p><strong>Object.create() 메서드 사용</strong>
지정된 프로토타입 객체 기반으로 새 객체 생성. 상속 구현에 유용</p>
<pre><code class="language-jsx"> const personPrototype = {
   greet: function() {
     console.log(&quot;안녕하세요!&quot;);
   }
 };

 const person = Object.create(personPrototype);
 person.name = &quot;철수&quot;;
 person.age = 18;

 console.log(person); // { name: &quot;철수&quot;, age: 18 } 출력됨
 person.greet(); // &quot;안녕하세요!&quot; 출력됨</code></pre>
</li>
<li><p><strong>생성자 함수 정의 및 사용</strong></p>
<pre><code class="language-jsx"> function Person(name, age) {
   this.name = name;
   this.age = age;
 }

 const person = new Person(&quot;철수&quot;, 18);

 console.log(person); // Person { name: &quot;철수&quot;, age: 18 } 출력됨</code></pre>
</li>
</ol>
<h3 id="리터럴-표기법">리터럴 표기법</h3>
<p>JavaScript는 간편한 <strong>리터럴 표기법</strong>을 제공하여 데이터를 쉽게 정의하고 사용할 수 있게 함. 이 <strong>단축 문법</strong>으로 각 자료를 효율적으로 지정 가능.</p>
<p>예시</p>
<pre><code class="language-jsx">// 객체 리터럴
const person = { name: &quot;철수&quot;, age: 18 };

// 배열 리터럴
const numbers = [1, 2, 3, 4, 5];

// 문자열 리터럴
const greeting = &quot;안녕하세요&quot;;

// 숫자 리터럴
const pi = 3.14;

// 불리언 리터럴
const isTrue = true;

// 함수 리터럴 (화살표 함수)
const add = (a, b) =&gt; a + b;</code></pre>
<h2 id="객체-속성-접근-방법">객체 속성 접근 방법</h2>
<h3 id="1-마침표-표기법">1. 마침표(.) 표기법</h3>
<p>객체 속성에 접근하는 <strong>가장 일반적인 방법</strong>. 마침표 사용</p>
<pre><code class="language-jsx">const person = { name: &quot;윤지&quot;, age: 18 };
console.log(person.name); // &quot;윤지&quot; 출력됨</code></pre>
<h3 id="2-대괄호-표기법">2. 대괄호([]) 표기법</h3>
<p>속성 이름을 문자열로 사용. 동적 접근이나 특수 문자, 공백 포함 시 유용</p>
<pre><code class="language-jsx">const person = { name: &quot;윤지&quot;, &quot;favorite-color&quot;: &quot;blue&quot; };
console.log(person[&quot;favorite-color&quot;]); // &quot;blue&quot; 출력됨</code></pre>
<p>차이점:</p>
<ul>
<li>마침표: 간결하지만 유효한 식별자만 가능</li>
<li>대괄호: 더 유연하며 동적 접근 가능</li>
</ul>
<p><strong>마침표 표기법을 주로 사용하되, 대괄호 표기법이 필요한 경우는?</strong></p>
<ol>
<li><p>속성 이름에 특수 문자나 공백이 포함된 경우</p>
<pre><code class="language-jsx"> const obj = { &quot;special-key&quot;: &quot;value&quot; };
 console.log(obj[&quot;special-key&quot;]); // &quot;value&quot;</code></pre>
</li>
<li><p>속성 이름을 동적으로 결정할 때 (변수로 접근)</p>
<pre><code class="language-jsx"> const key = &quot;name&quot;;
 const person = { name: &quot;철수&quot; };
 console.log(person[key]); // &quot;철수&quot;</code></pre>
</li>
<li><p>객체의 모든 속성을 순회할 때 (반복문 사용)</p>
<pre><code class="language-jsx"> const person = { name: &quot;철수&quot;, age: 18, city: &quot;서울&quot; };
 for (let key in person) {
   console.log(`${key}: ${person[key]}`);
 }
 // 출력:
 // name: 철수
 // age: 18
 // city: 서울</code></pre>
</li>
</ol>
<p><strong>객체는 존재하지 않는 속성에 접근 가능</strong></p>
<pre><code class="language-jsx">const person = {
  name: &quot;철수&quot;
};

console.log(person.age); // undefined 출력됨
console.log(person.height); // undefined 출력됨

// 조건문에서 활용
if (person.age === undefined) {
  console.log(&quot;age 속성이 정의되지 않음&quot;);
}</code></pre>
<ul>
<li>객체에 존재하지 않는 속성에 접근하면 에러가 발생하지 않고 <code>undefined</code>를 반환</li>
<li>JavaScript의 특징으로, 개발자가 유연하게 객체를 다룰 수 있게 함</li>
</ul>
<h2 id="동적으로-객체-제어추가수정삭제">동적으로 객체 제어(추가/수정/삭제)</h2>
<h3 id="객체-속성-추가">객체 속성 추가</h3>
<p>객체의 속성에 접근해서 값을 할당 가능</p>
<pre><code class="language-jsx">// 빈 객체 생성
const emptyObj = {};

// 속성 추가 (마침표 표기법)
emptyObj.name = &quot;철수&quot;;
emptyObj.age = 18;

// 속성 추가 (대괄호 표기법)
emptyObj[&quot;height&quot;] = 175;
emptyObj[&quot;favorite-color&quot;] = &quot;blue&quot;;

console.log(emptyObj); 
// { name: &quot;철수&quot;, age: 18, height: 175, favorite-color: &quot;blue&quot; } 출력됨</code></pre>
<h3 id="객체-속성-수정">객체 속성 수정</h3>
<pre><code class="language-jsx">const user = {
  name: &quot;유우시&quot;
  age: 20,
};

user.name = &quot;리쿠&quot;;

console.log(user); // { name: &quot;리쿠&quot; } 출력됨</code></pre>
<h3 id="객체-속성-삭제">객체 속성 삭제</h3>
<p><code>delete</code> 키워드 사용 (객체 자체는 삭제 불가)</p>
<p>객체를 제거하려면 변수에 <code>null</code>을 할당하거나 스코프 밖으로 이동시켜야 함</p>
<pre><code class="language-jsx">const user = {
  name: &quot;리쿠&quot;,
  age: 20,
};

delete user.age;

console.log(user); // { name: &quot;리쿠&quot; } 출력됨

// 존재하지 않는 속성 삭제 (에러 발생하지 않음)
delete user.weight;

// 객체 자체를 삭제하려고 시도 (작동하지 않음)
delete user;</code></pre>
<h3 id="객체-키-정의계산된-속성">객체 키 정의(계산된 속성)</h3>
<pre><code class="language-jsx">const key = &quot;name&quot;;
const user = {
  [key]: &quot;리쿠&quot;
};

console.log(user.name); // &quot;리쿠&quot; 출력됨
console.log(user[key]); // &quot;리쿠&quot; 출력됨</code></pre>
<h2 id="객체의-속성-축약-표현es6">객체의 속성 축약 표현(ES6)</h2>
<p>객체 리터럴에서 속성의 키와 값이 동일한 변수명일 경우, 이를 축약하여 표현 가능</p>
<p>객체 생성 시 외부 변수를 그대로 사용할 때 유용</p>
<h3 id="속성-축약">속성 축약</h3>
<pre><code class="language-jsx">// 기존 방식
const name = &quot;리쿠&quot;;
const age = 20;

const user1 = {
  name: name,
  age: age
};

// 축약 표현
const user2 = {
  name,
  age
};

console.log(user1); // { name: &quot;리쿠&quot;, age: 20 } 출력됨
console.log(user2); // { name: &quot;리쿠&quot;, age: 20 } 출력됨</code></pre>
<h3 id="함수-축약">함수 축약</h3>
<pre><code class="language-jsx">// 기존 방식
const user1 = {
  name: &quot;리쿠&quot;,
  sayHello: function() {
    console.log(&quot;안녕하세요!&quot;);
  }
};

// 축약 표현
const user2 = {
  name: &quot;리쿠&quot;,
  sayHello() {
    console.log(&quot;안녕하세요!&quot;);
  }
};

user1.sayHello(); // 출력: 안녕하세요!
user2.sayHello(); // 출력: 안녕하세요!</code></pre>
<h2 id="객체-병합과-복사">객체 병합과 복사</h2>
<p><strong>객체는 참조 자료형으로, 기본적으로 얕은 복사가 이루어짐</strong></p>
<p>얕은 복사: 객체의 최상위 속성만 새로운 메모리에 복사하고, 중첩된 객체나 배열은 원본과 동일한 참조를 유지함</p>
<p>깊은 복사: 객체의 모든 계층을 새로 생성하여 완전히 독립적인 복사본을 만듦</p>
<p>(깊은 복사 ⇒ 얕은 복사 ❌, 얕은 복사 ⇒ 깊은 복사 ⭕️)</p>
<p>예시:</p>
<pre><code class="language-jsx">const original = { name: &quot;리쿠&quot; };
const copy = original;

original.name = &quot;시온&quot;;

console.log(original); // { name: &quot;시온&quot; }
console.log(copy);     // { name: &quot;시온&quot; }</code></pre>
<h3 id="전개-연산자">전개 연산자</h3>
<p><code>...</code>는 함수의 매개변수로 사용 시 <strong>나머지 매개변수</strong>로 작동. 객체나 배열의 속성으로 사용 시 <strong>전개 연산자</strong>로 작동. 이 전개 연산자를 활용하여 객체의 얕은 복사 수행 가능</p>
<p>예시</p>
<pre><code class="language-jsx">const original = { name: &quot;리쿠&quot;, age: 20 };
const copy = { ...original }; 
// {} 비어있는 객체 껍데기를 만들고 속만 ...original로 채움

original.name = &quot;시온&quot;;

console.log(original); // { name: &quot;시온&quot;, age: 20 } 출력됨
console.log(copy);     // { name: &quot;리쿠&quot;, age: 20 } 출력됨</code></pre>
<p>이 방법은 객체의 최상위 속성에 대해서만 깊은 복사 수행. 중첩된 객체나 배열이 있는 경우 추가적인 처리 필요. 실제로는 얕은 복사에 해당</p>
<h3 id="전개-연산자를-사용한-객체-병합">전개 연산자를 사용한 객체 병합</h3>
<p>전개 연산자를 사용한 객체 병합의 예시 (두 개의 객체):</p>
<pre><code class="language-jsx">const obj1 = { name: &quot;리쿠&quot;, age: 21 };
const obj2 = { age: 18, nationality: &quot;한국&quot; };

const mergedObj = { ...obj1, ...obj2 };

console.log(mergedObj);
// { name: &quot;리쿠&quot;, age: 18, nationality: &quot;한국&quot; } 출력됨</code></pre>
<p>주요 특징</p>
<ul>
<li>동일 키 존재 시, 후순위 객체의 값으로 덮어씀</li>
<li>병합 순서가 최종 값 결정</li>
<li>선택적 속성 업데이트에 유용</li>
</ul>
<h3 id="중첩된-객체의-복사">중첩된 객체의 복사</h3>
<pre><code class="language-jsx">const original = {
  name: &quot;리쿠&quot;,
  age: 21,
  address: {
    city: &quot;후쿠이&quot;,
    country: &quot;일본&quot;
  }
};

const copy = { ...original };

original.name = &quot;시온&quot;;
original.address.city = &quot;서울&quot;;

console.log(original);
// 출력: { name: &quot;시온&quot;, age: 21, address: { city: &quot;서울&quot;, country: &quot;일본&quot; } }

console.log(copy);
// 출력: { name: &quot;리쿠&quot;, age: 21, address: { city: &quot;서울&quot;, country: &quot;일본&quot; } }</code></pre>
<ul>
<li>최상위 속성 'name'은 독립적으로 복사되어 원본 변경이 복사본에 영향을 주지 않음</li>
<li>중첩 객체 'address'는 참조가 복사되어, 원본 변경이 복사본에도 반영됨</li>
</ul>
<p>중첩 객체의 완전한 독립 복사를 위해 재귀적 깊은 복사나 JSON.parse(JSON.stringify()) 사용 가능. 단, 함수나 순환 참조에 주의 필요</p>
<p><strong>중첩 객체의 깊은 복사 방법</strong></p>
<ul>
<li><p><code>lodash</code> 라이브러리 사용 - 실무에서 많이 활용</p>
<ul>
<li>lodash - 개발 시 자주 사용되는 유용한 함수들의 모음</li>
<li>lodash의 cloneDeep() 메서드로 깊은 복사 가능</li>
</ul>
</li>
<li><p>JSON.stringify를 이용 - 문자열로 다 바꿈</p>
</li>
<li><p>JSON.stringify()와 JSON.parse()를 사용한 깊은 복사의 예시</p>
<pre><code class="language-jsx">  const original = {
    name: &quot;리쿠&quot;,
    age: 21,
    address: {
      city: &quot;후쿠이&quot;,
      country: &quot;일본&quot;
    }
  };

  // JSON.stringify()로 객체를 JSON 문자열로 변환 후,
  // JSON.parse()로 다시 객체로 변환
  // 이 과정에서 원본 객체의 구조가 완전히 새로 생성되어 깊은 복사가 이루어짐
  const deepCopy = JSON.parse(JSON.stringify(original));

  original.name = &quot;시온&quot;;
  original.address.city = &quot;서울&quot;;

  console.log(original);
  // 출력: { name: &quot;시온&quot;, age: 21, address: { city: &quot;서울&quot;, country: &quot;일본&quot; } }

  console.log(deepCopy);
  // 출력: { name: &quot;리쿠&quot;, age: 21, address: { city: &quot;후쿠이&quot;, country: &quot;일본&quot; } }</code></pre>
<p>  이 방법은 중첩된 객체까지 완전히 독립적으로 복사함. 하지만 함수, undefined, Symbol 등은 복사되지 않으며, 순환 참조가 있는 객체에는 사용할 수 없다는 점에 주의 필요</p>
<p>  <strong>배열 안의 객체 깊은 복사</strong></p>
<pre><code class="language-jsx">  // 객체를 포함한 배열 생성
  const originalArray = [{ name: &quot;리쿠&quot;, age: 21 }];

  // JSON.parse와 JSON.stringify를 사용한 깊은 복사
  const deepCopyArray = JSON.parse(JSON.stringify(originalArray));

  // 원본 배열의 객체 수정
  originalArray[0].name = &quot;시온&quot;;

  console.log(&quot;원본 배열:&quot;, originalArray);
  // 출력: 원본 배열: [{ name: &quot;시온&quot;, age: 21 }]

  console.log(&quot;깊은 복사된 배열:&quot;, deepCopyArray);
  // 출력: 깊은 복사된 배열: [{ name: &quot;리쿠&quot;, age: 21 }]</code></pre>
</li>
</ul>