<ul>
<li><strong>기본 css</strong><ul>
<li>인라인 스타일</li>
<li>글로벌 스타일</li>
<li>CSS Modules</li>
</ul>
</li>
<li><strong>CSS-in-JS</strong><ul>
<li>Styled-Components</li>
<li>Emotion</li>
<li>Vanilla Extract</li>
</ul>
</li>
<li><strong>Tailwind CSS</strong></li>
</ul>
<blockquote>
<p>💡 인라인+글로벌: 같이 사용되는 경우가 많음(메인 ❌)
<strong>css모듈</strong>, <strong>테일윈드</strong>, <strong>css-in-js</strong>(택1) 메인으로 쓰일 확률이 높음</p>
</blockquote>
<hr />
<h2 id="기본-css-작성-방법">기본 CSS 작성 방법</h2>
<h3 id="인라인-스타일">인라인 스타일</h3>
<p>컴포넌트 내부에서 스타일을 정의하는 방식으로, <strong>객체 형태</strong>와 <strong>카멜케이스 표기법</strong> 사용</p>
<p><strong>예제</strong></p>
<pre><code class="language-jsx">function App() {
  const styles = {
    container: {
      color: 'white',
      padding: '10px',
    },
  };

  return &lt;div style={styles.container}&gt;Hello React!&lt;/div&gt;;
}</code></pre>
<blockquote>
<p>💡이메일 시스템처럼 외부 CSS를 사용할 수 없는 환경에서 필수적 사용
but, 대규모 프로젝트에서는 유지보수가 어려워 잘 사용하지 않음</p>
</blockquote>
<hr />
<h3 id="글로벌-스타일">글로벌 스타일</h3>
<p><strong>외부 CSS 파일</strong>을 만들어 <code>import</code>하여 사용하는 방식</p>
<p>전역으로 스타일이 적용되어 <strong>모든 컴포넌트에 영향을 미침</strong></p>
<p><strong>예제</strong></p>
<pre><code class="language-jsx">// App.css
.container {
  background-color: #f0f0f0;
  padding: 20px;
}

// App.js
import './App.css';

function App() {
  return &lt;div className=&quot;container&quot;&gt;Hello React!&lt;/div&gt;;
}</code></pre>
<blockquote>
<p>💡 <strong>Tip</strong>: globals.css(공통 스타일)와 reset.css(기본 스타일 초기화) 사용하고, index.css에서 관리하는 것이 좋음</p>
</blockquote>
<pre><code class="language-tsx">/* index.css
css의 진입점 */
@import &quot;./globals.css&quot;;
@import &quot;./reset.css&quot;;</code></pre>
<hr />
<h3 id="css-modules">CSS Modules</h3>
<p><strong>특정 컴포넌트에만 스타일을 적용</strong>하고 싶을 때 사용하는 방법으로, 클래스 이름 충돌을 방지</p>
<p>파일 이름은<strong><code>.module.css</code></strong>로 끝나야 하며, 보통 컴포넌트 이름과 동일하게 작성</p>
<p>✅ 반드시 <strong>클래스 이름</strong>으로만 스타일을 작성</p>
<p>⇒ 클래스명으로 안 하면 글로벌시스템처럼 동작</p>
<p><strong>예제</strong></p>
<pre><code class="language-jsx">// Button.module.css
.button {
  background-color: blue;
  color: white;
  padding: 10px 20px;
}

// Button.js
import styles from './Button.module.css';

