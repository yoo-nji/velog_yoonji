<h2 id="클래스형-컴포넌트"><strong>클래스형 컴포넌트</strong></h2>
<p>리액트 초기에는 클래스형 컴포넌트가 주로 사용됨. 클래스형 컴포넌트는 <code>Component</code>를 상속받아 만들어짐</p>
<p><strong>예제 코드:</strong></p>
<pre><code class="language-jsx">import { Component } from &quot;react&quot;;

class App extends Component {
  render() {
    return &lt;h1&gt;App&lt;/h1&gt;;
  }
}

export default App;</code></pre>
<h2 id="함수형-컴포넌트"><strong>함수형 컴포넌트</strong></h2>
<p>함수형 컴포넌트는 함수의 형태로 작성됨. 최근에는 React의 주요 작성 방식으로 자리잡음</p>
<p><strong>예제 코드:</strong></p>
<pre><code class="language-jsx">export default function App() {
  return &lt;h1&gt;App&lt;/h1&gt;;
}</code></pre>
<h3 id="클래스형-컴포넌트가-덜-사용되게-된-이유"><strong>클래스형 컴포넌트가 덜 사용되게 된 이유</strong></h3>
<ol>
<li><strong>복잡한 생명주기 메서드</strong><ul>
<li><code>componentDidMount</code>, <code>componentDidUpdate</code> 등 여러 생명주기 메서드를 사용해야 하며, 이를 관리하기가 까다로움</li>
</ul>
</li>
<li><strong>this 바인딩 문제</strong><ul>
<li>클래스 내부의 메서드에서 <code>this</code>를 명시적으로 바인딩하거나 <code>bind</code>를 사용해야 해서 추가적인 작업이 필요함</li>
</ul>
</li>
<li><strong>보일러플레이트 코드</strong><ul>
<li>클래스형 컴포넌트는 상태 선언 등 기본 작업을 위해 불필요한 코드가 많이 작성됨</li>
</ul>
</li>
</ol>
<hr />
<h3 id="함수형-컴포넌트를-선호하는-현재-이유"><strong>함수형 컴포넌트를 선호하는 현재 이유</strong></h3>
<ol>
<li><strong><code>Hooks</code> 도입</strong><ul>
<li><code>useState</code>, <code>useEffect</code> 등의 훅을 통해 상태 관리와 생명주기 메서드를 간결하고 직관적으로 처리 가능</li>
</ul>
</li>
<li><strong>간결한 코드</strong><ul>
<li>함수형 컴포넌트는 클래스형 컴포넌트와 달리 불필요한 코드 없이 로직에 집중 가능</li>
</ul>
</li>
<li><strong>테스트 용이성</strong><ul>
<li>순수 함수로 작성되어 테스트가 더 간단함</li>
</ul>
</li>
<li><strong>성능 최적화</strong><ul>
<li>React 팀이 함수형 컴포넌트에 최적화 작업을 집중하는 중</li>
</ul>
</li>
<li><strong>커스텀 훅 사용</strong><ul>
<li>반복되는 로직을 커스텀 훅으로 분리하여 재사용성과 가독성을 높일 수 있음</li>
</ul>
</li>
</ol>
<hr />
<h2 id="reactfragment"><strong>React.Fragment</strong></h2>
<p>JSX에서는 여러 요소를 반환할 때 반드시 하나의 최상위 태그가 필요함. 이때 <code>React.Fragment</code>를 사용하면 불필요한 DOM 요소를 생성하지 않고 요소를 그룹화할 수 있음</p>
<h3 id="reactfragment의-전체-구문"><strong>React.Fragment의 전체 구문</strong></h3>
<pre><code class="language-jsx">import React from &quot;react&quot;;

return (
  &lt;React.Fragment&gt;
    &lt;h1&gt;제목&lt;/h1&gt;
    &lt;p&gt;내용&lt;/p&gt;
  &lt;/React.Fragment&gt;
);</code></pre>
<h3 id="단축-구문"><strong>단축 구문</strong></h3>
<p>React에서는 단축 문법으로 빈 태그 <code>&lt;&gt;</code>를 사용 가능. 이는 <code>React.Fragment</code>의 축약형임</p>
<pre><code class="language-jsx">return (
  &lt;&gt;
    &lt;h1&gt;제목&lt;/h1&gt;
    &lt;p&gt;내용&lt;/p&gt;
  &lt;/&gt;
);</code></pre>
<p><strong>주의사항:</strong></p>
<ul>
<li><code>React.Fragment</code>는 DOM에 추가 요소를 생성하지 않음</li>
<li>JSX 코드는 항상 <code>src</code> 폴더 내부에서 작성해야 함</li>
</ul>
<hr />
<h3 id="리액트에서-루트-컴포넌트"><strong>리액트에서 루트 컴포넌트</strong></h3>
<p>리액트 프로젝트에서 가장 최상위 컴포넌트를 <strong>루트 컴포넌트</strong>라고 하며, 일반적으로 <code>App</code> 컴포넌트가 루트 컴포넌트의 역할을 수행</p>
<p><strong>컴포넌트 트리와 DOM 트리</strong></p>
<ul>
<li><strong>컴포넌트 트리</strong>: 리액트에서의 컴포넌트 계층 구조를 의미</li>
<li><strong>DOM 트리</strong>: 브라우저가 렌더링한 HTML 요소들의 계층 구조로, 요소들 간의 부모-자식 및 형제 관계를 포함</li>
</ul>