<p>자바스크립트는 원시 값(Primitive Value)을 객체처럼 다룰 수 있도록 <strong><code>래퍼 객체</code></strong>를 자동으로 생성함. 이를 통해 기본 타입의 값(예: 숫자, 문자열, 불리언 등)에 대해 메서드나 프로퍼티를 호출 가능</p>
<hr />
<h2 id="래퍼-객체의-동작-원리">래퍼 객체의 동작 원리</h2>
<p><strong><code>래퍼 객체란?</code></strong> 자바스크립트가 기본 타입 값에 대해 메서드나 프로퍼티 호출 시 <strong>일시적으로 생성하는 객체</strong>로 사용 후 즉시 폐기되며, 개발자가 원시 값을 객체처럼 다룰 수 있게 함</p>
<h3 id="예시-래퍼-객체-생성-과정">예시: 래퍼 객체 생성 과정</h3>
<pre><code class="language-jsx">const pI = 3.141592;
console.log(pI.toFixed(2)); // 출력: &quot;3.14&quot;</code></pre>
<p>위 코드에서 <code>pI</code>는 <code>Number</code> 타입의 원시 값이지만, <code>toFixed()</code> 메서드를 호출 가능. 내부적으로 다음과 같은 방식으로 동작:</p>
<pre><code class="language-jsx">// 실제로는 이런 식으로 처리됨 (가상의 코드)
const pI = 3.141592;
const temp = new Number(pI); // 래퍼 객체가 임시로 생성
console.log(temp.toFixed(2)); // 래퍼 객체의 메서드를 호출
// 메서드 호출 후 래퍼 객체는 즉시 폐기</code></pre>
<ul>
<li>Number 타입의 경우, <strong>Number 객체로 임시 변환</strong>되며, 이 객체는 toFixed()와 같은 메서드를 가짐</li>
</ul>
<p>이러한 메커니즘 덕분에 원시 값에 대해서도 마치 객체처럼 메서드를 호출 가능. 이는 자바스크립트의 유연성을 보여주는 좋은 예시임</p>
<h2 id="래퍼-객체의-종류">래퍼 객체의 종류</h2>
<p>자바스크립트에는 <strong>Number</strong>, <strong>String</strong>, <strong>Boolean</strong> 등 기본 타입의 원시 값을 객체로 변환하는 <strong>래퍼 객체</strong>가 존재함. 예를 들어, 숫자는 <code>Number</code>, 문자열은 <code>String</code>, 불리언 값은 <code>Boolean</code> 객체로 임시 변환됨</p>
<pre><code class="language-jsx">const num = 10;
console.log(num.toString()); // &quot;10&quot; (숫자지만 객체처럼 사용 가능)</code></pre>
<p>위 코드에서 <code>num</code>은 원시 값이지만, <code>toString()</code> 메서드를 호출하면 <strong>일시적으로 <code>Number</code> 객체</strong>로 변환됨</p>
<h2 id="래퍼-객체의-특성-일시성">래퍼 객체의 특성: 일시성</h2>
<p>래퍼 객체는 <strong>일시적인 임시 객체</strong>로, 프로퍼티나 메서드를 호출할 때만 생성되고, 호출이 완료되면 즉시 삭제됨. </p>
<p>이러한 특성 덕분에 자바스크립트는 <strong>객체처럼 원시 값을 다룰 수 있는 유연성</strong>을 가지며, 별도의 래퍼 객체 생성 없이 기본 값에 대해 편리하게 메서드를 사용할 수 있음.</p>
<h2 id="✅-결론-프로토타입-기반-객체지향-언어로서의-자바스크립트">✅ 결론: 프로토타입 기반 객체지향 언어로서의 자바스크립트</h2>
<p>래퍼 객체는 자바스크립트의 <strong>프로토타입 기반 객체지향</strong> 특성을 보여줌. 모든 데이터를 객체처럼 다루고, 필요시 임시 객체를 생성해 유연성을 제공함</p>