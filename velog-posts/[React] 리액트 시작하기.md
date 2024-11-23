<h2 id="1-리액트">1. 리액트</h2>
<p>리액트는 <strong>라이브러리</strong>로 분류되며, 개발 방법의 자율성이 높음. </p>
<p>하지만 시간이 지나면서 프레임워크의 특성을 일부 포함하며 진화</p>
<p><strong>라이브러리 vs 프레임워크 비교</strong></p>
<p><strong><code>라이브러리</code></strong>: 떡볶이 → 떡, 고추장, 오뎅 등등 다 직접 조합해서 만드는 것</p>
<p><strong><code>프레임워크</code></strong>: 밀키트</p>
<h3 id="리액트-역사">리액트 역사</h3>
<ol>
<li>리액트는 Jordan Walke가 개인 사이드 프로젝트로 개발하여 출시</li>
<li>페이스북의 일부 시스템에 리액트를 적용했고, 매우 긍정적인 반응을 획득</li>
<li>이후 오픈소스로 전환되어 누구나 코드를 보고 수정을 제안 가능<ol>
<li>(단, 변경사항은 오픈소스 관리자의 승인 필요)</li>
</ol>
</li>
<li><strong>전자정부프레임워크</strong>에 공식 등록되어, 정부 발주 프로젝트에서 공식적으로 사용 가능</li>
</ol>
<h3 id="리액트의-특징">리액트의 특징</h3>
<ol>
<li><strong>컴포넌트 기반</strong>: UI를 작은 컴포넌트 단위로 나누어 재사용성과 유지보수성을 향상</li>
<li><strong>선언형 프로그래밍</strong>: 상태 변화에 따라 UI를 선언적으로 업데이트</li>
<li><strong>가상 DOM</strong>: DOM 조작을 최소화하여 성능을 최적화</li>
</ol>
<hr />
<h2 id="2-리액트-설치-및-실행">2. 리액트 설치 및 실행</h2>
<h3 id="cra">CRA</h3>
<ul>
<li>CRA(Create React App)는 리액트 애플리케이션을 빠르게 생성하기 위한 도구</li>
</ul>
<p>다만, 최근 유지보수가 중단(가장 최근 업데이트 2022년)되었고, 실무에서는 거의 미사용</p>
<p><strong>설치</strong></p>
<ol>
<li>프로젝트 폴더를 생성한 후 해당 디렉토리로 이동</li>
<li>설치 명령어</li>
</ol>
<pre><code class="language-bash">npx create-react-app .</code></pre>
<ul>
<li><strong>npx</strong>: 최신 버전을 가져와 설치<ul>
<li>npx는 없으면 서버에서 가장 최신 버전을 가져와서 설치하기 때문</li>
</ul>
</li>
<li><strong>.</strong>: 현재 디렉토리에 설치하겠다는 의미</li>
</ul>
<p><strong>실행</strong></p>
<pre><code class="language-bash">npm start</code></pre>
<ul>
<li>브라우저에서 자동으로 <code>localhost:3000</code>에 기본 페이지가 표시</li>
<li><code>npm start</code>는 <code>npm run start</code>의 축약형</li>
</ul>
<hr />
<h3 id="vite-설치-✅">Vite 설치 ✅</h3>
<p><strong>Vite</strong>는 빠르고 가벼운 빌드 도구로, 최신 트렌드를 반영한 개발 환경 제공. SWC를 사용해 더욱 빠른 컴파일 속도 보유</p>
<p><strong>설치</strong></p>
<ol>
<li>프로젝트 폴더 생성 후 해당 디렉토리로 이동</li>
<li>설치 명령어</li>
</ol>
<pre><code class="language-bash">npm create vite@latest .</code></pre>
<p><strong>SWC</strong></p>
<p>설치 시 다음과 같은 프롬프트 표시</p>
<pre><code class="language-bash">❯   JavaScript
    JavaScript + SWC
    TypeScript
    TypeScript + SWC</code></pre>
