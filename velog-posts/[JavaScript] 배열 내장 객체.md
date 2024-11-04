<h2 id="배열-메서드의-유형">배열 메서드의 유형</h2>
<ol>
<li><strong>파괴적 메서드</strong>: 배열을 직접 변경함 ⇒ <strong>원본 손상</strong>에 <strong><code>주의</code></strong> </li>
<li><strong>비파괴적 메서드</strong>: 원본 배열을 변경하지 않고, 새 값을 반환함</li>
</ol>
<hr />
<p><strong>사용빈도 높음 ⭐️</strong></p>
<p><strong>알고리즘 💻</strong></p>
<hr />
<h2 id="파괴적-메서드">파괴적 메서드</h2>
<h3 id="1-push"><strong>1. <code>push()</code></strong></h3>
<p>배열 끝에 요소 추가, 새로운 배열의 길이 반환</p>
<pre><code class="language-jsx">const arr = [1, 2];
arr.push(3); // [1, 2, 3]</code></pre>
<h3 id="2-pop"><strong>2. <code>pop()</code></strong></h3>
<p>배열 마지막 요소 제거, 해당 요소 반환</p>
<pre><code class="language-jsx">const arr = [1, 2, 3];
const last = arr.pop(); // arr: [1, 2], last: 3</code></pre>
<h3 id="3-shift"><strong>3. <code>shift()</code></strong></h3>
<p>배열의 첫 번째 요소 제거, <strong>제거된 요소</strong> 반환</p>
<pre><code class="language-jsx">const arr = [1, 2, 3];
const first = arr.shift(); // arr: [2, 3], first: 1</code></pre>
<h3 id="4-unshift"><strong>4. <code>unshift()</code></strong></h3>
<p>배열 앞에 요소 추가, <strong>새로운 배열의 길이</strong> 반환</p>
<pre><code class="language-jsx">const fruits = ['banana', 'orange'];
fruits.unshift('apple');
console.log(fruits); // ['apple', 'banana', 'orange']

// 여러 요소 추가
fruits.unshift('grape', 'mango');
console.log(fruits); // ['grape', 'mango', 'apple', 'banana', 'orange']

//새로운 배열의 길이 반환
const arr = [2, 3];
const length = arr.unshift(1); // arr: [1, 2, 3], length: 3</code></pre>
<h3 id="5-splice"><strong>5. <code>splice()</code></strong></h3>
<p>특정 위치에서 요소 추가, 제거 또는 대체, <strong>제거된 요소의 배열</strong> 반환</p>
<pre><code class="language-jsx">const arr = [1, 2, 3];
const removed = arr.splice(1, 1, 'a'); // arr: [1, 'a', 3], removed: [2]</code></pre>
<h3 id="6-sort"><strong>6. <code>sort()</code></strong></h3>
<p>배열 정렬, 정렬된 배열 반환. 얕은 복사 후 사용 권장</p>
<ul>
<li>기본: 문자열 정렬(유니코드 기준)<ul>
<li><strong>숫자: 비교함수 필요</strong></li>
</ul>
</li>
<li>⚠️ 대소문자 통일 후 정렬</li>
</ul>
<p><strong>정렬 예시</strong></p>
<ol>
<li><strong>숫자 배열 정렬</strong>: <code>(a, b) =&gt; a - b</code> 또는 <code>(a, b) =&gt; b - a</code> 콜백 함수로 오름차순/내림차순 정렬</li>
<li><strong>문자열 배열 정렬</strong>: <code>sort()</code> 호출만으로 알파벳순 정렬 가능</li>
<li><strong>객체 배열 정렬</strong>: <code>(a, b) =&gt; a.age - b.age</code>와 같이 특정 속성 기준으로 정렬</li>
</ol>
<pre><code class="language-jsx">// 숫자 배열 정렬
const numbers = [3, 1, 4, 1, 5, 9];
const sortedNumbers = [...numbers].sort((a, b) =&gt; a - b);//얕은복사, 오름차순 정렬
console.log('원본 숫자 배열:', numbers);
console.log('정렬된 숫자 배열:', sortedNumbers);
// 원본 숫자 배열: [3, 1, 4, 1, 5, 9]
// 정렬된 숫자 배열: [1, 1, 3, 4, 5, 9]

// 문자열 배열 정렬
const fruits = ['banana', 'apple', 'cherry', 'date'];
const sortedFruits = fruits.sort();
console.log('정렬된 문자열 배열:', fruits);
// 정렬된 문자열 배열: ['apple', 'banana', 'cherry', 'date']

