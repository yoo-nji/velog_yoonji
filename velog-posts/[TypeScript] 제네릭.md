<h2 id="1-제네릭의-기본-개념">1. 제네릭의 기본 개념</h2>
<ul>
<li><strong><code>제네릭</code></strong>은 타입스크립트에서 &quot;값을 타입으로 <code>치환</code>&quot;하는 역할</li>
<li>특정 값이 여러 타입을 가질 때 활용</li>
</ul>
<h3 id="제네릭-사용-목적">제네릭 사용 목적</h3>
<ul>
<li><strong>코드 재사용성 증가</strong>: 하나의 함수나 인터페이스로 다양한 타입 처리 가능</li>
<li><strong>타입 안정성 보장</strong>: 타입 추론 및 강제 적용으로 런타임 오류 방지</li>
<li><strong>가독성 및 유지보수성 향상</strong>: 중복 코드 감소</li>
</ul>
<hr />
<h2 id="2-제네릭의-주요-활용법">2. 제네릭의 주요 활용법</h2>
<h3 id="21-인터페이스--제네릭">2.1 인터페이스 + 제네릭</h3>
<pre><code class="language-tsx">interface Car&lt;T&gt; {
  name: string;
  color: string;
  option: T;
}

// 옵션이 없는 자동차
let car: Car&lt;null&gt; = {
  name: &quot;Tesla&quot;,
  color: &quot;Red&quot;,
  option: null,
};

// 옵션이 있는 자동차
let car2: Car&lt;{ giftcard: boolean }&gt; = {
  name: &quot;Tesla&quot;,
  color: &quot;Red&quot;,
  option: { giftcard: true },
};</code></pre>
<h3 id="22-함수와-제네릭">2.2 함수와 제네릭</h3>
<p>타입추론 <code>가능</code></p>
<h3 id="기본-문법">기본 문법</h3>
<pre><code class="language-tsx">function printValue&lt;T&gt;(value: T): T {
  return value;
}

printValue&lt;string&gt;(&quot;hello&quot;); // &quot;hello&quot;
printValue&lt;number&gt;(10); // 10</code></pre>
<h3 id="배열의-첫-번째-요소-반환-함수">배열의 첫 번째 요소 반환 함수</h3>
<ol>
<li>함수 선언식 + 제네릭</li>
</ol>
<pre><code class="language-tsx">function getFirstElement&lt;T&gt;(arr: T[]): T {
  return arr[0];
}
console.log(getFirstElement&lt;number&gt;([1, 2, 4])); // 전송됨</code></pre>
<ol>
<li>함수 표현식 + 제네릭</li>
</ol>
<pre><code class="language-tsx">const getFirstElement = function getFirstElement&lt;T&gt;(arr: T[]): T {
  return arr[0];
};</code></pre>
<ol>
<li>함수 표현식 + 타입 선언</li>
</ol>
<pre><code class="language-tsx">const getFirstElement: &lt;T&gt;(arr: T[]) =&gt; T = function getFirstElement(arr) {
  return arr[0];
};</code></pre>
<ol>
<li>화살표 함수 + 타입 선언</li>
</ol>
<pre><code class="language-tsx">const getFirstElement: &lt;T&gt;(arr: T[]) =&gt; T = (arr) =&gt; arr[0];</code></pre>
<p>타입 정의로 함수 타입 지정</p>
<pre><code class="language-tsx">type FirstFunc = &lt;T&gt;(arr: T[]) =&gt; T;
const getFirstElement: FirstFunc = function getFirstElement(arr) {
  return arr[0];
};</code></pre>
<p>인터페이스로 함수 타입 지정</p>
<pre><code class="language-tsx">interface FirstFunc {
  &lt;T&gt;(arr: T[]): T;
}
const getFirstElement: FirstFunc = (arr) =&gt; arr[0];</code></pre>
<p><strong>여러개의 타입 매개변수 사용 가능</strong></p>
<pre><code class="language-tsx">function mergObject&lt;T, U&gt;(obj1: T, obj2: U): T &amp; U {
  return { ...obj1, ...obj2 };
}

console.log(
  mergObject&lt;{ name: string }, { age: number }&gt;({ name: &quot;james&quot; }, { age: 10 }) // 함수는 타입추론이 돼서 생략 가능
);
console.log(mergObject&lt;{ name: string }, { gender: string }&gt;({ name: &quot;james&quot; }, { gender: &quot;male&quot; }));</code></pre>
<h2 id="3-심화-문법-제네릭-제약과-고급-활용">3. 심화 문법: 제네릭 제약과 고급 활용</h2>
<h3 id="31-제네릭-제약">3.1 제네릭 제약</h3>
<ul>
<li>제네릭의 타입 범위를 좁혀야 할 때 <strong>제네릭 제약</strong> 사용</li>
<li>제네릭 제약이 필요한 이유:<ul>
<li>코드의 재사용성은 높지만, 너무 광범위한 타입 허용이 문제가 될 수 있음</li>
<li>제약은 &lt;&gt; 안에 추가하여 설정함</li>
</ul>
</li>
<li><code>extends</code> 키워드:<ul>
<li>제네릭에서 &quot;확장&quot; 또는 &quot;상속&quot;의 의미로 사용함</li>
<li>특정 타입의 하위 타입만 허용하도록 제한함</li>
<li>예: <code>T extends string</code>은 T가 string 타입이거나 string의 하위 타입이어야 함</li>
</ul>
</li>
</ul>
<h3 id="특정-타입만-허용">특정 타입만 허용</h3>
<pre><code class="language-tsx">function getFirstElement&lt;T extends number | string&gt;(arr: T[]): T {
  return arr[0];
}

