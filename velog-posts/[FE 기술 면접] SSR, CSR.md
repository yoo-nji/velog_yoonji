<h2 id="1-csrclient-side-rendering이란"><strong>1. CSR(Client-Side Rendering)이란?</strong></h2>
<h3 id="개념"><strong>개념</strong></h3>
<p>브라우저가 서버로부터 <strong>비어있는 뼈대 HTML</strong>을 받아온 후, 필요한 자바스크립트 번들을 다운로드하고 번들을 실행하여 동적으로 컨텐츠를 채우는 렌더링 방식</p>
<h3 id="작동-방식"><strong>작동 방식</strong></h3>
<ol>
<li><strong>브라우저</strong>가 서버에 빈 HTML과 JS 파일 요청</li>
<li>브라우저가 JS 파일을 다운로드하고 실행</li>
<li>실행된 JS가 HTML의 빈 공간을 채우며 화면을 생성</li>
</ol>
<h3 id="장점"><strong>장점</strong></h3>
<ol>
<li><strong>빠른 상호작용</strong> 서버에서 필요한 파일을 초기에 로드받은 후에는 동적으로 빠르게 렌더링이 가능함</li>
<li><strong>서버 부담 감소</strong> 페이지 렌더링 후에는 추가 서버 요청이 필요 없어 서버 부하가 적음</li>
</ol>
<h3 id="단점"><strong>단점</strong></h3>
<ol>
<li><strong>초기 렌더링 속도 느림</strong> 브라우저가 JS 파일을 모두 다운로드하고 실행해야 화면 표시가 가능하여 초기 렌더링이 느림</li>
<li><strong>SEO 취약</strong> JS로 생성된 콘텐츠는 검색 엔진 크롤러가 읽지 못할 가능성이 높음</li>
</ol>
<h2 id="2-ssrserver-side-rendering이란"><strong>2. SSR(Server-Side Rendering)이란?</strong></h2>
<h3 id="개념-1"><strong>개념</strong></h3>
<p>SSR은 <strong>서버에서 HTML 페이지를 완성</strong>한 뒤 클라이언트(브라우저)에 전달하는 렌더링 방식</p>
<h3 id="작동-방식-1"><strong>작동 방식</strong></h3>
<ol>
<li>사용자가 브라우저에서 페이지 요청</li>
<li>서버는 요청에 따라 HTML 페이지 생성</li>
<li>생성된 HTML을 브라우저로 전송</li>
<li>브라우저는 HTML을 즉시 화면에 렌더링</li>
</ol>
<h3 id="장점-1"><strong>장점</strong></h3>
<ol>
<li><strong>빠른 초기 렌더링</strong> 서버에서 완성된 HTML을 제공하여 사용자에게 첫 화면을 빠르게 표시 가능.</li>
</ol>
<blockquote>
<p>💡 SSR은 서버에서 페이지를 구성하는 시간은 CSR보다 더 걸리지만, 브라우저가 JavaScript를 다운로드하고 실행할 필요가 없어 사용자가 실제로 콘텐츠를 보게 되는 시점은 더 빠르다</p>
</blockquote>
<ol>
<li><strong>SEO에 유리</strong> 검색 엔진 크롤러가 HTML을 쉽게 읽을 수 있어, 검색 결과 상위 노출 가능성이 높음</li>
</ol>
<h3 id="단점-1"><strong>단점</strong></h3>
<ol>
<li><strong>서버 부하 증가</strong> 모든 페이지 요청마다 서버가 HTML을 새로 만들어야 하기 때문</li>
<li><strong>복잡한 구현</strong> 서버와 클라이언트 로직의 분리 관리로 인한 개발과 유지보수의 복잡성 증가</li>
</ol>
<p><strong>🤔 Q. CSR은 왜 검색엔진에 불리하고 SSR은 왜 유리한가요?</strong></p>
<p>CSR의 경우, 아래 이미지처럼 초기 HTML이 거의 비어있는 상태(<code>div id=&quot;root&quot;</code>)로 전달되고 JavaScript가 실행된 후에야 실제 콘텐츠가 생성되는데, 대부분의 검색엔진 크롤러는 이 JavaScript 실행을 기다리지 않고 빈 HTML만 읽고 지나가기 때문</p>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/1913fbab-dc19-4646-b054-1993412bd8b5/image.png" /></p>
<p>반면 SSR은 서버에서 이미 모든 콘텐츠가 포함된 완성된 HTML을 제공하므로, 크롤러가 JavaScript 실행 없이도 모든 콘텐츠를 즉시 읽을 수 있어 검색 엔진 최적화에 유리함</p>
<h3 id="3-ssr과-csr-비교"><strong>3. SSR과 CSR 비교</strong></h3>
<table>
<thead>
<tr>
<th><strong>특징</strong></th>
<th><strong>SSR</strong></th>
<th><strong>CSR</strong></th>
</tr>
</thead>
<tbody><tr>
<td>초기 로딩 속도</td>
<td>빠름 (완성된 HTML 제공)</td>
<td>느림 (JS 다운로드 및 실행 필요)</td>
</tr>
<tr>
<td>상호작용 속도</td>
<td>느림 (Hydration 필요)</td>
<td>빠름 (JS 중심 렌더링)</td>
</tr>
<tr>
<td>SEO</td>
<td>유리 (HTML 제공)</td>
<td>불리 (JS 의존)</td>
</tr>
<tr>
<td>서버 리소스</td>
<td>높음 (매 요청마다 HTML 생성)</td>
<td>낮음 (정적 리소스 제공)</td>
</tr>
<tr>
<td>구현 복잡도</td>
<td>복잡 (서버-클라이언트 로직 분리 필요)</td>
<td>상대적으로 단순 (JS 중심)</td>
</tr>
</tbody></table>
<hr />
<h3 id="4-면접-질문과-예상-답변"><strong>4. 면접 질문과 예상 답변</strong></h3>
<p><strong>Q. SSR과 CSR의 주요 차이점은?</strong></p>
<p><strong>A.</strong> SSR은 서버에서 완성된 HTML을 생성하여 제공하고, CSR은 브라우저가 JavaScript로 화면을 동적 생성합니다.</p>
<p>각각의 특징</p>
<ul>
<li><strong>SSR</strong>: 초기 로딩 빠름, SEO 유리, 서버 부하 큼</li>
<li><strong>CSR</strong>: 동적 상호작용 빠름, 서버 부담 적음, SEO 취약</li>
</ul>
<p><strong>Q. 어떤 상황에서 각각을 사용해야 하나요?</strong></p>
<p><strong>SSR 적합</strong></p>
<ul>
<li>블로그, 쇼핑몰 등 검색엔진 최적화가 중요한 서비스</li>
<li>빠른 초기 로딩이 필수인 경우</li>
</ul>
<p><strong>CSR 적합</strong></p>
<ul>
<li>관리자 페이지처럼 상호작용이 많은 서비스</li>
<li>실시간 데이터 업데이트가 잦은 경우</li>
</ul>