function Button() {
  return &lt;button className={styles.button}&gt;Click me&lt;/button&gt;;
}</code></pre>
<p><strong>클래스를 여러 개 적용할 때는 템플릿 리터럴 사용</strong></p>
<pre><code class="language-jsx">// 템플릿 리터럴 사용
&lt;button className={`${styles.button} ${styles.primary}`}&gt;</code></pre>
<hr />
<h2 id="조건부-스타일링">조건부 스타일링</h2>
<h3 id="자바스크립트-문법-이용">자바스크립트 문법 이용</h3>
<p>&amp;&amp; 연산자</p>
<pre><code class="language-jsx">function Button({ primary, disabled }) {
  return (
    &lt;button 
      className={`button ${primary &amp;&amp; 'primary'} ${disabled &amp;&amp; 'disabled'}`}
    &gt;
      Click me
    &lt;/button&gt;
  );
}</code></pre>
<p>삼항 연산자</p>
<pre><code class="language-jsx">function Button({ primary, disabled }) {
  return (
    &lt;button 
      className={`button ${primary ? 'primary' : ''} ${disabled ? 'disabled' : ''}`}
    &gt;
      Click me
    &lt;/button&gt;
  );
}</code></pre>
<h3 id="classnames-라이브러리">classNames 라이브러리</h3>
<p><a href="https://www.npmjs.com/package/classnames">npm 사이트</a></p>
<p>classnames는 조건부로 클래스명을 결합할 수 있게 해주는 유틸리티 라이브러리</p>
<p>특히 여러 클래스를 동적으로 적용해야 할 때 유용</p>
<pre><code class="language-jsx">// const classNames = require('classnames'); // Node.js 사용법

// 프론트엔드에서는 import 사용
import classNames from &quot;classnames/bind&quot;;

// cx(classnames extensions)
const cx = classNames.bind(styles);
// classNames의 bind 메서드에 styles 객체를 바인딩하여 cx에 할당
// cx는 전달받은 클래스명들을 하나의 문자열로 조합하여 반환

// 클래스를 여러 개 적용할 때는 콤마로 구분
&lt;h1 className={cx(&quot;title&quot;)}&gt;내 웹사이트&lt;/h1&gt;
// 라이브러리 미사용 시 비교 코드
&lt;h1 className={styles.title}&gt;내 웹사이트&lt;/h1&gt;</code></pre>
<p>decorated 클래스는 isDecorated가 true일 때만 적용</p>
<pre><code class="language-jsx">function Header() {
  const isDecorated = true;

  return (
    &lt;h1 className={cx('title', { decorated: isDecorated })}&gt;
      내 웹사이트
    &lt;/h1&gt;
  );
}</code></pre>
<p><strong>가장 많이 사용되는 패턴</strong></p>
<pre><code class="language-tsx">classNames('foo', 'bar'); // =&gt; 'foo bar'
classNames('foo', { bar: true }); // =&gt; 'foo bar'
classNames({ 'foo-bar': true }); // =&gt; 'foo-bar'
classNames({ 'foo-bar': false }); // =&gt; ''
classNames({ foo: true }, { bar: true }); // =&gt; 'foo bar'
classNames({ foo: true, bar: true }); // =&gt; 'foo bar'</code></pre>
<hr />
<h2 id="스타일링-도구">스타일링 도구</h2>
<h3 id="css-in-js라이브러리">CSS-in-JS(라이브러리)</h3>
<p>CSS 코드를 자바스크립트 파일에서 작성하는 방식으로, 스타일과 컴포넌트를 하나의 파일로 관리 가능</p>
<h3 id="styled-components">Styled-Components</h3>
<p><a href="https://styled-components.com/">공식홈</a></p>
<ul>
<li>스타일을 적용한 컴포넌트를 생성할 수 있는 라이브러리</li>
<li>자바스크립트와 템플릿 리터럴을 사용해 styled 객체로 컴포넌트 생성</li>
<li>일반 문자열로 처리되어 CSS 자동완성 불가능. 이를 해결하기 위한 익스텐션</li>
<li>IE 지원 ❌</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/7cdd5846-b4af-4026-99f0-4dd746adc71e/image.png" /></p>
<p><strong>설치</strong></p>
<pre><code class="language-bash">npm install styled-components</code></pre>
<p><strong>예제</strong></p>
<pre><code class="language-jsx">import styled from &quot;styled-components&quot;;

const Title = styled.h1`
  font-size: 30px;
  color: blue;
`;

