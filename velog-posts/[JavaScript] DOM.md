<h1 id="domdocument-object-model이란"><strong>DOM(Document Object Model)이란?</strong></h1>
<p>DOM(Document Object Model): HTML 문서를 객체 기반의 트리 구조로 표현. JavaScript로 HTML 요소를 동적으로 조작 가능</p>
<blockquote>
<p><strong>🌳 DOM 구조 시각화 도구</strong>
<a href="https://bioub.github.io/dom-visualizer/">DOM Visualizer</a>: 웹 페이지의 DOM 구조를 시각적으로 표현
<a href="https://software.hixie.ch/utilities/js/live-dom-viewer/">Live DOM Viewer</a>: 실시간 HTML 입력 및 DOM 구조 확인 가능</p>
</blockquote>
<p><strong>HTML 코드 예제</strong></p>
<pre><code class="language-html">&lt;html&gt;
&lt;head&gt;
    &lt;title&gt;DOM 트리&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div id=&quot;container&quot;&gt;
        &lt;h1&gt;안녕하세요&lt;/h1&gt;
        &lt;p&gt;이것은 &lt;span&gt;간단한&lt;/span&gt; DOM 트리 예제입니다.&lt;/p&gt;
    &lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>
<p><strong>이 HTML 코드의 DOM 트리 구조 형성</strong></p>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/8f0ae4d4-c15f-4034-920e-097a1186653e/image.png" /></p>
<p>이 구조에서 각 HTML 요소는 DOM 트리의 노드가 됨 </p>
<p>⇒ 이미지처럼 요소 간의 관계(부모-자식, 형제)를 명확히 볼 수 있음</p>
<p>공백과 줄바꿈도 텍스트 노드로 인식됨</p>
<p><strong>✅ HTML 안의 모든 것은 (심지어 주석이더라도) DOM을 구성함</strong></p>
<hr />
<h2 id="자바스크립트로-html-접근하기">자바스크립트로 HTML 접근하기</h2>
<p>자바스크립트를 사용한 HTML 문서의 DOM 접근 및 조작 방법 다양. 가장 기본적인 DOM 접근 메서드 소개</p>
<h3 id="documentqueryselector-⭐️"><code>document.querySelector()</code> ⭐️</h3>
<p>CSS 선택자를 사용하여 일치하는 <strong>첫 번째 요소</strong> 반환. 여러 요소 일치 시에도 첫 번째로 발견된 요소만 반환</p>
<p>매우 유연하고 복잡한 선택자 사용 가능</p>
<p>CSS 선택자를 사용한 접근 방법</p>
<ul>
<li><code>element</code>: 태그 이름으로 선택 (예: <code>div</code>)</li>
<li><code>#id</code>: ID로 선택 (예: <code>#myElement</code>)</li>
<li><code>.class</code>: 클래스로 선택 (예: <code>.myClass</code>)</li>
<li><code>[attribute]</code>: 속성으로 선택 (예: <code>[type=&quot;text&quot;]</code>)</li>
<li><code>selector1, selector2</code>: 다중 선택 (예: <code>div, p</code>)</li>
<li><code>selector1 selector2</code>: 자손 선택 (예: <code>div p</code>)</li>
<li><code>selector1 &gt; selector2</code>: 직계 자식 선택 (예: <code>ul &gt; li</code>)</li>
</ul>
<pre><code class="language-jsx">// ID로 단일 요소 선택
const singleEl = document.querySelector('#myId');

// 클래스로 모든 요소 선택
const allEl = document.querySelectorAll('.myClass');</code></pre>
<h3 id="documentqueryselectorall--⭐️"><code>document.querySelectorAll()</code>  ⭐️</h3>
<p>CSS 선택자와 일치하는 모든 요소를 <strong>NodeList</strong>로 반환. 반복 작업 수행 가능</p>
<p>NodeList는 <strong>유사 배열 객체</strong>로, 여러 요소에 대한 반복 작업 수행 가능. 예: document.querySelectorAll('.myClass')는 'myClass' 클래스를 가진 모든 요소 선택. 여러 요소를 한 번에 선택하고 조작하는 데 유용</p>
<p>유사배열이기 때문에 [ ]로 접근 가능</p>
<pre><code class="language-jsx">//전체
const pEl = document.querySelectorAll('p');

