<h2 id="useref-비제어-컨트롤러로-dom-직접-조작"><strong>useRef: 비제어 컨트롤러로 DOM 직접 조작</strong></h2>
<h3 id="비제어-컨트롤러란"><strong>비제어 컨트롤러란?</strong></h3>
<p>비제어 컨트롤러는 DOM 요소에 직접 접근하여 값을 관리하는 방식으로, 실시간 값 변화 감지 불가</p>
<p>useRef를 사용해 DOM 요소 참조</p>
<h3 id="useref란"><strong>useRef란?</strong></h3>
<p>React에서 제공하는 Hook으로, 값을 보관하고 관리할 수 있는 저장소</p>
<p><strong>주요 특징:</strong></p>
<ul>
<li>컴포넌트가 리렌더링되어도 동일한 참조값 유지</li>
<li>값이 변경되어도 컴포넌트가 리렌더링되지 않음</li>
<li>DOM 요소에 직접 접근할 때 사용되며, current 프로퍼티를 통해 값을 안전하게 관리</li>
</ul>
<blockquote>
<p><strong>🤔 DOM 조작에 querySelector 대신 useRef를 사용하는 이유</strong>
querySelector는 실제 DOM을 직접 조작하여 React의 가상 DOM 시스템과 충돌 가능
컴포넌트가 리렌더링될 때마다 참조가 깨질 수 있고, React의 단방향 데이터 흐름을 방해할 수 있음
❌ React에서도 직접적인 DOM 조작을 권장하지 않음</p>
</blockquote>
<p>예시코드</p>
<pre><code class="language-tsx">import { useRef } from &quot;react&quot;;

export default function App() {
  const inputRef = useRef&lt;HTMLInputElement | null&gt;(null);

  const handleSubmit = () =&gt; {
    console.log(inputRef.current?.value); // input 값 가져오기
  };

  return (
    &lt;&gt;
      &lt;input type=&quot;text&quot; ref={inputRef} placeholder=&quot;Enter your name&quot; /&gt;
      &lt;button onClick={handleSubmit}&gt;Submit&lt;/button&gt;
    &lt;/&gt;
  );
}</code></pre>
<hr />
<h2 id="useref와-dom-접근"><strong>useRef와 DOM 접근</strong></h2>
<p><code>useRef</code>로 생성된 객체는 <code>current</code> 프로퍼티를 통해 DOM 요소에 접근 가능</p>
<p>이를 통해 값이나 메서드를 호출 가능</p>
<pre><code class="language-tsx">console.log(inputRef.current?.value); // input의 값
inputRef.current?.focus(); // input에 포커스</code></pre>
<hr />
<h2 id="폼-데이터"><strong>폼 데이터</strong></h2>
<p><code>useRef</code>를 여러 개 사용하여 폼 입력값 가져오기 가능</p>
<p><strong>예제: 다중 입력값 처리</strong></p>
<pre><code class="language-tsx">import { useRef } from &quot;react&quot;;

export default function App() {
  const idRef = useRef&lt;HTMLInputElement | null&gt;(null); //ref 객체
  const pwRef = useRef&lt;HTMLInputElement | null&gt;(null);

  const handleSubmit = (e: React.FormEvent&lt;HTMLFormElement&gt;) =&gt; {
    e.preventDefault();
    console.log(&quot;ID:&quot;, idRef.current?.value);
    console.log(&quot;Password:&quot;, pwRef.current?.value);
  };

  return (
    &lt;form onSubmit={handleSubmit}&gt;
      &lt;input type=&quot;text&quot; ref={idRef} placeholder=&quot;아이디 입력&quot; /&gt;
      &lt;input type=&quot;password&quot; ref={pwRef} placeholder=&quot;비밀번호  입력&quot; /&gt;
      &lt;button type=&quot;submit&quot;&gt;로그인&lt;/button&gt;
    &lt;/form&gt;
  );
}</code></pre>
<hr />
<h2 id="라디오-버튼과-체크박스-처리"><strong>라디오 버튼과 체크박스 처리</strong></h2>
<h3 id="라디오-버튼"><strong>라디오 버튼</strong></h3>
<p><code>useRef</code>와 배열을 활용해 선택된 라디오 버튼의 값을 가져옴</p>
<p>라디오 버튼 처리 시 필요한 특별 처리:</p>
<ul>
<li>배열로 참조 관리 (<code>useRef&lt;HTMLInputElement[]&gt;([])</code>)</li>
<li>각 라디오 버튼에 <code>ref</code> 콜백 함수로 배열에 요소 할당</li>
<li><code>find()</code> 메서드로 선택된 라디오 버튼 탐색</li>
</ul>
<p>예시 코드:</p>
<pre><code class="language-tsx">const radioRef = useRef&lt;HTMLInputElement[]&gt;([]);

// 선택된 라디오 버튼 찾기
const selectedRadio = radioRef.current.find((radio) =&gt; radio.checked);
console.log(selectedRadio?.value);

// JSX에서 ref 설정
&lt;input
  type=&quot;radio&quot;
  ref={(el) =&gt; {
    if (el) radioRef.current[0] = el;
  }}
  name=&quot;gender&quot;
  value=&quot;female&quot;
  defaultChecked
/&gt;
&lt;input
  type=&quot;radio&quot;
  ref={(el) =&gt; {
    if (el) radioRef.current[1] = el;
  }}
  name=&quot;gender&quot;
  value=&quot;male&quot;
/&gt;</code></pre>
<hr />
<h3 id="체크박스"><strong>체크박스</strong></h3>
<p><code>checked</code> 속성으로 체크 여부 확인</p>
<pre><code class="language-tsx">const checkboxRef = useRef&lt;HTMLInputElement | null&gt;(null);

console.log(&quot;Checked:&quot;, checkboxRef.current?.checked);</code></pre>
<hr />
<h2 id="제어-컨트롤러-vs-비제어-컨트롤러"><strong>제어 컨트롤러 vs 비제어 컨트롤러</strong></h2>
<table>
<thead>
<tr>
<th><strong>특징</strong></th>
<th><strong>제어 컨트롤러</strong></th>
<th><strong>비제어 컨트롤러</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>기본 원리</strong></td>
<td>상태(state)로 값 관리</td>
<td>DOM 요소에 직접 접근</td>
</tr>
<tr>
<td><strong>실시간 렌더링</strong></td>
<td>✅ 지원</td>
<td>❌ 지원하지 않음</td>
</tr>
<tr>
<td><strong>사용 사례</strong></td>
<td>실시간 상태 반영이 필요한 경우</td>
<td>간단한 DOM 접근, 초기화 작업 등</td>
</tr>
</tbody></table>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>