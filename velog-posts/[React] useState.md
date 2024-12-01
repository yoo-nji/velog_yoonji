<h2 id="1-리액트에서-변수-선언-방식">1. 리액트에서 변수 선언 방식</h2>
<p><strong>1. 일반 변수 선언 (화면 렌더링에 영향 없음)</strong></p>
<ul>
<li>let, const, var로 선언된 변수들은 리액트가 변화 추적 불가</li>
</ul>
<p><strong>2. 상태 변수 선언 (화면 렌더링에 영향 있음)</strong></p>
<ul>
<li>useState와 같은 리액트 훅으로 선언</li>
<li>상태 변경 시 화면 자동 리렌더링</li>
</ul>
<hr />
<h2 id="2-usestate-제어-컨트롤러-상태-관리">2. useState: 제어 컨트롤러 상태 관리</h2>
<p>React에서 상태를 사용해 폼 요소나 화면 UI를 <strong>제어 컨트롤러</strong> 방식으로 관리 가능</p>
<h3 id="제어-컨트롤러란"><strong>제어 컨트롤러란?</strong></h3>
<ul>
<li><strong>제어 컨트롤러</strong>는 React 상태를 사용해 폼 요소나 UI를 <strong><code>실시간</code></strong>으로 제어하는 방식임</li>
</ul>
<h3 id="usestate란"><strong>useState란?</strong></h3>
<ul>
<li>React 16.8에 도입된 <strong>훅(hook)</strong></li>
<li>상태와 상태를 변경하는 함수를 배열로 반환</li>
</ul>
<p><strong>기본 문법</strong></p>
<pre><code class="language-tsx">// 비구조화할당
const [state, setState] = useState(초기값);</code></pre>
<ul>
<li><code>state</code>: 현재 상태 값</li>
<li><code>setState</code>: 상태 값을 변경하는 함수</li>
<li><code>초기값</code>: 상태의 초기값</li>
</ul>
<hr />
<h2 id="3-usestate-사용-예제">3. <strong>useState 사용 예제</strong></h2>
<h3 id="상태-관리로-화면-렌더링-반영"><strong>상태 관리로 화면 렌더링 반영</strong></h3>
<pre><code class="language-tsx">import { useState } from &quot;react&quot;;

export default function App() {
  const [count, setCount] = useState(0);

  const increment = () =&gt; {
    setCount(count + 1); //값 전달 시 count의 최신값으로 설정
  };

  return (
    &lt;div&gt;
      &lt;h1&gt;count: {count}&lt;/h1&gt;
      &lt;button onClick={increment}&gt;증가&lt;/button&gt;
    &lt;/div&gt;
  );
}</code></pre>
<blockquote>
<p>✅ 관례</p>
<ul>
<li>상태 이름이 <code>count</code>면 업데이트 함수는 <code>setCount</code>로 작명</li>
<li>예: <code>isVisible</code> → <code>setIsVisible</code>, <code>userName</code> → <code>setUserName</code></li>
</ul>
</blockquote>
<hr />
<h2 id="4-setstate의-두-가지-사용-방식">4. <strong>setState의 두 가지 사용 방식</strong></h2>
<h3 id="1-값-전달-방식"><strong>1. 값 전달 방식</strong></h3>
<pre><code class="language-tsx">setCount(count + 1); //값 전달 시 count의 최신값으로 설정</code></pre>
<ul>
<li>이전 상태를 참조하지 않을 때 사용</li>
</ul>
<h3 id="2-콜백-함수-방식-setstate현재상태-⇒-값"><strong>2. 콜백 함수 방식</strong> <code>setState((현재상태) ⇒ 값)</code></h3>
<pre><code class="language-tsx">setCount((count) =&gt; count + 1); //콜백함수 반환값이 count의 최신값으로 설정</code></pre>
<ul>
<li><code>이전 상태를 참조</code>해야 할 때 사용</li>
</ul>
<h3 id="3-두-방식-차이점">3. 두 방식 차이점</h3>
<p>값 전달 방식과 콜백 함수 방식의 주요 차이점은 상태 업데이트의 동작 방식에 있음</p>
<p>예시: 3번의 상태 업데이트 시도</p>
<pre><code class="language-tsx">const increment = () =&gt; {
  setCount(count + 1);
  setCount(count + 1);
  setCount(count + 1);
};</code></pre>
<p>count는 1만 증가함. 각 setCount가 동일한 count 값을 참조하기 때문(비동기)</p>
<p>하지만 콜백 함수 사용 시:</p>
<pre><code class="language-tsx">const increment = () =&gt; {
  setCount(prev =&gt; prev + 1);
  setCount(prev =&gt; prev + 1);
  setCount(prev =&gt; prev + 1);
};</code></pre>
<p>count가 3씩 증가함. 각 콜백이 이전 상태의 최신값을 참조하여 업데이트하기 때문</p>
<hr />
<h2 id="5-리액트에서의-불변성">5. <strong>리액트에서의 불변성</strong></h2>
<p>React는 <strong>불변성</strong>을 기반으로 상태 변화를 감지</p>
<p>✅ 즉, 상태를 직접 변경하지 않고 새로운 상태를 생성해야 함</p>
<h3 id="배열-상태-예제"><strong>배열 상태 예제</strong></h3>
<pre><code class="language-tsx">const [students, setStudents] = useState([&quot;james&quot;, &quot;john&quot;]);

