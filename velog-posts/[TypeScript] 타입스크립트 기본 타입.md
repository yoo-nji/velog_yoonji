<p>타입스크립트는 자바스크립트에 <strong>타입 시스템</strong> 추가로 코드의 안정성과 유지보수성이 향상됨</p>
<hr />
<h2 id="1-string-타입">1. <code>string</code> 타입</h2>
<p>문자열 처리 타입</p>
<ul>
<li>큰따옴표(&quot;&quot;), 작은따옴표(''), 백틱(`) 모두 string 타입으로 처리 가능</li>
<li>템플릿 리터럴(<code>${expression}</code>)에서 표현식의 결과도 string 타입으로 변환</li>
<li>이모티콘도 string 타입으로 처리 가능</li>
</ul>
<pre><code class="language-tsx">let str: string = &quot;Hello, TypeScript&quot;;
let backTick: string = `Hello ${doubleQuote}`;
let emoji: string = &quot;😊&quot;;

console.log(str); // Hello, TypeScript
console.log(backTick); // &quot;Hello World&quot;
console.log(emoji);    // &quot;😊&quot;</code></pre>
<h2 id="2-number-타입">2. <code>number</code> 타입</h2>
<p>정수, 소수, 음수, <code>NaN</code>, <code>Infinity</code> 등 포함한 숫자 타입</p>
<pre><code class="language-tsx">let x: number = 10;          // 정수
let y: number = 3.14;        // 소수
let z: number = -100;        // 음수
let a: number = NaN;         // Not a Number
let b: number = Infinity;    // 무한대

let result: number = 0 / 0;  // NaN
let positiveInfinity: number = 1 / 0; // 무한대</code></pre>
<h2 id="3-boolean-타입">3. <code>boolean</code> 타입</h2>
<p><code>true</code> 또는 <code>false</code> 값 가짐</p>
<pre><code class="language-tsx">let isDone: boolean = true;
let isTrue: boolean = false;

// 비교 연산
let result: boolean = 10 &gt; 5; // true
let result2: boolean = &quot;hello&quot; === &quot;hello&quot;; // true</code></pre>
<ul>
<li>문자열 &quot;true&quot;는 boolean 타입으로 설정 시 오류 발생, JSON.parse()로 변환한 true는 boolean 타입으로 지정 가능</li>
</ul>
<pre><code class="language-tsx">let boolTrue: boolean = JSON.parse(&quot;true&quot;); // 가능
// let boolString: boolean = &quot;true&quot;;  // 오류 발생</code></pre>
<ul>
<li>falsy로 평가되는 값들도 boolean 타입으로 지정하여 사용 가능</li>
</ul>
<pre><code class="language-tsx">let empty = &quot;&quot;;
let isZero: boolean = !!0;       // false
let isEmpty: boolean = !!empty;  // false
let isNanValue: boolean = !!NaN; // false</code></pre>
<h2 id="4-object-타입">4. <code>object</code> 타입</h2>
<p>객체, 배열, 함수 등 포함. <strong>속성 타입을 명확히 지정</strong>하는 것이 좋음</p>
<pre><code class="language-tsx">let obj: { name: string; age: number } = { name: &quot;John&quot;, age: 30 };
console.log(obj.name); // John</code></pre>
<p>배열과 함수도 객체 타입에 포함</p>
<pre><code class="language-tsx">let emptyArr: object = [];
let emptyFunc: object = function () {};</code></pre>
<h2 id="5-array-타입">5. <code>array</code> 타입</h2>
<p>배열 타입 정의 방식 두 가지:</p>
<ul>
<li><code>type[]</code> (최신 스타일)</li>
<li><code>Array&lt;type&gt;</code> (구버전)</li>
</ul>
<pre><code class="language-tsx">const numArr: number[] = [1, 2, 3];
const stringArr: Array&lt;string&gt; = [&quot;a&quot;, &quot;b&quot;, &quot;c&quot;];

// 중첩 배열
const nestedArray: number[][] = [
  [1, 2, 3],
  [4, 5, 6],
];

// 혼합 배열 (유니언 타입)
const mixedArr: (string | number)[] = [&quot;apple&quot;, 1, &quot;banana&quot;, 2];

// 생성자 함수를 사용한 배열 생성
const constructorArr: number[] = new Array(1, 2, 3);</code></pre>
<h2 id="6-tuple-타입">6. <code>tuple</code> 타입</h2>
<p><strong>튜플</strong>: 배열의 각 요소가 <strong>다른 타입</strong>을 가질 수 있는 배열. 특정 위치에 있는 타입 명시 가능</p>
<pre><code class="language-tsx">// 튜플
const mixArr: [number, string, {}, number[]] = [1, &quot;a&quot;, {}, [1, 2, 3]];

// 옵셔널 요소
let user: [string, number, string?] = [&quot;John&quot;, 25];
user.push(23); // 가능
console.log(user); // [&quot;John&quot;, 25, 23]

// 구조 분해 할당
let [item, ...rest]: [string, ...number[]] = [&quot;item1&quot;, 1, 2, 3, 4];</code></pre>
<p><strong>옵셔널 요소</strong>: <code>string?</code>는 해당 위치의 요소가 문자열이거나 생략 가능함을 표시. 타입 끝에 ?를 붙여 할당되지 않은 요소의 타입을 지정할 수 있음</p>
<p><strong>구조 분해 할당</strong>: 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 JavaScript 표현식. 위 예제에서는 첫 번째 요소를 <code>item</code>으로, 나머지 요소들을 <code>rest</code> 배열로 분해함</p>
<h2 id="7-null과-undefined-타입">7. <code>null</code>과 <code>undefined</code> 타입</h2>
<p><code>null</code>과 <code>undefined</code>는 각각 비어 있음을 나타냄</p>
<pre><code class="language-tsx">let x: null = null;
let b: undefined = undefined;

// null 병합 연산자
let result = x ?? &quot;default&quot;; // x가 null 또는 undefined면 &quot;default&quot; 반환</code></pre>
<h2 id="8-any-타입">8. <code>any</code> 타입</h2>
<p><strong>모든 타입 허용</strong>으로 개발 속도를 높이는 데 사용. 타입 안전성이 낮아 남용은 피해야 함</p>
<pre><code class="language-tsx">let value: any = 10;
value = &quot;hello&quot;;
value = true;
console.log(value); // true</code></pre>
<h2 id="9-unknown-타입">9. <code>unknown</code> 타입</h2>
<p><code>unknown</code>은 모든 타입을 허용하지만, 실제로 사용하기 전에 <strong>타입 검증</strong>이 필요함</p>
<pre><code class="language-tsx">let value: unknown = [1, 2];

// 타입 검증 (타입 가드)
if (Array.isArray(value)) {
  console.log(value[0]); // 1
}</code></pre>
<h2 id="10-any-vs-unknown-타입-비교">10. <code>any</code> vs <code>unknown</code> 타입 비교</h2>
<p><code>any</code>와 <code>unknown</code> 타입은 모든 타입 허용. 사용 방식과 안전성에서 차이점 존재</p>
<h3 id="any-타입">any 타입:</h3>
<pre><code class="language-tsx">let value: any = 10;
value = &quot;hello&quot;;
console.log(value.length); // 타입 검증 없이 사용 가능</code></pre>
<h3 id="unknown-타입">unknown 타입:</h3>
<pre><code class="language-tsx">let value: unknown = [1, 2];
if (Array.isArray(value)) {
  console.log(value[0]); // 타입 검증 후 사용
}</code></pre>
<p><strong>주요 차이점:</strong></p>
<ul>
<li><code>any</code>: 타입 검사를 무시하여 편리하지만 안전성이 낮음</li>
<li><code>unknown</code>: 사용 전 타입 검사 필요, 더 안전한 코드 작성 가능</li>
</ul>
<blockquote>
<p>Tip: 실무에서는 any 대신 unknown을 사용하는 것이 권장됨</p>
</blockquote>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>