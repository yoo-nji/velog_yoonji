<h1 id="자바스크립트로-구현하는-싱글-페이지-애플리케이션spa">자바스크립트로 구현하는 싱글 페이지 애플리케이션(SPA)</h1>
<h2 id="1-spa">1. SPA</h2>
<p><strong>SPA(Single Page Application):</strong> 초기 로딩 후 페이지 전체를 새로고침하지 않고 동적으로 콘텐츠를 갱신하는 웹 애플리케이션</p>
<p><strong>장점:</strong> 빠른 응답성과 효율적인 네트워크 사용으로 매끄러운 사용자 경험 제공</p>
<p>SPA는 필요한 데이터만 받아와 화면을 갱신하며, 주로 자바스크립트와 <code>history API</code>를 활용하여 구현</p>
<h2 id="2-자바스크립트를-사용한-spa-구현-방법">2. 자바스크립트를 사용한 SPA 구현 방법</h2>
<p>SPA 구현 시 자바스크립트의 <code>history API</code>를 활용하여 브라우저 히스토리 제어 가능</p>
<p><code>history.pushState()</code>와 <code>popstate</code> 이벤트는 사용자의 페이지 이동 시 URL 동적 변경 및 뒤로 가기, 앞으로 가기 기능 구현에 중요한 역할을 함</p>
<h3 id="history-api">History API</h3>
<ul>
<li><code>History API</code>는 브라우저 히스토리 제어를 위한 자바스크립트 기능 제공</li>
<li><code>history.pushState()</code> 메서드로 SPA에서 URL과 상태를 동적 변경. 주소 표시줄은 변경되지만 페이지는 새로고침되지 않아 동적 콘텐츠 갱신과 URL 업데이트를 동시에 처리 가능</li>
<li></li>
</ul>
<p><strong><code>history.pushState(state, title, url)</code> 메서드의 주요 매개변수</strong></p>
<ul>
<li><strong>state</strong>: 새로 저장할 히스토리 상태를 나타내는 객체. <strong>페이지 전환 시 필요한 데이터 포함</strong> 가능</li>
<li><strong>title</strong>: 새 히스토리 항목의 제목. 브라우저에서 무시되어 빈 문자열(””)로 처리됨</li>
<li><strong>url</strong>: 새로운 히스토리 항목의 URL 지정. 상대 경로나 절대 경로를 사용하여 현재 페이지의 URL 변경 가능</li>
</ul>
<h3 id="history-api를-이용한-spa-상태-관리">History API를 이용한 SPA 상태 관리</h3>
<p><code>history.pushState()</code>를 이용해 SPA에서 상태 추가 및 URL 변경 예시:</p>
<pre><code class="language-jsx">// 새 상태를 히스토리에 추가
window.history.pushState({page: 2}, &quot;&quot;, &quot;/page2&quot;);</code></pre>
<h3 id="popstate-이벤트를-통한-상태-복원">Popstate 이벤트를 통한 상태 복원</h3>
<pre><code class="language-jsx">window.addEventListener('popstate', function(event) {
  const page = event.state?.page || 'home';
  updateContent(page);
});