console.log(getFirstElement&lt;number&gt;([1, 2, 4])); // 1
console.log(getFirstElement&lt;string&gt;([&quot;hello&quot;, &quot;world&quot;])); // &quot;hello&quot;
// console.log(getFirstElement&lt;boolean&gt;([true, false])); // ❌ 오류</code></pre>
<h3 id="특정-속성을-가진-타입만-허용">특정 속성을 가진 타입만 허용</h3>
<pre><code class="language-tsx">// 조건: 입력값은 { length: number } 속성을 반드시 가져야 함
function getElementsLength&lt;T extends { length: number }&gt;(value: T): number {
  return value.length;
}

console.log(getElementsLength(&quot;hello&quot;)); // 5
console.log(getElementsLength([1, 2, 3])); // 3
// console.log(getElementsLength(10)); // ❌ 오류</code></pre>
<h3 id="여러-조건을-동시에-적용">여러 조건을 동시에 적용</h3>
<p>제네릭은 여러 타입 조건을 '&amp;'를 사용하여 동시에 적용 가능:</p>
<pre><code class="language-tsx">// T는 string과 { length: number } 둘 다 만족해야 함
function printText&lt;T extends string &amp; { length: number }&gt;(text: T) {
    console.log(text, text.length);
}</code></pre>
<h3 id="32-객체의-속성값-추출-keyof">3.2 객체의 속성값 추출: <code>keyof</code></h3>
<p><code>keyof</code>는 객체의 키를 제네릭으로 추출할 때 사용</p>
<pre><code class="language-tsx">//getProperty 함수: 객체와 속성 키를 받아 해당 속성 값을 반환
//조건: obj는 객체여야 하고, key는 obj의 속성 중 하나여야 함
//keyof: 객체의 키를 추출해서 유니온으로 반환

function getProperty&lt;T extends object, K extends keyof T&gt;(obj: T, key: K): T[K] {
  return obj[key];
}

// 함수 호출: 객체 { name: &quot;james&quot; }에서 &quot;name&quot; 속성 값을 가져옴
//K extends &quot;name&quot;
console.log(getProperty({ name: &quot;james&quot;, age: 20 }, &quot;name&quot;)); // &quot;james&quot;
//K extends &quot;name&quot; | &quot;age&quot;
console.log(getProperty({ name: &quot;james&quot;, age: 20 }, &quot;age&quot;)); // 20</code></pre>
<h3 id="속성값-업데이트">속성값 업데이트</h3>
<pre><code class="language-tsx">function updateProperty&lt;T extends object, K extends keyof T&gt;(obj: T, key: K, value: T[K]): T {
  obj[key] = value;
  return obj;
}

const car = { brand: &quot;benz&quot;, model: &quot;s-class&quot;, year: 2020 };
console.log(updateProperty(car, &quot;year&quot;, 2024));
// { brand: &quot;benz&quot;, model: &quot;s-class&quot;, year: 2024 }</code></pre>
<hr />
<h2 id="4-제네릭-활용-예제">4. 제네릭 활용 예제</h2>
<h3 id="객체-병합">객체 병합</h3>
<p>두 객체를 병합하는 함수. 반환 타입은 두 객체의 타입을 합친 형태</p>
<pre><code class="language-tsx">function mergeObjects&lt;T, U&gt;(obj1: T, obj2: U): T &amp; U {
  return { ...obj1, ...obj2 };
}

console.log(mergeObjects({ name: &quot;james&quot; }, { age: 10 })); // { name: &quot;james&quot;, age: 10 }</code></pre>
<h3 id="사용자-정보-출력">사용자 정보 출력</h3>
<p>입력 객체가 특정 속성을 포함해야 하는 경우, 제네릭을 사용해 타입을 강제 가능</p>
<pre><code class="language-tsx">// printUserInfo 함수: Nameable과 Ageable 속성을 모두 가진 객체의 정보를 출력
// 조건: 입력 객체는 반드시 name과 age 속성을 가져야 함
type Nameable = { name: string };
type Ageable = { age: number };

// 함수 정의: Nameable &amp; Ageable 타입을 만족하는 객체를 인자로 받음
//제네릭으로 필수, 제약 타입을 지정 가능
function printUserInfo&lt;T extends Nameable &amp; Ageable&gt;(user: T): void {
  console.log(`${user.name}, ${user.age}`);
}

printUserInfo({ name: &quot;james&quot;, age: 10 }); // james, 10</code></pre>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>