<h2 id="이벤트">이벤트</h2>
<ul>
<li>자바스크립트 이벤트는 브라우저에서 발생하는 사용자 상호작용을 의미</li>
<li>웹 애플리케이션과 사용자 간 인터랙션의 핵심</li>
<li>클릭, 더블 클릭, 키보드 입력, 스크롤 등의 상호작용 발생 시 이벤트가 트리거되어 웹 페이지가 동적으로 반응</li>
</ul>
<p><strong>이벤트 등록의 기본 문법</strong></p>
<pre><code class="language-jsx">[문서객체].addEventListener(&quot;이벤트명&quot;, 콜백함수);</code></pre>
<h3 id="이벤트-주요-구성">이벤트 주요 구성</h3>
<ul>
<li><strong><code>이벤트 타겟</code> (Event Target)</strong><ul>
<li>이벤트 타겟은 <strong>어느 요소에서 이벤트가 발생했는지</strong>를 나타냄. 쉽게 말해, 이벤트가 걸리는 요소 자체를 의미</li>
</ul>
</li>
<li><strong><code>이벤트 타입</code> (Event Type)</strong><ul>
<li>이벤트 타입은 <strong>이벤트의 종류</strong>를 나타냄. 예: 클릭, 키보드 입력, 드래그, 마우스 오버 등. 이 타입에 따라 이벤트 발생 시 트리거되는 작업이 달라짐</li>
</ul>
</li>
<li><strong><code>이벤트 핸들러</code> (Event Handler)</strong><ul>
<li>이벤트 핸들러는 <strong>이벤트 발생 시 실행할 콜백 함수</strong>. 예: 버튼 클릭 시 특정 작업을 수행하도록 정의한 함수가 이벤트 핸들러</li>
</ul>
</li>
</ul>
<p><strong>이벤트 처리 예제: 버튼 클릭 이벤트</strong></p>
<pre><code class="language-html">&lt;button id=&quot;myButton&quot;&gt;클릭하세요&lt;/button&gt;</code></pre>
<pre><code class="language-jsx">// 버튼 요소 선택
const button = document.getElementById('myButton');

// 클릭 이벤트 핸들러 정의
function handleClick() {
  alert('버튼이 클릭됨');
}

// 버튼에 클릭 이벤트 리스너 추가
button.addEventListener('click', handleClick);</code></pre>
<ul>
<li><strong>이벤트 타겟</strong>: <code>myButton</code> ID를 가진 버튼 요소</li>
<li><strong>이벤트 타입</strong>: <code>'click'</code> (클릭 이벤트)</li>
<li><strong>이벤트 핸들러</strong>: <code>handleClick</code> 함수 (클릭 시 알림 표시)</li>
</ul>
<hr />
<h1 id="html-속성을-통한-이벤트-지정"><strong>HTML 속성을 통한 이벤트 지정</strong></h1>
<p>HTML 태그에 직접 이벤트 속성 지정으로 이벤트 처리 가능. 그러나 이 방식은 <strong>관심사 분리(Separation of Concerns)</strong> 원칙 미준수로 유지보수성 측면에서 지양됨</p>
<pre><code class="language-html">&lt;button onclick=&quot;alert('버튼이 클릭되었습니다!')&quot;&gt;클릭하세요&lt;/button&gt;</code></pre>
<h3 id="주요-html-이벤트-속성">주요 HTML 이벤트 속성</h3>
<ul>
<li><code>onclick</code>: 클릭 이벤트</li>
<li><code>onmouseover</code>: 마우스 오버 이벤트</li>
<li><code>onkeydown</code>: 키보드 키 다운 이벤트</li>
</ul>
<blockquote>
<p><strong>관심사 분리란?</strong>HTML(구조), CSS(스타일), JavaScript(동작)를 분리하여 코드의 <strong>유지보수성과 재사용성을 높이는 개념</strong>. 따라서 이벤트 처리는 가능하면 JavaScript 파일에서 <code>addEventListener()</code> 사용이 권장됨</p>
</blockquote>
<h1 id="이벤트-객체-event-object"><strong>이벤트 객체 (Event Object)</strong></h1>
<p>이벤트 핸들러 함수는 이벤트에 대한 상세 정보를 담은 <strong>이벤트 객체</strong>를 매개변수로 받음. 이를 통해 발생한 이벤트에 대한 다양한 정보 사용 가능</p>
<h3 id="주요-이벤트-객체-속성">주요 이벤트 객체 속성</h3>
<ul>
<li><strong>event.type</strong>: 발생한 이벤트의 유형 (예: <code>'click'</code>, <code>'keydown'</code>)</li>
<li><strong>event.target</strong>: 이벤트가 발생한 요소 (이벤트 타겟)</li>
<li><strong>event.currentTarget</strong>: 현재 이벤트가 발생 중인 요소 (이벤트 버블링 중 변할 수 있음)</li>
</ul>
<pre><code class="language-jsx">$$li.forEach((li) =&gt; {
  li.addEventListener('click', function (e) {
    e.currentTarget.remove(); // 이벤트가 발생한 요소를 삭제
  });
});</code></pre>
<ul>
<li><strong>event.preventDefault() ⭐️</strong>: 이벤트의 기본 동작을 취소</li>
<li><strong>event.stopPropagation()</strong>: 이벤트 버블링을 중지</li>
</ul>
<pre><code class="language-jsx">document.getElementById('myButton').addEventListener('click', function(event) {
    console.log('이벤트 타입:', event.type);
    console.log('타겟 요소:', event.target);
    event.preventDefault(); // 기본 동작 방지
});</code></pre>
<h1 id="자주-사용하는-이벤트-요약"><strong>자주 사용하는 이벤트 요약</strong></h1>
<h3 id="1-클릭-이벤트-click">1. 클릭 이벤트 (click)</h3>
<ul>
<li><strong>설명</strong>: 사용자가 요소를 클릭할 때 발생하는 이벤트=</li>
</ul>
<pre><code class="language-html">html
코드 복사
&lt;button id=&quot;myButton&quot;&gt;클릭하세요!&lt;/button&gt;
&lt;div id=&quot;output&quot;&gt;&lt;/div&gt;