function App() {
  return &lt;Title&gt;Hello, styled-components!&lt;/Title&gt;;
}</code></pre>
<blockquote>
<p>💡 CSS-in-JS의 단점
<strong>런타임 CSS 생성</strong>으로 인해 큰 프로젝트에서 초기 로딩이 느려질 수 있음
<strong>태그가 직관적이지 않음</strong> ⇒ 구조 확인이 어려움</p>
</blockquote>
<h3 id="emotion-👩🎤">Emotion 👩‍🎤</h3>
<p><a href="https://emotion.sh/docs/introduction">공식홈</a></p>
<p>Styled-Components와 유사하지만 <strong>IE 지원 ✅</strong> (후발주자 특, 단점보완)</p>
<p><strong>설치</strong></p>
<pre><code class="language-bash">npm i @emotion/css</code></pre>
<p><strong>예제</strong></p>
<pre><code class="language-jsx">import { css } from &quot;@emotion/react&quot;;

function App() {
  return (
    &lt;h1
      css={css`
        font-size: 30px;
        color: purple;
      `}
    &gt;
      Hello, Emotion!
    &lt;/h1&gt;
  );
}</code></pre>
<p>html 구조를 Styled-Components보다 명확하게 알 수 있음</p>
<p><strong>Emotion 전략</strong></p>
<pre><code class="language-tsx">npm i @emotion/styled @emotion/react</code></pre>
<p>이거 공홈에 있는 건데 이거 설치하고</p>
<pre><code class="language-tsx">import styled from &quot;@emotion/styled&quot;;</code></pre>
<p><strong>스타일드 컴포넌트 그대로 이모션에서 사용할 수 있음</strong></p>
<p><strong>Emotion은</strong> 스타일드 컴포넌트 문법도 100% 똑같이 지원함 🤣 (퍼가요~)</p>
<h3 id="vanilla-extract">Vanilla Extract</h3>
<p><a href="https://vanilla-extract.style/">공식 홈</a></p>
<p>셋 중 가장 최신기술</p>
<p><strong>✅ 선주자를 이기는 매력포인트</strong></p>
<ul>
<li>zero-runtime(런타임 비용이 0에 수렴한다는 의미)<ul>
<li>기존 css in js 라이브러리보다 성능향상</li>
</ul>
</li>
<li>타입스크립트 완벽지원</li>
</ul>
<ol>
<li><strong>설치</strong></li>
</ol>
<pre><code class="language-tsx">npm install @vanilla-extract/css</code></pre>
<ol>
<li><strong>비트기반 설치 명령어</strong></li>
</ol>
<pre><code class="language-tsx">npm install --save-dev @vanilla-extract/vite-plugin</code></pre>
<ol>
<li><strong>vanilla라는 폴더 생성</strong></li>
</ol>
<p>그 안에 <code>style.css.ts</code> 타입스크립트 파일 생성</p>
<pre><code class="language-tsx">import { style } from &quot;@vanilla-extract/css&quot;;

export const h1Style = style({
  fontSize: &quot;30px&quot;,
  color: &quot;pink&quot;,
});</code></pre>
<p><a href="https://vanilla-extract.style/documentation/integrations/vite/">여기</a> 설정법대로 vite.config.ts에 적용</p>
<pre><code class="language-tsx">import { defineConfig } from &quot;vite&quot;;
import { vanillaExtractPlugin } from &quot;@vanilla-extract/vite-plugin&quot;;
import react from &quot;@vitejs/plugin-react-swc&quot;;

// https://vite.dev/config/
export default defineConfig({
  plugins: [react(), vanillaExtractPlugin()],
});</code></pre>
<p> <strong>사용</strong></p>
<pre><code class="language-tsx">//App.tsx
import { h1Style } from &quot;./vanilla/style.css&quot;;

