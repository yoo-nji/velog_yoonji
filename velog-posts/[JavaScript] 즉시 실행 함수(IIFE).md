<h3 id="즉시-실행-함수">즉시 실행 함수</h3>
<p><strong><code>즉시 실행 함수(IIFE)</code></strong>는 선언과 동시에 호출되는 함수. 이 패턴은 <strong>전역 범위 오염 방지</strong>와 함께 필요 작업 수행. 호출 후 <strong>즉시 콜스택에서 제거</strong>되어 <strong>코드 충돌 위험</strong> 감소.</p>
<p>프레임워크와 모듈 시스템의 발전으로 IIFE 사용 감소</p>
<h3 id="iife-기본-형태"><strong>IIFE 기본 형태</strong></h3>
<pre><code class="language-jsx">(function() {
    // 코드
})();</code></pre>
<p><strong>함수 선언과 동시에 호출</strong>하는 구조</p>
<h3 id="사용-시기"><strong>사용 시기</strong></h3>
<ul>
<li><strong>전역 범위 오염 방지</strong>를 위해 사용</li>
<li>코드를 <strong>한 번만 실행하고 재호출이 불필요한 경우</strong>에 유용</li>
</ul>
<h3 id="특징"><strong>특징</strong></h3>
<ul>
<li><strong>한 번 실행된 코드</strong>는 재호출 불가<ul>
<li>호출과 동시에 삭제되어 <strong>재사용 불가</strong></li>
</ul>
</li>
</ul>
<h3 id="iife-간단한-예제"><strong>IIFE 간단한 예제</strong></h3>
<pre><code class="language-jsx">(function test() {
  console.log(&quot;이 함수는 즉시 실행됨!&quot;);
})();

// 익명 함수 형태
(function() {
  console.log(&quot;이 함수는 즉시 실행됨!&quot;);
})();

// 화살표 함수 형태
(() =&gt; {
  console.log(&quot;이 함수는 즉시 실행됨!&quot;);
})();</code></pre>
<p>위 코드에서 함수가 <strong>정의됨과 동시에 호출</strong>. 콘솔에는 &quot;이 함수는 즉시 실행됨!&quot;이라는 메시지 출력.</p>
<h3 id="라이브러리에서-iife-사용-예시"><strong>라이브러리에서 IIFE 사용 예시</strong></h3>
<p>여러 <strong>JavaScript 라이브러리</strong>들이 전역 스코프 보호를 위해 IIFE 패턴 활용. 예를 들어, 내부 변수나 함수를 외부에서 접근 못하게 하는 데 유용.</p>
<h3 id="iife를-이용한-카운터-예제"><strong>IIFE를 이용한 카운터 예제</strong></h3>
<pre><code class="language-jsx">// 일반적인 방식
let counter = 0;
function incrementCounter() {
  counter++;
  console.log(counter);
}

// IIFE를 사용한 방식
const counter = (function() {
  let count = 0; // 지역 변수로 보호됨
  return function() {
    count++;
    console.log(count);
  };
})();

counter(); // 1
counter(); // 2</code></pre>
<p>위 예제에서는 <strong>IIFE를 사용해 <code>count</code> 변수가 전역 스코프에 노출되지 않도록</strong> 처리. 이렇게 하면 <code>count</code> 변수는 외부에서 접근 불가능하고, 클로저(closure)를 통해 안전하게 관리. 이는 변수 오염 방지와 코드의 <strong>안전성</strong> 향상.</p>