//일부
const firstpEl = document.querySelectorAll('p')[2];</code></pre>
<h3 id="documentgetelementbyid"><code>document.getElementById()</code></h3>
<p>주어진 ID와 일치하는 <strong>단일 요소</strong> 반환. 문서 내에서 유일해야 함</p>
<pre><code class="language-jsx">const element = document.getElementById('myElement');</code></pre>
<h3 id="documentgetelementsbyclassname"><code>document.getElementsByClassName()</code></h3>
<p>주어진 클래스 이름을 가진 모든 요소를 <strong>HTMLCollection</strong>으로 반환</p>
<pre><code class="language-jsx">const elements = document.getElementsByClassName('myClass');
const firstElement = elements[0];</code></pre>
<h2 id="문서-객체-조작하기">문서 객체 조작하기</h2>
<h3 id="1-스타일-변경">1. 스타일 변경</h3>
<p>DOM 요소의 스타일 변경으로 동적인 시각 효과 생성. <code>style</code> 속성이나 <code>classList</code>를 사용해 스타일 조작</p>
<pre><code class="language-jsx">const element = document.querySelector('#myElement');
element.style.backgroundColor = 'blue';
element.style.fontSize = '20px';</code></pre>
<h3 id="2-속성-추가-삭제-및-변경">2. 속성 추가, 삭제 및 변경</h3>
<p>DOM 요소의 속성 조작으로 동적인 기능 구현</p>
<pre><code class="language-jsx">// 속성 추가
const img = document.querySelector('img');
img.setAttribute('alt', '풍경 이미지');

// 속성 변경
img.setAttribute('src', 'new-image.jpg');

// 속성 가져오기
const altText = img.getAttribute('alt');
console.log(altText); // '풍경 이미지' 출력

const classValue = img.getAttribute('class');
console.log(classValue); // 클래스 값 출력 또는 null

// 속성 삭제
img.removeAttribute('title');

// 속성 존재 여부 확인
if (img.hasAttribute('src')) {
    console.log('src 속성 존재');
}</code></pre>
<h3 id="속성-조작-메서드-요약">속성 조작 메서드 요약</h3>
<ul>
<li><strong>setAttribute(속성명, 속성값)</strong>: 속성 추가 및 변경</li>
<li><strong>getAttribute()</strong>: 특정 속성 값 가져오기</li>
<li><strong>removeAttribute()</strong>: 특정 속성 제거</li>
</ul>
<blockquote>
<p>속성 조작 메서드는 <strong>기존 속성 값을 초기화</strong>할 수 있음. <strong>예</strong>, 'setAttribute()'로 class 설정 시 기존 클래스 덮어씌워짐. 반면 <code>'classList'</code> 메서드들은 <strong>기존 클래스 유지</strong>하며 특정 클래스만 추가나 제거 가능해 더 유연함</p>
</blockquote>
<h2 id="✅-class-속성-제어-메서드"><strong>✅ class 속성 제어 메서드</strong></h2>
<ul>
<li><strong>classList.add()</strong>: 클래스 추가 ⭐️</li>
<li><strong>classList.remove()</strong>: 클래스 제거 ⭐️</li>
<li><strong>classList.toggle()</strong>: 클래스 추가/제거 토글 ⭐️</li>
<li><strong>classList.contains()</strong>: 특정 클래스 포함 여부 확인 (true/false)</li>
</ul>
<pre><code class="language-jsx">const element = document.querySelector('#myElement');
element.classList.add('highlight');
element.classList.remove('hidden');
element.classList.toggle('active');</code></pre>
<h2 id="콘텐츠-조작">콘텐츠 조작</h2>
<ul>
<li><strong>innerText</strong>: 요소의 보이는 텍스트만 조작</li>
<li><strong>textContent</strong>: 모든 텍스트 콘텐츠 조작 (숨겨진 텍스트 포함) ⭐️</li>
<li><strong>innerHTML</strong>: 요소 내부의 HTML 콘텐츠 조작</li>
<li><strong>outerHTML</strong>: 요소 자체와 그 내부 HTML 포함하여 조작</li>
</ul>
<pre><code class="language-jsx">const container = document.getElementById(&quot;container&quot;);
container.textContent = &quot;새 텍스트 콘텐츠&quot;;
container.innerHTML = &quot;&lt;h1&gt;HTML 콘텐츠&lt;/h1&gt;&quot;;</code></pre>
<blockquote>
<p>⚠️ 주의: innerHTML은 XSS 공격에 취약할 수 있으며, textContent가 더 안전함</p>
</blockquote>
<h2 id="새로운-문서-객체-추가">새로운 문서 객체 추가</h2>
<p>새로운 문서 객체는 createElement()로 생성하고 appendChild() 또는 insertBefore()를 통해 추가함</p>
<h3 id="createelement--appendchild">createElement() + appendChild()</h3>
<ul>
<li>appendChild()는 항상 부모 요소의 <strong>마지막 자식</strong>으로만 요소 추가</li>
</ul>
<pre><code class="language-jsx">// 새 div 요소 생성
const newDiv = document.createElement('div');