&lt;script&gt;
    const button = document.getElementById(&quot;myButton&quot;);
    const output = document.getElementById(&quot;output&quot;);

    button.addEventListener(&quot;click&quot;, function() {
        output.textContent = &quot;버튼이 클릭되었습니다!&quot;;
        output.style.color = &quot;green&quot;;
    });
&lt;/script&gt;
</code></pre>
<h3 id="2-키보드-이벤트-keydown-keyup">2. 키보드 이벤트 (keydown, keyup)</h3>
<ul>
<li><strong>설명</strong>: 키보드의 키를 누르거나 뗄 때 발생하는 이벤트</li>
<li><code>keydown</code>은 키를 누르는 순간, <code>keyup</code>은 키를 뗄 때 발생=</li>
</ul>
<pre><code class="language-html">html
코드 복사
&lt;input type=&quot;text&quot; id=&quot;inputField&quot; placeholder=&quot;여기에 입력하세요...&quot; /&gt;
&lt;div id=&quot;keyOutput&quot;&gt;&lt;/div&gt;

&lt;script&gt;
    const inputField = document.getElementById(&quot;inputField&quot;);
    const keyOutput = document.getElementById(&quot;keyOutput&quot;);

    inputField.addEventListener(&quot;keydown&quot;, function(event) {
        keyOutput.textContent = `누른 키: ${event.key}`;
    });

    inputField.addEventListener(&quot;keyup&quot;, function(event) {
        keyOutput.textContent += ` (뗀 키: ${event.key})`;
    });
