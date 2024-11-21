<h2 id="1-기본적인-타입-별칭">1. 기본적인 타입 별칭</h2>
<pre><code class="language-tsx">type ID = string | number;

let id: ID = &quot;a&quot;; // ✅ OK
id = 10;          // ✅ OK</code></pre>
<p><code>ID</code>는 문자열 또는 숫자 타입을 나타냄. 이를 통해 <code>id</code> 변수는 두 가지 타입을 모두 사용 가능</p>
<h2 id="2-객체-타입-별칭">2. 객체 타입 별칭</h2>
<p>객체 구조를 타입별칭으로 정의하여 재사용 가능</p>
<pre><code class="language-tsx">type User = {
  name: string;
  age: number;
};

const user: User = {
  name: &quot;Alice&quot;,
  age: 30,
};</code></pre>
<h2 id="3-함수-타입-별칭">3. 함수 타입 별칭</h2>
<p>함수의 매개변수와 반환 타입 지정 시 유용</p>
<pre><code class="language-tsx">type SumFunc = (n1: number, n2: number) =&gt; number;

// 함수 표현식
const sum: SumFunc = function (n1, n2) {
  return n1 + n2;
};

// 화살표 함수
const sum2: SumFunc = (n1, n2) =&gt; n1 + n2;</code></pre>
<h2 id="4-readonly와-불변성">4. readonly와 불변성</h2>
<p><code>readonly</code> 키워드로 객체 속성을 읽기 전용으로 만들거나 배열을 상수로 변경 가능. 이를 통해 불변성 유지</p>
<h3 id="객체-읽기-전용">객체 읽기 전용</h3>
<pre><code class="language-tsx">type ReadonlyUser = {
  readonly id: number;
  name?: string; // ✅ ?옵셔널 연산자를 붙이면 string | undefined와 동일
  age: number;
};

const user: ReadonlyUser = { id: 1, name: &quot;Alice&quot;, age: 30 };
// user.id = 2; // ❌ 오류: 'id' 속성은 읽기 전용이라 다른 값 할당 불가</code></pre>
<h3 id="배열-읽기-전용">배열 읽기 전용</h3>
<pre><code class="language-tsx">type ReadonlyArray = readonly number[];
const arr: ReadonlyArray = [1, 2, 3];
// arr[0] = 10; // ❌ 오류: 상수로 변경되어 다른 값 할당 불가능</code></pre>
<h2 id="5-제네릭-타입-별칭">5. 제네릭 타입 별칭</h2>
<p>제네릭 사용으로 코드 재사용성 향상</p>
<p>제네릭 타입 별칭 사용 시 관용적 지정 방법으로 <code>대문자</code> 활용:</p>
<ul>
<li>T: Type (일반적 타입)</li>
<li>K: Key (키 타입)</li>
<li>V: Value (값 타입)</li>
<li>E: Element (요소 타입)</li>
</ul>
<p>예시:</p>
<pre><code class="language-tsx">type Container&lt;T&gt; = { value: T };
type Dictionary&lt;K extends string, V&gt; = { [key in K]: V };
type List&lt;E&gt; = E[];</code></pre>
<pre><code class="language-tsx">// option이 다양할 때
// 가독성이 좋지 않은 방식
type Car = {
  name: string;
  color: string;
  option: null | string | { giftcard: boolean };
};

// 👍 개선된 방식
type Car&lt;T&gt; = {
  name: string;
  color: string;
  option: T;
};

const car: Car&lt;null&gt; = {
  name: &quot;Benz&quot;,
  color: &quot;black&quot;,
  option: null,
};

const car2: Car&lt;string&gt; = {
  name: &quot;Benz&quot;,
  color: &quot;black&quot;,
  option: &quot;key&quot;,
};

const car3: Car&lt;{ giftcard: boolean }&gt; = {
  name: &quot;Benz&quot;,
  color: &quot;black&quot;,
  option: {
    giftcard: true,
  },
};</code></pre>
<h2 id="6-인덱스-시그니처">6. 인덱스 시그니처</h2>
<p>키와 값이 동일한 타입일 때 객체의 키와 값을 동적으로 정의 가능</p>
<pre><code class="language-tsx">type UserMap = {
  [key: string]: string;
};

let users: UserMap = {
  name: &quot;John&quot;,
  address: &quot;Seoul&quot;,
};

// 다른 타입 추가 시 유니온 사용
type UserMap = {
  [key: string]: string | number
};</code></pre>
<blockquote>
<p>💡 인덱스 시그니처는 자동완성 미지원. 자동완성 필요 시 고정 속성 추가</p>
</blockquote>
<pre><code class="language-tsx">type UserMap = {
  name: string; // 고정 속성
  [key: string]: string;
};</code></pre>
<h2 id="7-튜플-타입">7. 튜플 타입</h2>
<pre><code class="language-tsx">type Point = [number, number];
const point: Point = [10, 20];</code></pre>
<h2 id="8-인터섹션-타입">8. 인터섹션 타입</h2>
<p>인터섹션 타입은 '&amp;' 기호로 여러 타입을 결합해 새로운 타입 생성</p>
<pre><code class="language-tsx">type Nameable = { name: string };
type Ageable = { age: number };

type Person = Nameable &amp; Ageable;

const person: Person = { name: &quot;Alice&quot;, age: 30 };</code></pre>
<h2 id="9-리터럴-타입">9. 리터럴 타입</h2>
<p>특정 값들만 허용하도록 제한</p>
<pre><code class="language-jsx">type Direction = &quot;LEFT&quot; | &quot;RIGHT&quot; | &quot;UP&quot; | &quot;DOWN&quot;;

const direction: Direction = &quot;LEFT&quot;; // ✅ OK
// const direction: Direction = &quot;FORWARD&quot;; // ❌ 오류</code></pre>
<p><strong>활용</strong></p>
<pre><code class="language-jsx">type ButtonSize = &quot;small&quot; | &quot;medium&quot; | &quot;large&quot;;

interface Button {
  size: ButtonSize;
  label: string;
}

const myButton: Button = {
  size: &quot;medium&quot;, // ✅ OK
  label: &quot;Click Me&quot;,
};

// myButton.size = &quot;extra-large&quot;; // ❌ 오류</code></pre>
<h2 id="10-조건부-타입">10. 조건부 타입</h2>
<p>조건부 타입은 타입 시스템 내에서 조건문 사용 가능. 기본 문법:</p>
<pre><code class="language-tsx">type ConditionalType&lt;T&gt; = T extends U ? X : Y;</code></pre>
<ul>
<li>T: 검사할 타입</li>
<li>U: T가 확장하는지 확인할 타입</li>
<li>X: 조건이 참일 때의 결과 타입</li>
<li>Y: 조건이 거짓일 때의 결과 타입</li>
</ul>
<pre><code class="language-tsx">type IsString&lt;T&gt; = T extends string ? &quot;yes&quot; : &quot;no&quot;;

const result1: IsString&lt;string&gt; = &quot;yes&quot;;
const result2: IsString&lt;number&gt; = &quot;no&quot;;</code></pre>
<h2 id="11-키-선택-타입">11. 키 선택 타입</h2>
<pre><code class="language-tsx">type User = {
  name: string;
  age: number;
  address: string;
};

type UserKeys = keyof User; // &quot;name&quot; | &quot;age&quot; | &quot;address&quot;
const key: UserKeys = &quot;address&quot;;</code></pre>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>