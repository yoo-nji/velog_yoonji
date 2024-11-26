<h2 id="현대-프론트엔드-개발의-필수-도구-빌드툴"><strong>현대 프론트엔드 개발의 필수 도구: 빌드툴</strong></h2>
<p><strong><code>빌드툴이란</code></strong> 프론트엔드 개발자들이 코드를 더 쉽고 빠르게 만들기 위해 사용하는 도구</p>
<p><strong>빌드툴 종류</strong></p>
<ul>
<li><strong>트랜스파일러</strong></li>
<li><strong>번들러</strong></li>
<li>등…</li>
</ul>
<h2 id="1-트랜스파일러"><strong>1. 트랜스파일러</strong></h2>
<h3 id="11-바벨babel">1.1. <strong>바벨(Babel)</strong></h3>
<p><strong>바벨이란?</strong></p>
<p>바벨은 <strong>JavaScript 트랜스파일러</strong>로, 최신 문법을 구버전 브라우저에서도 실행 가능하게 변환하는 도구</p>
<p><strong>예시: ES6 → ES5 변환</strong></p>
<pre><code class="language-jsx">// ES6 문법
const greet = () =&gt; console.log('Hello');

// 변환 후 (ES5)
var greet = function () {
    console.log('Hello');
};</code></pre>
<p><strong>바벨의 필요성</strong></p>
<ul>
<li>JavaScript는 매년 새로운 버전이 나오지만 모든 브라우저가 최신 문법을 지원하지는 않음. 특히 <strong>IE(인터넷 익스플로러)와 같은 구버전 브라우저</strong>에서는 최신 문법이 동작하지 않아 변환이 필요함</li>
</ul>
<p><strong>바벨의 장점</strong></p>
<ol>
<li>최신 문법을 사용하여 <strong>가독성과 유지보수성 향상</strong></li>
<li>브라우저 간 <strong>호환성 문제 해결</strong></li>
</ol>
<p><strong>바벨의 한계</strong></p>
<ul>
<li><strong>빌드 속도 저하</strong>: 프로젝트가 커질수록 변환 시간이 증가</li>
<li>대규모 프로젝트에서는 <strong>병목현상 발생 가능</strong></li>
</ul>
<blockquote>
<p><strong>💡 병목현상:</strong> 시스템의 성능이나 처리 속도가 특정 부분에 제한되는 현상</p>
</blockquote>
<h3 id="1-2-swc-speedy-web-compiler"><strong>1-2. SWC (Speedy Web Compiler)</strong></h3>
<p>바벨의 기능을 대체하면서 <strong>Rust</strong> 기반으로 설계되어 훨씬 빠른 성능 보유</p>
<ul>
<li><strong>장점</strong><ol>
<li><strong>최고 속도</strong>: 병렬 처리를 통해 바벨보다 <strong>17배 빠른</strong> 코드 변환</li>
<li><strong>Next.js 기본 채택</strong>: 최신 프레임워크에서 널리 사용 중</li>
<li><strong>바벨과 호환 가능</strong>: 기존 설정을 쉽게 전환 가능</li>
</ol>
</li>
</ul>
<hr />
<h2 id="2-번들러">2. 번들러</h2>
<h3 id="2-1-웹팩webpack"><strong>2-1. 웹팩(Webpack)</strong></h3>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/83eaa09b-894b-4d3d-bd65-ac022efa2ffa/image.png" /></p>
<p>웹팩 공홈</p>
<p><strong>웹팩이란?</strong></p>
<p>웹팩은 <strong>모듈 번들러</strong>로, 다양한 파일과 리소스를 하나의 파일로 묶어주는 도구임</p>
<blockquote>
<p><strong>💡 번들링</strong>: 여러 개의 파일(CSS, JavaScript, 이미지 등)을 하나로 묶거나 적절한 크기로 나누어 배포하는 과정</p>
</blockquote>
<p><strong>왜 번들링이 필요한가?</strong></p>
<ul>
<li>웹 애플리케이션은 CSS, 이미지, 폰트, 아이콘 등 다양한 리소스로 구성됨</li>
<li><strong>각 파일마다 서버 요청이 필요</strong>해서 <strong>네트워크 지연</strong> 발생</li>
<li>웹팩은 파일들을 하나로 묶어 요청을 최소화하고 성능을 개선함</li>
</ul>
<p><strong>웹팩 동작 방식</strong></p>
<ul>
<li>개발 서버에서 코드를 수정할 때<ol>
<li><strong>전체 번들링을 다시 실행</strong></li>
<li>수정된 파일뿐만 아니라 프로젝트 전체를 번들링</li>
<li>변경 사항을 브라우저에 반영하기 위해 <strong>전체 페이지를 새로고침</strong></li>
</ol>
</li>
</ul>
<p><strong>단점</strong></p>
<ul>
<li>번들링 과정이 오래 걸려서, <strong>큰 프로젝트에서는 개발 중 지연 시간이 길어짐</strong></li>
<li>변경된 코드가 적더라도 전체를 다시 번들링해야 하므로 <strong>비효율적</strong></li>
</ul>
<h3 id="2-2-vite"><strong>2-2. Vite</strong></h3>
<p>Vite는 <strong>빠르고 효율적인 개발 환경</strong>을 제공하는 도구로, 기존 웹팩의 한계를 극복하고자 설계됨</p>
<p><strong>특징: 번들링 없는 개발 서버</strong></p>
<ol>
<li><strong>브라우저의 ESM(ES Modules) 활용</strong><ul>
<li>Vite는 브라우저가 JavaScript 파일을 직접 가져올 수 있는 <strong>ES Modules</strong> 방식을 사용함</li>
<li>브라우저가 필요한 파일만 서버에 요청하므로, 번들링 없이 빠르게 실행됨</li>
</ul>
</li>
<li><strong>HMR(Hot Module Replacement)</strong><ul>
<li>코드가 수정되면 수정된 파일만 브라우저에 전달하여 <strong>실시간 업데이트</strong> 가능</li>
<li>전체 페이지를 새로고침하지 않아 더 빠른 개발 경험 제공</li>
</ul>
</li>
</ol>
<h3 id="vite와-webpack의-차이"><strong>Vite와 Webpack의 차이</strong></h3>
<table>
<thead>
<tr>
<th><strong>특징</strong></th>
<th><strong>Webpack</strong></th>
<th><strong>Vite</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>ESM 처리 방식</strong></td>
<td>번들링 과정에서 ESM을 하나의 파일로 묶음</td>
<td>브라우저가 ESM 파일을 직접 로드</td>
</tr>
<tr>
<td><strong>번들링</strong></td>
<td>개발 단계에서도 번들링 필요</td>
<td>개발 단계에서는 번들링 없이 ESM으로 동작</td>
</tr>
<tr>
<td><strong>HMR(실시간 반영)</strong></td>
<td>수정된 파일만 번들링 후 브라우저에 전달</td>
<td>수정된 파일만 즉시 브라우저에 전달</td>
</tr>
<tr>
<td><strong>개발 속도</strong></td>
<td>번들링 과정 때문에 큰 프로젝트에서는 느릴 수 있음</td>
<td>번들링이 없어서 매우 빠름</td>
</tr>
</tbody></table>