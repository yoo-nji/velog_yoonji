<h3 id="프레젠테이션-컴포넌트"><strong>프레젠테이션 컴포넌트</strong></h3>
<p><strong><code>프레젠테이션 컴포넌트란?</code></strong> 자식 컴포넌트에게 프롭스를 전달하는 역할만 하는 컴포넌트</p>
<ul>
<li>상위에서 받은 <strong>props를 하위로 전달</strong>하는 것이 주된 역할</li>
<li>⚠️ 여러 컴포넌트를 거쳐 전달 시 <strong>프롭스 드릴링(props drilling)</strong> 문제 발생 가능</li>
</ul>
<hr />
<h2 id="프롭스-드릴링-패턴"><strong>프롭스 드릴링 패턴</strong></h2>
<p><strong><code>프롭스 드릴링이란?</code></strong></p>
<p> 데이터(혹은 함수)를 상위 컴포넌트에서 하위 컴포넌트로 전달하기 위해, <strong>중간 컴포넌트들을 거쳐야</strong> 하는 패턴</p>
<p><strong>예시 코드</strong></p>
<pre><code class="language-jsx">// App.js
function App() {
  const user = &quot;User1&quot;; // 최상위에서 데이터 생성
  return &lt;ParentComponent user={user} /&gt;;
}

// ParentComponent.js
function ParentComponent({ user }) {
  return &lt;ChildComponent user={user} /&gt;;
}

// ChildComponent.js
function ChildComponent({ user }) {
  return &lt;GrandChildComponent user={user} /&gt;;
}

// GrandChildComponent.js
function GrandChildComponent({ user }) {
  // 데이터가 최종적으로 렌더링되는 프레젠테이션 컴포넌트
  return &lt;div&gt;{user}&lt;/div&gt;;
}</code></pre>
<h3 id="❌-프롭스-드릴링의-문제점">❌ <strong>프롭스 드릴링의 문제점</strong></h3>
<ol>
<li><strong>불필요한 전달</strong>: 중간 컴포넌트들이 사용하지 않는 데이터도 계속 전달해야 함<ol>
<li>예: 100번째 자식에게 전달하려면 99개의 중간 컴포넌트를 거쳐야 함</li>
</ol>
</li>
<li><strong>유지보수 어려움</strong>: 깊은 계층 구조에서 전달 로직이 복잡해짐</li>
<li><strong>재사용성 저하</strong>: 중간 컴포넌트가 데이터 전달에 의존하게 됨</li>
</ol>
<hr />
<h3 id="🛠-리액트의-해결-방법-전역-상태-관리">🛠 <strong>리액트의 해결 방법: 전역 상태 관리</strong></h3>
<ul>
<li>리액트는 이러한 문제를 해결하기 위해 <strong>전역 상태 관리</strong> 기능을 제공함</li>
<li>전역 상태 관리를 사용하면 <strong>데이터가 필요한 컴포넌트에서 바로 접근 가능</strong>하며, 중간 컴포넌트를 거칠 필요 없음</li>
<li>대표적인 도구:<ul>
<li><strong>Context API</strong>: 리액트 내장 기능</li>
<li><strong>Redux</strong>: 널리 사용되는 외부 라이브러리</li>
<li><strong>Zustand</strong>: 경량화된 상태 관리 도구</li>
</ul>
</li>
</ul>