&lt;/script&gt;
</code></pre>
<h3 id="3-드래그-이벤트-drag-dragstart-dragend">3. 드래그 이벤트 (drag, dragstart, dragend)</h3>
<ul>
<li><strong>설명</strong>: 사용자가 요소를 드래그할 때 발생하는 이벤트</li>
<li>사용자 인터페이스(UI)에서 요소를 이동하거나 재배치할 때 사용</li>
</ul>
<pre><code class="language-html">&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;ko&quot;&gt;
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot;&gt;
    &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;&gt;
    &lt;title&gt;드래그 이벤트 예제&lt;/title&gt;
    &lt;style&gt;
        #draggable {
            width: 100px;
            height: 100px;
            background-color: blue;
            cursor: move; /* 드래그 시 커서 변경 */
            position: relative;
        }
    &lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div id=&quot;draggable&quot; draggable=&quot;true&quot;&gt;드래그 해보세요!&lt;/div&gt;
    &lt;div id=&quot;status&quot;&gt;&lt;/div&gt;

    &lt;script&gt;
        const draggable = document.getElementById(&quot;draggable&quot;);
        const status = document.getElementById(&quot;status&quot;);

        draggable.addEventListener(&quot;dragstart&quot;, function(event) {
            status.textContent = &quot;드래그가 시작되었습니다!&quot;;
            event.dataTransfer.setData(&quot;text/plain&quot;, &quot;이것은 드래그 중입니다.&quot;);
        });

        draggable.addEventListener(&quot;dragend&quot;, function(event) {
            status.textContent = &quot;드래그가 종료되었습니다!&quot;;
        });
    &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</code></pre>
<h3 id="4-폼-이벤트-submit-change-input">4. 폼 이벤트 (submit, change, input)</h3>
<ul>
<li><strong>설명</strong>: 사용자가 폼을 제출하거나, 입력 값을 변경할 때 발생하는 이벤트.</li>
</ul>
<pre><code class="language-html">&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;ko&quot;&gt;
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot;&gt;
    &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;&gt;
    &lt;title&gt;폼 이벤트 예제&lt;/title&gt;
    &lt;style&gt;
        #output {
            margin-top: 20px;
            color: blue;
        }
    &lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;form id=&quot;myForm&quot;&gt;
        &lt;label for=&quot;name&quot;&gt;이름:&lt;/label&gt;
        &lt;input type=&quot;text&quot; id=&quot;name&quot; placeholder=&quot;이름을 입력하세요&quot; required&gt;
        &lt;br&gt;
        &lt;label for=&quot;email&quot;&gt;이메일:&lt;/label&gt;
        &lt;input type=&quot;email&quot; id=&quot;email&quot; placeholder=&quot;이메일을 입력하세요&quot; required&gt;
        &lt;br&gt;
        &lt;button type=&quot;submit&quot;&gt;제출&lt;/button&gt;
    &lt;/form&gt;
    &lt;div id=&quot;output&quot;&gt;&lt;/div&gt;

    &lt;script&gt;
        const form = document.getElementById(&quot;myForm&quot;);
        const output = document.getElementById(&quot;output&quot;);

        // submit 이벤트 핸들러
        form.addEventListener(&quot;submit&quot;, function(event) {
            event.preventDefault(); // 기본 제출 동작 방지
            const name = document.getElementById(&quot;name&quot;).value;
            const email = document.getElementById(&quot;email&quot;).value;
            output.textContent = `이름: ${name}, 이메일: ${email}이(가) 제출되었습니다.`;
        });

        // change 이벤트 핸들러
        const nameInput = document.getElementById(&quot;name&quot;);
        nameInput.addEventListener(&quot;change&quot;, function() {
            output.textContent += ` 이름이 변경되었습니다: ${nameInput.value}`;
        });

        // input 이벤트 핸들러
        nameInput.addEventListener(&quot;input&quot;, function() {
            console.log(`현재 이름 입력: ${nameInput.value}`);
        });
    &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</code></pre>
<hr />
<h1 id="키코드-key-code-정보">키코드 (Key Code) 정보</h1>
<p>키보드 이벤트 시 특정 키를 식별할 수 있는 고유한 키 코드가 존재합니다. 주로 <code>event.key</code>나 <code>event.code</code> 속성을 사용하는 것이 권장됩니다.</p>
<ul>
<li>엔터 키: 13</li>
<li>스페이스바: 32</li>
<li>화살표 키: 왼쪽(37), 위(38), 오른쪽(39), 아래(40)</li>
</ul>
<pre><code class="language-jsx">document.addEventListener(&quot;keydown&quot;, function(event) {
    if (event.keyCode === 13) {
        console.log(&quot;엔터 키가 눌렸습니다!&quot;);
    }
});</code></pre>
<blockquote>
<p>📚 다른 이벤트 정보는 <a href="https://developer.mozilla.org/ko/docs/Web/API/Element/click_event">여기</a> 참고</p>
</blockquote>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>