<p>SWC(Speedy Web Compiler) 옵션 선택 시 Babel보다 빠른 컴파일 속도를 제공하는 프로젝트 생성</p>
<p><strong>SWC란?</strong></p>
<p>국내 개발자가 만든 Rust 기반 컴파일러로, 버셀에서 채용</p>
<p>빠른 성능과 효율적인 코드 최적화가 특징. Vite의 기본 트랜스파일러로 사용</p>
<p>노드모듈 없이 기본 구조만 포함, npm i로 설치 후 프로젝트 시작</p>
<p><strong>실행</strong></p>
<pre><code class="language-bash">npm run dev</code></pre>
<ul>
<li><code>localhost:5173</code>에서 애플리케이션 실행</li>
</ul>
<hr />
<h2 id="3-리액트-문법-jsx">3. 리액트 문법 JSX</h2>
<p>리액트는 <strong>JSX</strong>(JavaScript + XML)라는 독특한 문법을 사용해 HTML과 유사한 방식으로 UI 작성</p>
<h3 id="jsx-규칙">JSX 규칙</h3>
<ol>
<li><strong>하나의 최상위 요소</strong> 반환 필수</li>
<li>태그는 <strong>닫힘</strong> 필수 (e.g., <code>&lt;br /&gt;</code>)</li>
<li>속성명은 <strong>카멜케이스</strong>로 작성 (e.g., <code>className</code>, <code>htmlFor</code>)</li>
<li>주석은 <code>{ /* 주석 내용 */ }</code> 형태로 작성</li>
<li>자바스크립트 예약어 사용 불가 (e.g., <code>for</code> 대신 <code>htmlFor</code>)</li>
</ol>
<p>권장 규칙</p>
<ul>
<li>한 줄 이상의 코드는 소괄호로 묶음</li>
</ul>
<p><strong>JSX 예제</strong></p>
<pre><code class="language-jsx">export default function App() {
  return (
    &lt;div&gt;
      &lt;h1&gt;Hello, React JSX!&lt;/h1&gt;
      &lt;h2&gt;Create Element&lt;/h2&gt;
    &lt;/div&gt;
  );
}</code></pre>
<h3 id="createelement-vs-jsx">createElement vs JSX</h3>
<p>리액트의 두 가지 엘리먼트 생성 방식</p>
<ol>
<li><strong>createElement 방식</strong>: 리액트 초기부터 존재한 순수 JavaScript 기반 방식<ul>
<li>문법이 복잡하고 가독성이 낮음</li>
<li>중첩된 엘리먼트 생성 시 코드가 매우 복잡함</li>
</ul>
</li>
<li><strong>JSX 방식</strong>: HTML과 유사한 문법으로 직관적인 코드 작성<ul>
<li>별도의 환경 설정이 필요했으나, 현재는 대부분의 개발 도구에서 기본 지원</li>
<li>가독성이 좋고 유지보수가 용이함</li>
</ul>
</li>
</ol>
<pre><code class="language-jsx">// createElement 예시

  &lt;div id=&quot;root&quot;&gt;&lt;/div&gt;
// 기본 예제
//createElement(태그명, 속성(객체형태), 콘텐츠)
const element = React.createElement(&quot;h1&quot;, { id: &quot;title&quot; }, &quot;Hello, React!&quot;);
// ReactDOM.render로 화면에 컴포넌트를 렌더링
ReactDOM.render(element, document.getElementById('root'));

// 중첩 예제
//createElement(태그명, 속성(객체형태), 콘텐츠1, 콘텐츠2, 콘텐츠3)
const h1El = React.createElement(&quot;h1&quot;, null, &quot;Hello, React!&quot;);
const h2El = React.createElement(&quot;h2&quot;, null, &quot;Create Element&quot;);
const main = React.createElement(&quot;main&quot;, { id: &quot;main&quot; }, h1El, h2El);
ReactDOM.render(main, document.getElementById('root'));</code></pre>
<h3 id="export-default와-export의-차이"><code>export default</code>와 <code>export</code>의 차이</h3>
<ul>
<li><strong><code>export default</code></strong>: 파일당 하나만 사용 가능하며, 원하는 이름으로 임포트 가능</li>
<li><strong><code>export</code></strong>: 여러 항목을 내보낼 수 있으며, 임포트 시 정확한 이름을 사용해야 함</li>
</ul>
<p><strong>예제</strong></p>
<pre><code class="language-jsx">// 파일1.jsx
export default function Component() {
  return &lt;div&gt;컴포넌트&lt;/div&gt;;
}

// 임포트
import Component from './파일1';

// 파일2.jsx
export function Component1() {
  return &lt;div&gt;컴포넌트1&lt;/div&gt;;
}

export function Component2() {
  return &lt;div&gt;컴포넌트2&lt;/div&gt;;
}

// 임포트
import { Component1, Component2 } from './파일2';
</code></pre>
<h2 id="4-리액트-프로젝트-구조">4. 리액트 프로젝트 구조</h2>
<p>Vite로 생성된 리액트 프로젝트 구조</p>
<pre><code class="language-csharp">my-react-app/
├── node_modules/     # 종속성 모듈들 (건드릴 일 없음)
├── public/           # 정적 파일들 (빌드 도구에 영향을 받지 않는 파일)
│   └── index.html    # 메인 HTML 파일
├── src/              # 소스 코드
│   ├── App.jsx       # 메인 컴포넌트
│   ├── main.jsx      # 진입점
│   ├── index.css     # 전역 스타일
│   └── assets/       # 이미지 및 자원 파일 (public과 달리 빌드 영향을 받음)
├── package.json      # 프로젝트 설정 및 종속성 정보 (중요)
└── vite.config.js    # Vite 설정 파일 (건드릴 일 없음)
└── .gitignore        # Git 무시 파일 목록</code></pre>
<h3 id="파일-정리-팁">파일 정리 팁</h3>
<ol>
<li><p><strong>필요 없는 파일 삭제</strong></p>
<ul>
<li><code>index.css</code>와 <code>App.css</code> 등 사용하지 않는 파일 제거</li>
<li>main.tsx에서 CSS import 구문 제거</li>
<li>에셋폴더 제거</li>
</ul>
</li>
<li><p><strong><code>.gitignore</code> 설정 추가</strong></p>
<ul>
<li><p><code>package-lock.json</code>, <code>.env</code>, <code>node_modules</code> 등 커밋 제외할 파일 추가</p>
</li>
<li><p>일부 예시</p>
<p>```jsx
node_modules
dist
dist-ssr</p>
</li>
<li><p>.local
package-lock.json
.env
```</p>
</li>
</ul>
</li>
</ol>