export default function App() {
  return (
    &lt;&gt;
      &lt;h1 className={h1Style}&gt;hello, vanilla extract&lt;/h1&gt;
    &lt;/&gt;
  );
}</code></pre>
<hr />
<h2 id="tailwind-css">Tailwind CSS</h2>
<p><a href="https://tailwindcss.com/">공식홈</a></p>
<p>Tailwind는 <strong>유틸리티 퍼스트 방식</strong>을 제공하며, 미리 정의된 클래스를 조합해 스타일 적용</p>
<ul>
<li>유틸리티퍼스트 장점<ul>
<li>코드의 이식성 높음 ⇒ 복사 붙여넣기만 하면 똑같은 ui 구현</li>
<li>퍼블리셔와의 협업 효율성 높음</li>
</ul>
</li>
</ul>
<blockquote>
<p><strong>💡 <code>유틸리티 클래스</code></strong> 하나의 클래스가 하나의 CSS 속성을 담당하는 1:1 관계</p>
</blockquote>
<p>✅ <a href="https://tailwindcss.com/docs/guides/vite">설치 가이드</a> 참고</p>
<ol>
<li><strong>설치</strong></li>
</ol>
<pre><code class="language-bash">npm install -D tailwindcss postcss autoprefixer</code></pre>
<blockquote>
<p>⚠️ CLI 말고 framework Guides에서 vite로 설치 필요</p>
</blockquote>
<ol>
<li>테일윈드 초기화</li>
</ol>
<p>⇒ tailwind.config.js와 postcss.config.js 파일 생성</p>
<pre><code class="language-tsx">npx tailwindcss init -p</code></pre>
<ol>
<li>tailwind.config.js 파일에서 content 부분 수정</li>
</ol>
<pre><code class="language-jsx">/** @type {import('tailwindcss').Config} */
export default {
  content: [
    &quot;./index.html&quot;,
    &quot;./src/**/*.{js,ts,jsx,tsx}&quot;,
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}</code></pre>
<ol>
<li>tailwind.css 파일 생성 후 추가</li>
</ol>
<pre><code class="language-css">@tailwind base;
@tailwind components;
@tailwind utilities;</code></pre>
<ol>
<li>app.tsx</li>
</ol>
<pre><code class="language-tsx">export default function App() {
  return (
    &lt;h1 className=&quot;text-3xl font-bold underline&quot;&gt;
      Hello world!
    &lt;/h1&gt;
  )
}</code></pre>
<blockquote>
<p>⚠️ 테일윈드 스타일 적용 확인 가능
개발 서버 재시작 필요할 수 있음</p>
</blockquote>
<p><strong>예제</strong></p>
<pre><code class="language-jsx">export default function App() {
  return &lt;h1 className=&quot;text-3xl font-bold underline&quot;&gt;Hello, Tailwind!&lt;/h1&gt;;
}</code></pre>
<h3 id="커스텀-설정-tailwindconfigjs"><strong>커스텀 설정 (tailwind.config.js)</strong></h3>
<pre><code class="language-jsx">export default {
  theme: {
    extend: {
      colors: {
        'main': '#ff0000',
      },
      spacing: {
        'big': '5rem',
      }
    }
  }
}</code></pre>
<p><strong>사용 예시</strong></p>
<pre><code class="language-tsx">function App() {
  return (
    &lt;div className=&quot;text-main mt-big&quot;&gt;
      빨간색 글자에 위쪽 마진 5rem
    &lt;/div&gt;
  );
}</code></pre>
<blockquote>
<p>💡 VS Code용 <code>Tailwind IntelliSense</code> 확장 프로그램으로 클래스 자동 완성과 정렬 가능</p>
</blockquote>
<h2 id="테일윈드-추가설정">테일윈드 추가설정</h2>
<h3 id="tailwind-밑줄-없애기">@tailwind 밑줄 없애기</h3>
<p>settings.json에서 아래 설정 추가로 @tailwind 지시자 경고 무시 가능</p>
<pre><code class="language-json">{
  &quot;css.lint.unknownAtRules&quot;: &quot;ignore&quot;
}</code></pre>
<p>VS Code에서 테일윈드의 @tailwind 구문 경고 표시 제거</p>
<h3 id="모바일에서-hover-스타일-막기">모바일에서 hover 스타일 막기</h3>
<p>tailwind.config.js에 아래 설정 추가로 모바일 기기에서 hover 효과 방지 ⇒ 최적화</p>
<pre><code class="language-jsx">/** @type {import('tailwindcss').Config} */
exports = {
  future: {
    hoverOnlyWhenSupported: true,
  },
}</code></pre>
<h3 id="테일윈드-머지패키지">테일윈드 머지패키지</h3>
<p>테일윈드 CSS 클래스를 JS로 효율적으로 병합하는 유틸리티 함수로, 스타일 충돌 시 마지막 스타일 적용</p>
<p>classnames 라이브러리와 유사하나 테일윈드에 최적화된 도구</p>
<p><a href="https://www.npmjs.com/package/tailwind-merge">tailwind-merge 패키지</a></p>
<p><strong>1. twMerge 사용법</strong></p>
<pre><code class="language-tsx">import { twMerge } from &quot;tailwind-merge&quot;;

export default function App() {
  return (
    &lt;&gt;
      {/* 스타일충돌 */}
      {/* &lt;h1 className=&quot;text-3xl underline text-2xl&quot;&gt;App&lt;/h1&gt; */}

      {/* 방법1 */}
      &lt;h1 className={twMerge(`text-3xl underline text-2xl`)}&gt;App&lt;/h1&gt;

      {/* 방법2 */}
      &lt;h1 className={twMerge(&quot;text-3xl&quot;, &quot;underline&quot;, &quot;text-2xl&quot;)}&gt;App&lt;/h1&gt;
    &lt;/&gt;
  );
}</code></pre>
<p><strong>2. twJoin</strong> ❌ 활용도 낮음</p>
<p>조건부 클래스 결합 시 falsy 값 자동 필터링, 여러 클래스 안전한 결합</p>
<pre><code class="language-tsx">import { twJoin } from &quot;tailwind-merge&quot;;

// 조건부로 클래스 적용
const isActive = true;
const className = twJoin(
  &quot;text-lg&quot;,
  isActive &amp;&amp; &quot;bg-blue-500&quot;,
  isActive ? &quot;text-white&quot; : &quot;text-gray-500&quot;
);</code></pre>
<p><strong>머지 vs 조인</strong></p>
<p>머지: 결합, 중복제거</p>
<p>조인: 중복제거</p>
<h3 id="tailwind-forms">tailwind-forms</h3>
<p><a href="https://github.com/tailwindlabs/tailwindcss-forms"><strong>깃허브 링크</strong></a></p>
<p><strong>필요성</strong></p>
<ul>
<li>테일윈드의 css 자동 리셋으로 인해 form 요소 미표시 문제 해결</li>
<li>개념 학습 단계에서 시각적 확인 용이</li>
</ul>
<p><strong>설치</strong></p>
<pre><code class="language-bash">npm install -D @tailwindcss/forms</code></pre>
<p><strong>tailwind.config.js 설정</strong></p>
<pre><code class="language-jsx">module.exports = {
  plugins: [
    require('@tailwindcss/forms'),
  ],
}</code></pre>
<hr />
<h3 id="css-정렬-플러그인">CSS 정렬 플러그인</h3>
<p><a href="https://tailwindcss.com/blog/automatic-class-sorting-with-prettier">공식문서</a></p>
<p><strong>Prettier Tailwind 플러그인</strong>으로 Tailwind 클래스 자동 정렬 가능</p>
<p>테일윈드의 공식 프리티어 플러그인으로, 테일윈드에서 지정한 순서대로 클래스 정렬</p>
<p>설치 순서</p>
<ol>
<li>테일윈드 사용 중인 디렉토리에서 터미널 실행</li>
<li>설치</li>
</ol>
<pre><code class="language-bash">npm install -D prettier prettier-plugin-tailwindcss</code></pre>
<ol>
<li>디렉토리 최상단에 '.prettierrc' 파일 생성 후 내용 작성</li>
</ol>
<p><code>.prettierrc</code> 설정:</p>
<pre><code class="language-json">{
  &quot;plugins&quot;: [&quot;prettier-plugin-tailwindcss&quot;]
}</code></pre>
<ol>
<li>코드 작성 후 저장 시 프리티어 적용되어 클래스 정렬됨</li>
</ol>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>