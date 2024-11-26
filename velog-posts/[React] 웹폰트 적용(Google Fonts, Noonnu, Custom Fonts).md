<h2 id="1-google-fonts-적용하기">1. Google Fonts 적용하기</h2>
<h3 id="1-1-적용-방법">1-1. 적용 방법</h3>
<ol>
<li><a href="https://fonts.google.com/">Google Fonts</a> 사이트 접속</li>
<li>원하는 폰트를 검색하고 선택</li>
<li><strong>&quot;Get font&quot; → &quot;&lt;&gt;Get embed code&quot;</strong>를 복사하여 프로젝트에 추가</li>
</ol>
<hr />
<h3 id="1-2-link-방식">1-2. Link 방식</h3>
<p><strong>HTML 파일의 <code>&lt;head&gt;</code> 태그에 추가</strong></p>
<pre><code class="language-html">&lt;link rel=&quot;preconnect&quot; href=&quot;https://fonts.googleapis.com&quot;&gt;
&lt;link href=&quot;https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&amp;display=swap&quot; rel=&quot;stylesheet&quot;&gt;</code></pre>
<p><strong><code>preconnect</code>란?</strong></p>
<p>HTML이 렌더링되기 전에 특정 URL과 미리 연결하여 리소스 로딩 시간을 단축시키는 기능임</p>
<p><strong>CSS에서 폰트 사용</strong></p>
<p><strong>font-family 속성 사용 예시</strong></p>
<pre><code class="language-css">.custom-text {
  font-family: 'Roboto', sans-serif;
  font-weight: 400;
}

.custom-text-bold {
  font-family: 'Roboto', sans-serif;
  font-weight: 700;
}</code></pre>
<ul>
<li><strong>font-family</strong>: 적용할 폰트를 지정</li>
<li><strong>font-weight</strong>: 폰트의 굵기를 지정 (400: 기본, 700: 굵게)</li>
</ul>
<p>여러 폰트를 콤마(,)로 구분하여 지정하면, 앞의 폰트가 없을 경우 다음 폰트가 적용됨</p>
<hr />
<h3 id="1-3-import-방식">1-3. @import 방식</h3>
<p><strong>CSS 파일의 최상단에 추가</strong></p>
<pre><code class="language-css">@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&amp;display=swap');</code></pre>
<h3 id="link와-import-비교"><strong>Link와 @import 비교</strong></h3>
<ul>
<li><strong>Link 방식</strong>: 병렬로 리소스를 로드하여 <strong>더 빠른 로딩</strong>이 가능함</li>
<li><strong>@import 방식</strong>: CSS 파일이 순차적으로 로드되므로 로딩 속도가 느려질 수 있음</li>
</ul>
<blockquote>
<p>💡 권장: 성능 최적화를 위해 Link 방식을 사용하는 것이 좋음</p>
</blockquote>
<p><strong>css 폰트 사용 link와 동일</strong></p>
<hr />
<h3 id="1-4-swap과-block의-차이">1-4. Swap과 Block의 차이</h3>
<h3 id="swap-속성"><strong>swap</strong> 속성</h3>
<p>폰트 로드 전까지 시스템 폰트를 먼저 표시한 뒤, 로드 완료 시 지정한 폰트로 교체.</p>
<pre><code class="language-css">@import url('https://fonts.googleapis.com/css2?family=Roboto&amp;display=swap');</code></pre>
<h3 id="block-속성"><strong>block</strong> 속성</h3>
<p>폰트 로드 전까지 텍스트를 보이지 않게 한 뒤, 로드 완료 시 표시.</p>
<pre><code class="language-css">@import url('https://fonts.googleapis.com/css2?family=Roboto&amp;display=block');</code></pre>
<hr />
<h2 id="2-눈누-폰트-적용하기">2. 눈누 폰트 적용하기</h2>
<p><strong>눈누 폰트</strong>는 한글 폰트에 특화된 무료 폰트 플랫폼으로, 상업적으로도 이용 가능</p>
<h3 id="적용-방법">적용 방법</h3>
<ol>
<li><a href="https://noonnu.cc/font_page/pick">눈누 폰트</a> 사이트 접속.</li>
<li>원하는 폰트를 선택 후 <strong>WEB</strong> 버튼 클릭.</li>
<li>제공된 <strong>@font-face 코드</strong>를 CSS 파일에 추가.</li>
</ol>
<p><strong>예제:</strong></p>
<pre><code class="language-css">@font-face {
  font-family: 'BagelFatOne-Regular';
  src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_JAMO@1.0/BagelFatOne-Regular.woff2') format('woff2');
  font-weight: normal;
  font-style: normal;
}

.bagelfatone {
  font-family: 'BagelFatOne-Regular';
}</code></pre>
<hr />
<h2 id="3-다운로드-폰트-사용하기">3. 다운로드 폰트 사용하기</h2>
<p>웹 프로젝트에서 폰트 파일을 직접 다운로드하여 사용하는 방법</p>
<h3 id="적용-방법-1">적용 방법</h3>
<ol>
<li>원하는 폰트 파일(.woff, .woff2, .ttf 등) 다운로드</li>
<li>프로젝트 내 <code>fonts</code> 폴더에 저장</li>
<li>CSS 파일에서 <strong>@font-face</strong>로 선언</li>
</ol>
<h3 id="예제">예제:</h3>
<pre><code class="language-css">@font-face {
  font-family: 'CustomFont';
  src: url('../fonts/custom-font.woff2') format('woff2');
  font-weight: normal;
  font-style: normal;
}</code></pre>
<blockquote>
<p>⚠️ 저작권 확인 필수: 폰트를 사용하기 전에 반드시 저작권 범위 확인 필요
✅ 항상 woff2를 먼저 불러오도록 먼저 배치
⇒ woff2를 지원하지 못하는 경우에만 woff를 불러오도록 배치하는 것이 퍼포먼스 향상에 도움</p>
</blockquote>
<hr />
<h3 id="woff와-woff2의-차이">woff와 woff2의 차이</h3>
<p><strong><code>.woff</code> (Web Open Font Format)</strong></p>
<ul>
<li><strong>압축</strong>: zlib 기반.</li>
<li><strong>파일 크기</strong>: <code>.ttf</code>보다 작지만 <code>.woff2</code>보다는 큼.</li>
<li><strong>호환성</strong>: 오래된 브라우저와도 호환 가능.</li>
</ul>
<p><strong><code>.woff2</code> (Web Open Font Format 2)</strong></p>
<ul>
<li><strong>압축</strong>: Brotli 알고리즘 기반.</li>
<li><strong>파일 크기</strong>: <code>.woff</code>보다 20-30% 더 작음.</li>
<li><strong>호환성</strong>: 최신 브라우저에서 지원.</li>
</ul>