// 객체 배열 정렬
const people = [
  { name: 'Alice', age: 30 },
  { name: 'Bob', age: 25 },
  { name: 'Charlie', age: 35 }
];
people.sort((a, b) =&gt; a.age - b.age); //나이순
console.log('나이순으로 정렬된 객체 배열:', people);
// 나이순으로 정렬된 객체 배열: [{ name: 'Bob', age: 25 }, { name: 'Alice', age: 30 }, { name: 'Charlie', age: 35 }]</code></pre>
<h3 id="7-reverse"><strong>7. <code>reverse()</code></strong></h3>
<p>배열의 순서 뒤집기, <strong>뒤집힌 배열</strong> 반환</p>
<pre><code class="language-jsx">const arr = [1, 2, 3];
arr.reverse(); // arr: [3, 2, 1]</code></pre>
<h3 id="8-fill"><strong>8. <code>fill()</code></strong></h3>
<p>배열의 모든 요소를 특정 값으로 채우기, <strong>채워진 배열</strong> 반환</p>
<ul>
<li>시작과 끝 인덱스 지정 가능. 더미배열 생성 시 활용</li>
</ul>
<pre><code class="language-jsx">// 모든 요소를 5로 채우기
const array1 = [1, 2, 3, 4];
console.log(array1.fill(5));
// 출력: [5, 5, 5, 5]

// 인덱스 1부터 3 이전까지 0으로 채우기
const array2 = [1, 2, 3, 4];
console.log(array2.fill(0, 1, 3));
// 출력: [1, 0, 0, 4]

// 더미 배열 만들기
const dummyArray = new Array(5).fill(0);
console.log(dummyArray);
// 출력: [0, 0, 0, 0, 0]</code></pre>
<h3 id="9-copywithin"><strong>9. <code>copyWithin()</code></strong></h3>
<p>배열의 일부를 복사하여 다른 위치에 덮어쓰기, <strong>배열</strong> 반환</p>
<p>복사와 붙여넣기가 같은 배열 내에서 이루어져 배열의 길이 변화 없음</p>
<pre><code class="language-jsx">array.copyWithin(target, start)</code></pre>
<ul>
<li><code>target</code>: 복사한 요소를 붙여넣을 시작 위치</li>
<li><code>start</code>: 복사를 시작할 인덱스. 기본값은 0</li>
</ul>
<pre><code class="language-jsx">// 시작 인덱스만 지정
const array2 = [1, 2, 3, 4, 5];
console.log(array2.copyWithin(0, 3));
// 출력: [4, 5, 3, 4, 5]

// 음수 인덱스 사용
const array3 = [1, 2, 3, 4, 5];
console.log(array3.copyWithin(-2, -3, -1));
// 출력: [1, 2, 3, 3, 4]</code></pre>
<h2 id="비파괴적-메서드">비파괴적 메서드</h2>
<h3 id="10-slice-⭐️"><strong>10. <code>slice()</code></strong> ⭐️</h3>
<p>배열의 일부를 추출하여 <strong>새 배열</strong> 반환</p>
<pre><code class="language-jsx">const arr = [1, 2, 3];
const newArr = arr.slice(1); // newArr: [2, 3]</code></pre>
<h3 id="11-concat"><strong>11. <code>concat()</code></strong></h3>
<p>배열을 합쳐 <strong>새 배열</strong> 반환</p>
<pre><code class="language-jsx">const arr1 = [1];
const arr2 = [2, 3];
const result = arr1.concat(arr2); // result: [1, 2, 3]</code></pre>
<h3 id="12-map-⭐️"><strong>12. <code>map()</code></strong> ⭐️</h3>
<p>배열의 각 요소에 함수 적용한 결과를 <strong>새 배열</strong>로 반환</p>
<pre><code class="language-jsx">const arr = [1, 2, 3];
const doubled = arr.map(x =&gt; x * 2); // doubled: [2, 4, 6]</code></pre>
<h3 id="13-filter-⭐️"><strong>13. <code>filter()</code></strong> ⭐️</h3>
<p>조건이 true인 요소만으로 <strong>새 배열</strong> 반환</p>
<pre><code class="language-jsx">const arr = [1, 2, 3, 4];
const evens = arr.filter(x =&gt; x % 2 === 0); // evens: [2, 4]</code></pre>
<h3 id="14-reduce-⭐️"><strong>14. <code>reduce()</code></strong> ⭐️</h3>
<p>배열을 하나의 값으로 축약하고 <strong>축약된 값</strong> 반환</p>
<p><strong>초기값 설정 주의사항:</strong></p>
<ul>
<li>빈 배열에서 초기값 없이 사용 시 오류 발생 가능</li>
<li>초기값 ❌: prev는 배열[0], cur는 배열[1]</li>
<li>초기값 ⭕️: prev는 초기값, cur는 배열[0]</li>
</ul>
<p><strong>기본 구조</strong></p>
<pre><code class="language-jsx">reduce((누적값, 현재값, 인덱스, 배열) =&gt; { }, 초기값)</code></pre>
<ul>
<li>누적값: 콜백의 반환값 누적</li>
<li>현재값: 처리할 현재 요소</li>
<li>인덱스: 현재 요소의 인덱스 (선택)</li>
<li>배열: reduce()를 호출한 배열 (선택)</li>
<li>초기값: 반복 시작할 초기값 (선택)</li>
</ul>
<pre><code class="language-jsx">const arr = [1, 2, 3];
const sum = arr.reduce((acc, cur) =&gt; acc + cur, 0); // sum: 6</code></pre>
<h3 id="15-foreach-⭐️"><strong>15. <code>forEach()</code> ⭐️</strong></h3>
<p>배열의 각 요소 순회, <strong>반환값 없음</strong></p>
<pre><code class="language-jsx">const arr = [1, 2, 3];
arr.forEach(x =&gt; console.log(x)); // 출력: 1, 2, 3</code></pre>
<h3 id="16-find"><strong>16. <code>find()</code></strong></h3>
<p>조건을 만족하는 <strong>첫 번째 요소</strong> 반환</p>
<ul>
<li>find() 메서드는 조건 만족하는 첫 번째 요소 찾으면 즉시 반환하고 순회 중단</li>
</ul>
<pre><code class="language-jsx">const arr = [1, 2, 3];
const found = arr.find(x =&gt; x &gt; 1); // found: 2</code></pre>
<h3 id="17-findindex"><strong>17. <code>findIndex()</code></strong></h3>
<p>조건을 만족하는 <strong>첫 번째 요소의 인덱스</strong> 반환</p>
<ul>
<li>만족하는 게 없으면 -1 반환</li>
</ul>
<pre><code class="language-jsx">const arr = [1, 2, 3];
const index = arr.findIndex(x =&gt; x &gt; 1); // index: 1</code></pre>
<h3 id="18-some-💻"><strong>18. <code>some()</code></strong> 💻</h3>
<p>배열 중 하나라도 조건 만족하면 <code>true</code>, 아니면 <code>false</code> 반환</p>
<pre><code class="language-jsx">const arr = [1, 2, 3];
const hasEven = arr.some(x =&gt; x % 2 === 0); // hasEven: true</code></pre>
<h3 id="19-every-💻"><strong>19. <code>every()</code></strong> 💻</h3>
<p><code>모든</code> 요소가 조건 만족하면 <code>true</code>, 아니면 <code>false</code> 반환</p>
<pre><code class="language-jsx">const arr = [2, 4, 6];
const allEven = arr.every(x =&gt; x % 2 === 0); // allEven: true</code></pre>
<h3 id="20-includes-⭐️"><strong>20. <code>includes()</code></strong> ⭐️</h3>
<p>배열의 <code>일정</code> 요소가 매개변수와 일치하는지 확인 <code>true</code>, 아니면 <code>false</code> 반환</p>
<pre><code class="language-jsx">const fruits = ['apple', 'banana', 'orange', 'grape'];