const addStudent = () =&gt; {
  // ❌ 잘못된 방식 (원본 수정)
  // students.push(&quot;smith&quot;);
  // setStudents(students);

  // ✅ 올바른 방식 (새 배열 생성)
  setStudents((prevStudents) =&gt; [...prevStudents, &quot;smith&quot;]);
};</code></pre>
<blockquote>
<p>💡 올바른 방식: spread 연산자(...), map(), filter()를 사용해 새로운 상태를 생성</p>
</blockquote>
<hr />
<h2 id="6-제네릭-타입으로-상태-관리">6. <strong>제네릭 타입으로 상태 관리</strong></h2>
<h3 id="타입스크립트와-usestate"><strong>타입스크립트와 useState</strong></h3>
<pre><code class="language-tsx">interface User {
  name: string;
  age: number;
  gender?: string; // 선택적(optional) 속성
}

const [user, setUser] = useState&lt;User&gt;({ name: &quot;john&quot;, age: 20 });

// gender는 선택적 속성으로 추가 가능
const updateUser = () =&gt; {
  setUser(prev =&gt; ({ ...prev, gender: &quot;male&quot; }));
};</code></pre>
<h2 id="7-폼-요소-상태-관리">7. <strong>폼 요소 상태 관리</strong></h2>
<h3 id="inputtypetext">input[type=&quot;text&quot;]</h3>
<pre><code class="language-tsx">const [input, setInput] = useState(&quot;&quot;);

const handleChange = (e: React.ChangeEvent&lt;HTMLInputElement&gt;) =&gt; {
  setInput(e.target.value);
};

return &lt;input type=&quot;text&quot; value={input} onChange={handleChange} /&gt;;

// 혹은 onChange 내에서 직접 호출
&lt;input type=&quot;text&quot; value={input} onChange={(e) =&gt; setInput(e.target.value)} /&gt;</code></pre>
<blockquote>
<p>💡 <strong><code>value</code></strong>와 <strong><code>onChange</code></strong>는 폼 요소 제어 시 세트로 사용</p>
<ul>
<li>value 속성 없으면 리셋 기능 추가해도 인풋 내부 값 제어 불가</li>
<li>폼 요소 완전 제어를 위해 value와 onChange 함께 사용 필수</li>
</ul>
</blockquote>
<h3 id="inputtypedate"><strong>input[type='date']</strong></h3>
<pre><code class="language-jsx">// date input
const [dateInput, setDateInput] = useState(&quot;&quot;);
&lt;input type=&quot;date&quot; value={dateInput} onChange={(e) =&gt; setDateInput(e.target.value)} /&gt;</code></pre>
<h3 id="textarea">textarea</h3>
<pre><code class="language-jsx">// textarea
const [textInput, setTextInput] = useState(&quot;초기값&quot;);
&lt;textarea value={textInput} onChange={(e) =&gt; setTextInput(e.target.value)} /&gt;</code></pre>
<h3 id="체크박스"><strong>체크박스</strong></h3>
<pre><code class="language-tsx">const [checked, setChecked] = useState(false);
&lt;input type=&quot;checkbox&quot; checked={checked} onChange={() =&gt; setChecked(!checked)} /&gt;;</code></pre>
<h3 id="radio">radio</h3>
<p><strong><code>초기값</code></strong> 설정 필수 ⇒ defaultChecked 설정</p>
<pre><code class="language-jsx">const [radioValue, setRadioValue] = useState(&quot;male&quot;);
      &lt;div&gt;
        &lt;input
          type=&quot;radio&quot;
          name=&quot;gender&quot;
          className=&quot;border border-slate-500&quot;
          value={&quot;male&quot;}
          defaultChecked
          onChange={() =&gt; setRadioValue(&quot;male&quot;)}
        /&gt;
        male
      &lt;/div&gt;
      &lt;div&gt;
        &lt;input
          type=&quot;radio&quot;
          name=&quot;gender&quot;
          className=&quot;border border-slate-500&quot;
          value={&quot;female&quot;}
          onChange={() =&gt; setRadioValue(&quot;female&quot;)}
        /&gt;
        female
      &lt;/div&gt;</code></pre>
<h3 id="셀렉트-박스"><strong>셀렉트 박스</strong></h3>
<p>select 요소 초기값 지정 시 defaultValue 속성 사용 가능</p>
<p><strong>value와 defaultValue 차이점</strong></p>
<ul>
<li>value: <strong>컴포넌트가 제어되는 상태</strong>로, React에 의해 값이 관리됨</li>
<li>defaultValue: 컴포넌트의 초기값만 설정하고 이후 React의 제어를 받지 않음</li>
</ul>
<pre><code class="language-tsx">const [selected, setSelected] = useState(&quot;apple&quot;);
&lt;select value={selected} onChange={(e) =&gt; setSelected(e.target.value)}&gt;
  &lt;option value=&quot;apple&quot;&gt;Apple&lt;/option&gt;
  &lt;option value=&quot;banana&quot;&gt;Banana&lt;/option&gt;
&lt;/select&gt;;</code></pre>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>