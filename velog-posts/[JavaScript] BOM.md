<h2 id="윈도우의-주요-구성-요소">윈도우의 주요 구성 요소</h2>
<p>웹 브라우저의 주요 구성 요소는 필수적인 객체들로 구성. 이들은 브라우저의 기능을 활용하는 데 중요한 역할. 구성 요소들은 크게 <strong>BOM</strong>과 <strong>DOM</strong>으로 구분. 둘 다 <strong>window</strong> 객체와 밀접하게 연관</p>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/dcf1388d-73d6-484a-904b-a6c92e26f55c/image.png" /></p>
<h3 id="1-bom-browser-object-model">1. BOM (Browser Object Model)</h3>
<p>BOM은 브라우저 환경에서 제공하는 여러 객체를 포함하여 웹 페이지와 브라우저 간의 상호작용을 가능하게 함. 이 구성의 핵심은 <strong>window</strong> 객체로, 브라우저 창을 나타내며 다양한 기능에 접근 가능</p>
<ul>
<li><strong>window.location</strong>: 현재 페이지의 URL 정보를 읽거나 변경 가능</li>
<li><strong>window.history</strong>: 브라우저 히스토리 조작 가능</li>
</ul>
<p>⚠️ <strong>window 객체</strong>는 브라우저 전용이므로 HTML 환경에서 실행 필요</p>
<h3 id="2-dom-document-object-model">2. DOM (Document Object Model)</h3>
<p>DOM은 HTML 문서의 구조를 객체로 표현하여 JavaScript로 문서를 동적으로 조작 가능. DOM은 사실 BOM의 일부로 볼 수 있으나, 그 크기와 중요성 때문에 별도로 취급</p>
<blockquote>
<p><strong>사실 DOM도 BOM의 하위집합</strong>이지만, 그 규모가 크기 때문에 BOM과 DOM으로 나누어 구분</p>
</blockquote>
<hr />
<h2 id="window-객체-주요-메서드와-속성">window 객체 주요 메서드와 속성</h2>
<h3 id="1-alert">1. <code>alert()</code></h3>
<ul>
<li><strong>기능</strong>: 간단한 경고 메시지를 표시. 사용자가 확인을 누를 때까지 코드 실행 일시 중지</li>
<li><strong>실무</strong>: 사용자 경험을 위해 주로 커스텀 UI로 대체</li>
</ul>
<pre><code class="language-jsx">alert(&quot;안녕하세요!&quot;); // 경고창 표시</code></pre>
<h3 id="2-settimeout">2. <code>setTimeout()</code></h3>
<ul>
<li><strong>기능</strong>: 지정된 시간 후 함수를 실행</li>
</ul>
<pre><code class="language-jsx">setTimeout(() =&gt; console.log(&quot;3초 후 실행&quot;), 3000);</code></pre>
<h3 id="3-setinterval">3. <code>setInterval()</code></h3>
<ul>
<li><strong>기능</strong>: 지정된 간격으로 함수를 반복 실행. <code>clearInterval()</code>로 중지 가능</li>
</ul>
<pre><code class="language-jsx">let count = 0;
const id = setInterval(() =&gt; {
  console.log(count++);
  if (count &gt; 5) clearInterval(id);
}, 1000);</code></pre>
<h3 id="4-confirm">4. <code>confirm()</code></h3>
<ul>
<li><strong>기능</strong>: 확인/취소 선택지가 있는 대화 상자를 표시. 확인 시 <code>true</code>, 취소 시 <code>false</code>를 반환</li>
</ul>
<pre><code class="language-jsx">const result = confirm(&quot;계속하시겠습니까?&quot;);
console.log(result ? &quot;계속&quot; : &quot;취소&quot;);</code></pre>
<h3 id="5-prompt">5. <code>prompt()</code></h3>
<ul>
<li><strong>기능</strong>: 사용자 입력을 받는 대화 상자. 입력값을 문자열로 반환하며, 취소 시 <code>null</code>을 반환</li>
</ul>
<pre><code class="language-jsx">const name = prompt(&quot;이름을 입력하세요:&quot;);
if (name) console.log(`안녕하세요, ${name}님!`);</code></pre>
<h3 id="6-innerwidth-innerheight">6. <code>innerWidth</code>, <code>innerHeight</code></h3>
<ul>
<li><strong>기능</strong>: 브라우저 창의 뷰포트 크기를 픽셀 단위로 반환</li>
<li><strong>활용</strong>: 반응형 웹 디자인에서 유용하게 사용</li>
</ul>
<pre><code class="language-jsx">console.log(&quot;너비:&quot;, window.innerWidth, &quot;높이:&quot;, window.innerHeight);
window.addEventListener('resize', () =&gt; {
  console.log(&quot;변경된 창 너비:&quot;, window.innerWidth);
});</code></pre>
<h2 id="location-객체">location 객체</h2>
<p><strong>location</strong> 객체는 현재 문서의 URL 정보를 제공하고 조작할 수 있는 중요한 BOM 객체</p>
<h3 id="1-locationhref">1. <code>location.href</code></h3>
<ul>
<li><strong>기능</strong>: 현재 페이지의 전체 URL을 나타냄. 이를 변경하면 해당 URL로 이동</li>
</ul>
<pre><code class="language-jsx">console.log(location.href); // 현재 URL 출력
location.href = &quot;https://www.example.com&quot;; // 페이지 이동</code></pre>
<h3 id="2-locationreload">2. <code>location.reload()</code></h3>
<ul>
<li><strong>기능</strong>: 현재 페이지를 새로고침. <code>true</code>를 전달하면 캐시를 무시하고 서버에서 다시 로드</li>
</ul>
<pre><code class="language-jsx">location.reload(true); // 서버에서 다시 로드</code></pre>
<h3 id="3-locationreplace">3. <code>location.replace()</code></h3>
<ul>
<li><strong>기능</strong>: 히스토리에 추가 없이 페이지를 대체</li>
<li>이 메서드를 사용하면 사용자가 '뒤로 가기' 버튼을 눌러도 이전 페이지로 돌아갈 수 없음. 보안과 작업 완료 후 이전 페이지 접근 방지에 유용</li>
</ul>
<pre><code class="language-jsx">location.replace(&quot;https://www.newsite.com&quot;);</code></pre>
<h3 id="4-locationhostname">4. <code>location.hostname</code></h3>
<ul>
<li><strong>기능</strong>: 현재 URL의 도메인 이름을 반환</li>
</ul>
<pre><code class="language-jsx">console.log(location.hostname);</code></pre>
<h2 id="navigator-객체">navigator 객체</h2>
<p><strong>navigator</strong> 객체는 브라우저와 운영 체제의 정보를 제공</p>
<h3 id="navigatoruseragent"><code>navigator.userAgent</code></h3>
<ul>
<li><strong>기능</strong>: 브라우저 및 운영 체제 정보를 포함한 문자열을 반환</li>
<li><strong>활용</strong>: 웹 서버나 스크립트가 클라이언트의 환경을 파악하는 데 사용됨</li>
</ul>
<pre><code class="language-jsx">console.log(navigator.userAgent);
// 출력예) &quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36&quot;</code></pre>
<h2 id="screen-객체">Screen 객체</h2>
<p><strong>Screen</strong> 객체는 사용자의 화면 정보를 제공. 픽셀 크기, 색상 깊이 등의 정보를 통해 사용자 환경에 맞춘 웹 페이지를 구성할 때 유용</p>
<h3 id="주요-속성">주요 속성</h3>
<ul>
<li><strong>screen.width</strong>, <strong>screen.height</strong>: 전체 화면 크기</li>
<li><strong>screen.availWidth</strong>, <strong>screen.availHeight</strong>: 사용 가능한 화면 크기</li>
<li><strong>screen.colorDepth</strong>, <strong>screen.pixelDepth</strong>: 색상 및 픽셀 깊이</li>
</ul>
<pre><code class="language-jsx">console.log(&quot;화면 너비:&quot;, screen.width, &quot;화면 높이:&quot;, screen.height);</code></pre>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>