console.log(fruits.includes('banana')); // true
console.log(fruits.includes('kiwi')); // false

// 두 번째 매개변수로 검색 시작할 인덱스 지정 가능 (선택)
console.log(fruits.includes('apple', 1)); // false (인덱스 1부터 검색 시작)

// 대소문자 구분
console.log(fruits.includes('Apple')); // false</code></pre>
<h3 id="21-join"><strong>21. <code>join()</code></strong></h3>
<p>배열 요소를 결합하여 <strong>문자열</strong> 반환</p>
<pre><code class="language-jsx">const arr = [1, 2, 3];
arr.join('-'); // &quot;1-2-3&quot;</code></pre>
<h3 id="22-indexof"><strong>22. <code>indexOf()</code></strong></h3>
<p>특정 요소의 첫 인덱스 반환, 없으면 <code>-1</code></p>
<p>매개변수와 동일한 요소 찾음. 없으면 -1</p>
<pre><code class="language-jsx">const arr = [1, 2, 3, 2];
arr.indexOf(2); // 1</code></pre>
<h3 id="23-lastindexof"><strong>23. <code>lastIndexOf()</code></strong></h3>
<p>특정 요소의 마지막 인덱스 반환</p>
<pre><code class="language-jsx">const arr = [1, 2, 3, 2];
arr.lastIndexOf(2); // 3</code></pre>
<h3 id="24-flat"><strong>24.</strong> <code>flat()</code></h3>
<p>다차원 배열을 평면 배열로 변환하고 <strong>새로운 배열</strong> 반환, 깊이 지정 가능</p>
<pre><code class="language-jsx">// 중첩된 배열 선언
const nestedArray = [1, [2, [3, 4]], 5, [6, 7]];

// flat()을 인자 없이 사용하면 한 단계만 평면화
console.log(nestedArray.flat()); // [1, 2, [3, 4], 5, 6, 7]

// flat(2)는 두 단계까지 평면화
console.log(nestedArray.flat(2)); // [1, 2, 3, 4, 5, 6, 7]

// 깊게 중첩된 배열 선언
const deeplyNestedArray = [1, [2, [3, [4, 5]]]];

// flat(Infinity)는 모든 중첩 수준 평면화
console.log(deeplyNestedArray.flat(Infinity)); // [1, 2, 3, 4, 5]</code></pre>
<blockquote>
<p>📚 자세한 건 <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array">MDN 공식 문서</a> 참고</p>
</blockquote>