// 텍스트 노드 생성
const newContent = document.createTextNode('안녕하세요!');

// 새 div에 텍스트 노드 추가
newDiv.appendChild(newContent);

// 기존 DOM에 새 div 추가
document.body.appendChild(newDiv);</code></pre>
<h3 id="createelement--insertbefore">createElement() + insertBefore()</h3>
<p>insertBefore()는 특정 노드 앞에 삽입할 때 유용함</p>
<p>이 메서드는 부모 노드에서 호출되며, 두 개의 매개변수를 받음: 첫 번째는 삽입할 새 노드이고, 두 번째는 기준이 되는 노드임 예:</p>
<pre><code class="language-jsx">// 새 요소 생성
const newElement = document.createElement('div');
newElement.textContent = '새로운 요소';

// 부모 요소 선택
const parentElement = document.getElementById('parent');

// 기준 요소 선택 (이 요소 앞에 새 요소가 삽입됨)
const referenceElement = document.getElementById('existing');

// 새 요소를 기준 요소 앞에 삽입
parentElement.insertBefore(newElement, referenceElement);</code></pre>
<h2 id="기존-문서-객체-삭제">기존 문서 객체 삭제</h2>
<h3 id="removechild">removeChild()</h3>
<p>부모 노드에서 호출, 삭제할 자식 노드를 매개변수로 받음</p>
<pre><code class="language-jsx">// 삭제할 요소 선택
const elementToRemove = document.getElementById('oldElement');

// 부모 요소에서 자식 요소 삭제
elementToRemove.parentNode.removeChild(elementToRemove);</code></pre>
<h3 id="remove-⭐️">remove() ⭐️</h3>
<p>요소 자체에서 직접 호출, 최근에는 더 간단한 <code>remove()</code> 메서드 사용이 일반적</p>
<pre><code class="language-jsx">// 삭제할 요소 선택
const elementToRemove = document.getElementById('oldElement');

// 요소 직접 삭제
elementToRemove.remove();</code></pre>
<h2 id="노드-관계-속성">노드 관계 속성</h2>
<p>DOM 트리 내 노드 간의 관계 탐색 가능</p>
<ul>
<li><strong>parentNode</strong>: 부모 노드</li>
<li><strong>childNodes</strong>: 모든 자식 노드를 NodeList로 반환</li>
<li><strong>firstChild</strong>: 첫 번째 자식 노드</li>
<li><strong>lastChild</strong>: 마지막 자식 노드</li>
<li><strong>nextSibling</strong>: 다음 형제 노드</li>
<li><strong>previousSibling</strong>: 이전 형제 노드</li>
</ul>
<pre><code class="language-jsx">// DOM 노드 관계 속성 예시
const element = document.getElementById('myElement'); // 특정 요소 선택
const parent = element.parentNode; // 부모 노드 가져오기
const firstChild = element.firstChild; // 첫 번째 자식 노드 가져오기
const nextSibling = element.nextSibling; // 다음 형제 노드 가져오기</code></pre>
<p>이 속성들은 DOM 트리를 유연하게 탐색하는 데 매우 유용하며, 문서 구조를 동적으로 변경할 때 활용됨</p>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>