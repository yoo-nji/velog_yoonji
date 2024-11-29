<h2 id="클릭-이벤트-click-event">클릭 이벤트 (Click Event)</h2>
<p><strong>리액트 이벤트는 카멜 케이스</strong>로 작성하며, 함수 참조 방식(<code>onClick={handler}</code>)으로 사용함</p>
<pre><code class="language-tsx">// ❌ 잘못된 사용 예
&lt;button onclick=&quot;clickHandler&quot;&gt;Click me&lt;/button&gt;
&lt;button onclick=&quot;{clickHandler()}&quot;&gt;Click me&lt;/button&gt;
// ✅ 올바른 사용 예
&lt;button onClick={clickHandler}&gt;Click me&lt;/button&gt;</code></pre>
<h3 id="기본-클릭-이벤트-코드">기본 클릭 이벤트 코드</h3>
<pre><code class="language-tsx">export default function App() {
//✅ 리액트는 일반적으로 화살표 함수 사용(선언문도 가능하나 화살표 함수가 일반적)
  const clickHandler = () =&gt; {
    alert(&quot;Click!&quot;);
  };

  return (
    &lt;&gt;
      &lt;h1&gt;App&lt;/h1&gt;
      &lt;button onClick={clickHandler}&gt;Click me&lt;/button&gt;
    &lt;/&gt;
  );
}</code></pre>
<blockquote>
<p>⚠️ 함수 <strong>호출</strong> 방식으로 전달<code>({clickHandler()})</code>시 컴포넌트가 렌더링될 때마다 함수가 실행됨
⇒ 이를 피하기 위해 함수 참조로 전달할 것</p>
</blockquote>
<hr />
<h3 id="이벤트-객체의-baseevent">이벤트 객체의 BaseEvent</h3>
<p>이벤트 객체는 이벤트 발생 시 클릭 위치, 입력 키, 마우스 좌표 등의 정보를 포함함</p>
<p>이벤트 핸들러는 매개변수('e' 또는 'event')를 통해 이 정보에 접근 가능</p>
<pre><code class="language-tsx">// ❌ 매개변수 없이 사용하면 BaseEvent 정보를 활용할 수 없음
const handleClick = () =&gt; {
  // 이벤트 객체의 정보에 접근 불가
};

// ✅ 매개변수로 이벤트 객체를 받아 BaseEvent 정보 활용 가능
const handleClick = (event: React.MouseEvent) =&gt; {
  console.log(event.nativeEvent); // 원본 DOM 이벤트
  console.log(event.isPropagationStopped()); // 이벤트 전파 중단 여부
  console.log(event.type); // 이벤트 타입
};</code></pre>
<hr />
<h2 id="체인지-이벤트-change-event">체인지 이벤트 (Change Event)</h2>
<p>입력 값이 변경될 때 발생하는 이벤트. <code>e.target.value</code>를 통해 현재 입력된 값을 가져올 수 있음</p>
<h3 id="자동-타입-추론">자동 타입 추론</h3>
<p>타입스크립트 사용 시 <strong>인라인 화살표 함수</strong>를 사용하면 이벤트 객체의 타입을 자동으로 추론함</p>
<pre><code class="language-tsx">// ✅ 인라인 화살표 함수로 작성하면 자동 타입 추론
&lt;input type=&quot;text&quot; onChange={(e) =&gt; {
  console.log(e.target.value); // e의 타입이 자동으로 추론됨
}} /&gt;</code></pre>
<p>이렇게 인라인 화살표 함수를 사용하면 TypeScript가 이벤트 객체의 타입을 자동으로 추론해주며, 이 추론된 타입을 함수에 활용 가능</p>
<h3 id="체인지-이벤트-핸들러-예제">체인지 이벤트 핸들러 예제</h3>
<p>changeHandler 함수는 input 요소의 값이 변경될 때마다 호출됨</p>
<pre><code class="language-tsx">const changeHandler = (e: React.ChangeEvent&lt;HTMLInputElement&gt;) =&gt; {
  console.log(e.target.value);
};

return &lt;input type=&quot;text&quot; onChange={changeHandler} /&gt;;</code></pre>
<hr />
<h2 id="키보드-이벤트-keyboard-event">키보드 이벤트 (Keyboard Event)</h2>
<p>키보드 입력과 관련된 이벤트로, 키가 눌릴 때 <code>onKeyDown</code> 핸들러를 사용함</p>
<pre><code class="language-tsx">const keyDownHandler = (e: React.KeyboardEvent&lt;HTMLInputElement&gt;) =&gt; {
  console.log(e.key); // 눌린 키 이름
  console.log(e.keyCode); // 키 코드
};

return &lt;input type=&quot;text&quot; onKeyDown={keyDownHandler} /&gt;;</code></pre>
<hr />
<h2 id="폼-이벤트-form-event">폼 이벤트 (Form Event)</h2>
<p>리액트의 SPA(Single Page Application)에서는 폼 제출 시 새로고침이 불필요함</p>
<p>폼의 제출 이벤트(<code>onSubmit</code>)에서 <strong>페이지 새로고침</strong>을 막아 SPA 동작을 유지해야 함</p>
<pre><code class="language-tsx">const submitHandler = (e: React.FormEvent&lt;HTMLFormElement&gt;) =&gt; {
  e.preventDefault(); // 기본 동작 방지
     //적절한 로직 처리
};

return (
  &lt;form onSubmit={submitHandler}&gt;
    &lt;input type=&quot;text&quot; name=&quot;id&quot; /&gt;
    &lt;button type=&quot;submit&quot;&gt;Submit&lt;/button&gt;
  &lt;/form&gt;
);</code></pre>
<hr />
<h2 id="이벤트-핸들러와-매개변수">이벤트 핸들러와 매개변수</h2>
<p>이벤트 핸들러에 매개변수를 전달할 때는 화살표 함수로 감싸서 전달해야 함</p>
<h3 id="매개변수가-필요-없는-경우">매개변수가 필요 없는 경우</h3>
<pre><code class="language-tsx">// 매개변수가 필요없을 때는 함수 참조만 전달
&lt;button onClick={handleClick}&gt;Click&lt;/button&gt;

// 또는 매개변수 없는 화살표 함수로도 가능
&lt;button onClick={() =&gt; handleClick()}&gt;Click&lt;/button&gt;</code></pre>
<h3 id="매개변수가-필요한-경우">매개변수가 필요한 경우</h3>
<pre><code class="language-tsx">// 매개변수가 필요할 때는 화살표 함수로 래핑
&lt;button onClick={() =&gt; handleClick(param)}&gt;Click&lt;/button&gt;</code></pre>
<h3 id="이벤트-객체와-매개변수-모두-필요한-경우">이벤트 객체와 매개변수 모두 필요한 경우</h3>
<pre><code class="language-tsx">// 이벤트 객체(e)를 명시적으로 전달하고 싶을 때
&lt;button onClick={(e) =&gt; handleClick(e)}&gt;Click&lt;/button&gt;

// 이벤트 객체와 다른 매개변수를 함께 전달할 때
&lt;button onClick={(e) =&gt; handleClick(e, param)}&gt;Click&lt;/button&gt;</code></pre>
<blockquote>
<p>이벤트 객체만 필요한 경우에는 함수 이름만 전달하는 방식이 더 간단하고 권장됨</p>
</blockquote>