function updateContent(page) {
  document.getElementById('content').innerHTML = pages[page];
}</code></pre>
<p>사용자의 뒤로가기 클릭 시, <code>popstate</code> 이벤트 핸들러에서 <code>event.state</code>를 통해 객체 접근 가능</p>
<p><strong>event.state</strong> </p>
<pre><code class="language-jsx">// 뒤로가기, 앞으로 가기 이벤트 처리
window.addEventListener('popstate', function(event) {
  console.dir(event.state) //{page: 2}
});</code></pre>
<p><code>console.dir(event)</code>로 <code>popstate</code> 이벤트 객체의 상세 정보 확인 가능</p>
<p>객체 내 <code>state</code> 속성은 <code>pushState()</code> 또는 <code>replaceState()</code> 메서드로 전달된 상태 객체임</p>
<p>상태 객체 활용으로 페이지 전환 시 필요 데이터 저장 및 복원 가능, SPA에서 더 풍부한 네비게이션 경험 제공 가능함</p>
<h2 id="3-예제-자바스크립트로-spa-구현하기">3. 예제: 자바스크립트로 SPA 구현하기</h2>
<pre><code class="language-html">&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot; /&gt;
    &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot; /&gt;
    &lt;title&gt;SPA Example&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;ul&gt;
        &lt;li&gt;&lt;a href=&quot;/&quot; data-url=&quot;home&quot;&gt;Home&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href=&quot;/about&quot; data-url=&quot;about&quot;&gt;About&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href=&quot;/contact&quot; data-url=&quot;contact&quot;&gt;Contact&lt;/a&gt;&lt;/li&gt;
    &lt;/ul&gt;
    &lt;div id=&quot;page&quot;&gt;Home 페이지입니다.&lt;/div&gt;
    &lt;script&gt;
        // SPA 페이지 콘텐츠 정의
        const pages = {
            home: &quot;Home 페이지입니다.&quot;,
            about: &quot;About 페이지입니다.&quot;,
            contact: &quot;Contact 페이지입니다. &lt;input text='text' placeholder='연락처 입력 하세요' /&gt;&quot;,
        };

        // 각 링크에 이벤트 핸들러 추가
        const aEls = document.querySelectorAll(&quot;a&quot;);
        aEls.forEach((aEl) =&gt;
            aEl.addEventListener(&quot;click&quot;, function (e) {
                e.preventDefault(); // 링크의 기본 동작 방지
                const page = e.currentTarget.dataset.url; 
                // 클릭한 링크의 페이지 정보 가져오기
                history.pushState({ page: page }, &quot;&quot;, `/${page}`);
                // URL과 상태를 히스토리에 추가
                document.getElementById(&quot;page&quot;).innerHTML = pages[page];
                // 페이지 콘텐츠 업데이트
            })
        );

        // 뒤로가기, 앞으로 가기 이벤트 처리
        window.addEventListener(&quot;popstate&quot;, function (event) {
            const page = event.state?.page || &quot;home&quot;; 
            // 상태가 없으면 기본 페이지로 설정(예외처리)
            document.getElementById(&quot;page&quot;).innerHTML = pages[page];
            // 이전 상태에 맞는 콘텐츠 렌더링
        });
    &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</code></pre>
<h3 id="코드-설명">코드 설명</h3>
<ol>
<li><strong>페이지 콘텐츠 설정</strong>: <code>pages</code> 객체에 페이지별로 표시할 콘텐츠 정의. 각 페이지에 맞는 텍스트나 HTML을 미리 설정하여 링크 클릭 시 <code>innerHTML</code>을 이용해 해당 내용 표시 가능</li>
<li><strong>링크 이벤트 핸들러 설정</strong>: 모든 링크에 <code>click</code> 이벤트 핸들러 추가하여 클릭 시 다음 작업 수행<ul>
<li><code>e.preventDefault()</code>: 페이지 이동을 막고 자바스크립트로 전환 처리</li>
<li><code>e.currentTarget.dataset.url</code>: 클릭한 링크의 <code>data-url</code> 속성에서 페이지 정보 가져옴</li>
<li><code>history.pushState()</code>: URL 변경 및 새로운 상태를 브라우저의 히스토리에 저장</li>
<li><code>document.getElementById(&quot;page&quot;).innerHTML</code>: <code>pages</code> 객체를 이용해 <code>page</code> div의 콘텐츠 업데이트</li>
</ul>
</li>
<li><strong>뒤로가기, 앞으로 가기 이벤트 처리</strong>: <code>popstate</code> 이벤트는 사용자가 브라우저의 뒤로가기나 앞으로가기를 누를 때 발생<ul>
<li><code>event.state</code>: <code>pushState</code>를 통해 저장된 상태 가져옴. 페이지 이동 시 <code>state</code> 객체에 저장된 정보를 활용하여 콘텐츠 복원 가능</li>
<li><code>document.getElementById(&quot;page&quot;).innerHTML</code>: 가져온 <code>state</code>에 따라 <code>page</code> div의 콘텐츠 업데이트</li>
</ul>
</li>
</ol>
<h2 id="4-history-api-메서드">4. History API 메서드</h2>
<ul>
<li><code>history.back()</code>: 현재 URL에서 한 단계 뒤로 이동</li>
<li><code>history.forward()</code>: 현재 URL에서 한 단계 앞으로 이동</li>
<li><code>history.go(n)</code>: <code>n</code>이 양수면 앞으로, 음수면 뒤로 이동. 예: <code>history.go(-2)</code>는 두 단계 뒤로 이동</li>
</ul>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>