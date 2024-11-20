<h2 id="타입별칭"><strong>타입별칭</strong></h2>
<h3 id="타입별칭이란">타입별칭이란?</h3>
<p>타입별칭: 기존 타입에 별칭(이름) 부여하여 재사용 용이. 복잡한 타입을 간단한 이름으로 대체하거나, 여러 타입 조합하여 관리 시 유용함</p>
<h3 id="타입별칭-작성-규칙">타입별칭 작성 규칙</h3>
<ol>
<li><code>type</code> 키워드 사용</li>
<li>별칭 이름은 <strong>첫 글자를 대문자로</strong> 작성하는 것이 일반적 관례</li>
</ol>
<p>예제 코드</p>
<pre><code class="language-tsx">// 타입별칭 선언
type MyType = string | number | boolean;

// 타입별칭 사용
let value: MyType;

value = &quot;hello&quot;;  // string
value = 123;      // number
value = true;     // boolean</code></pre>
<p>타입별칭 사용: 복잡한 타입도 간결하게 표현 가능. 코드의 가독성과 유지보수성 향상</p>
<hr />
<h2 id="타입추론"><strong>타입추론</strong></h2>
<h3 id="타입추론이란">타입추론이란?</h3>
<p>타입추론: TypeScript가 할당된 <strong>값을 보고 타입을 자동으로 추론</strong>하는 기능</p>
<p><strong>변수 선언 시</strong> 타입을 명시하지 않아도 TypeScript가 타입을 알아서 지정</p>
<p><strong>타입추론 예제</strong></p>
<pre><code class="language-tsx">let num = 10; // 타입추론: number
let str = &quot;hello&quot;; // 타입추론: string

// num 변수는 타입을 명시하지 않아도 자동으로 number로 추론됨
num = 20; // 정상
// num = &quot;hello&quot;; // 에러: string을 number에 할당할 수 없음</code></pre>
<p>위 코드에서 <code>num</code> 변수는 값을 기반으로 <code>number</code> 타입으로 추론됨. 별도로 타입을 명시하지 않아도 안전하게 사용 가능</p>
<h3 id="함수의-반환값도-타입추론">함수의 <code>반환값</code>도 타입추론</h3>
<p>함수의 반환값도 TypeScript가 자동으로 타입을 추론함</p>
<pre><code class="language-tsx">function sum(a: number, b: number) {
  return a + b;
}

const result = sum(10, 20); // result의 타입은 number로 추론됨</code></pre>
<p>반환값에 타입을 명시하지 않아도 <code>sum</code> 함수의 반환 타입은 <code>number</code>로 추론됨</p>
<h3 id="타입추론이-적용되지-않는-경우-함수-매개변수"><strong>타입추론이 적용되지 않는 경우: 함수 <code>매개변수</code></strong></h3>
<p>타입추론은 함수의 매개변수에는 기본적으로 적용되지 않음. 매개변수의 타입을 명시하지 않으면 TypeScript는 이를 알 수 없어 에러를 발생시킴</p>
<p><strong>타입추론이 되지 않는 예제</strong></p>
<pre><code class="language-tsx">function multiply(a, b) {
  return a * b;
}
multiply(2, 3); // 에러 발생</code></pre>
<p><strong>해결: 타입을 명시하거나 기본값 설정</strong></p>
<pre><code class="language-tsx">// 1. 매개변수 타입 명시
function multiply(a: number, b: number): number {
  return a * b;
}

// 2. 매개변수 기본값 설정
function multiplyWithDefault(a = 2, b = 3): number {
  return a * b;
}</code></pre>
<hr />
<h2 id="타입표명-vs-타입추론"><strong>타입표명 vs 타입추론</strong></h2>
<p>TypeScript에서는 타입을 <strong>직접 명시(타입표명)</strong>하거나, <strong>자동으로 추론(타입추론)</strong>할 수 있음. 두 가지 방식 중 선택은 팀의 규칙이나 개인 성향에 따라 달라질 수 있음</p>
<h3 id="강사님-선호-방식">강사님 선호 방식</h3>
<ul>
<li><strong>타입추론을 적극 활용</strong>: 불필요한 타입 선언을 줄여 코드가 깔끔해짐</li>
<li>타입추론이 문제가 되지 않는 경우 굳이 타입을 명시하지 않음</li>
<li>함수 매개변수처럼 타입추론이 적용되지 않는 곳에서는 타입을 명시함</li>
</ul>