<p>TypeScript: JavaScript의 슈퍼셋으로, 강력한 타입 안정성과 정적 타입 검사 제공</p>
<p>TypeScript 프로젝트의 초기 설정부터 실행까지의 과정 단계별 설명</p>
<hr />
<h2 id="1-초기-세팅">1. 초기 세팅</h2>
<h3 id="npm-초기화">npm 초기화</h3>
<p>TypeScript 프로젝트 시작을 위한 <code>package.json</code> 파일 생성 방법:</p>
<pre><code class="language-bash">npm init -y</code></pre>
<ul>
<li><code>-y</code> 옵션: 기본 설정으로 <code>package.json</code> 파일 자동 생성</li>
</ul>
<h3 id="전역-nodejs-패키지-확인">전역 Node.js 패키지 확인</h3>
<p>현재 시스템에 전역으로 설치된 Node.js 패키지 확인 명령어:</p>
<pre><code class="language-bash">npm ls -g --depth=0</code></pre>
<h3 id="출력-예시">출력 예시:</h3>
<pre><code class="language-bash">/usr/local/lib
├── corepack@0.29.3
├── n@10.0.0
└── npm@10.8.2</code></pre>
<ul>
<li>전역 설치된 패키지: 시스템 전체에서 사용 가능</li>
<li><strong>Tip</strong>: 전역 설치 최소화 권장, 프로젝트별 로컬 설치 선호</li>
</ul>
<h3 id="전역-패키지-제거">전역 패키지 제거:</h3>
<pre><code class="language-bash">npm uninstall -g [패키지명]</code></pre>
<h3 id="npm-캐시-정리">npm 캐시 정리</h3>
<p>npm 관련 문제 예방을 위한 캐시 검증 및 정리 방법:</p>
<pre><code class="language-bash">npm cache verify</code></pre>
<p>npm 캐시의 무결성 확인 및 필요 시 정리 수행</p>
<h2 id="2-typescript-설치">2. TypeScript 설치</h2>
<p>TypeScript 로컬 설치 명령어:</p>
<pre><code class="language-bash">npm install typescript --save-dev</code></pre>
<ul>
<li><code>--save-dev</code> 옵션: 개발 환경에서만 필요한 패키지 설치</li>
</ul>
<h2 id="3-typescript-초기화">3. TypeScript 초기화</h2>
<p>TypeScript 설정을 위한 <code>tsconfig.json</code> 파일 생성 명령어:</p>
<pre><code class="language-bash">npx tsc --init</code></pre>
<ul>
<li><code>tsconfig.json</code>: TypeScript 컴파일러 옵션 설정 파일</li>
</ul>
<h2 id="4-tsconfigjson-설정">4. tsconfig.json 설정</h2>
<p><code>tsconfig.json</code> 파일 예제(강사님 샘플 코드 일부)
프로젝트 요구사항에 따라 설정 조정 가능</p>
<pre><code class="language-json">{   
    // 엄격한 타입 검사를 활성화합니다.
    // 여러 가지 타입 검사 옵션을 포함하여 더욱 엄격한 타입 체크를 수행합니다.
    &quot;strict&quot;: true,

    // .d.ts 파일의 타입 검사를 건너뜁니다.
    // 이는 컴파일 속도를 높이기 위해 유용합니다.
    &quot;skipLibCheck&quot;: true
  },

  // 컴파일 대상 파일을 지정합니다.
  // 여기서는 `src` 디렉토리 아래의 모든 `.ts` 파일을 포함합니다.
  &quot;include&quot;: [&quot;src/**/*.ts&quot;],

  // 컴파일에서 제외할 파일을 지정합니다.
  // 여기서는 `node_modules` 디렉토리를 제외합니다.
  &quot;exclude&quot;: [&quot;node_modules&quot;]
}</code></pre>
<ul>
<li><code>include</code>: 컴파일 대상 파일 경로 지정.</li>
<li><code>exclude</code>: 컴파일에서 제외할 파일 경로 지정.</li>
</ul>
<h2 id="5-typescript-컴파일">5. TypeScript 컴파일</h2>
<ul>
<li><code>컴파일이란?</code> TypeScript 코드를 브라우저나 Node.js가 이해할 수 있는 JavaScript로 변환하는 과정</li>
</ul>
<p>TypeScript 파일을 JavaScript로 컴파일하기 위한 <code>tsc</code> 명령어 사용. </p>
<p><strong>전제 조건:</strong> <code>src</code> 디렉토리에 TypeScript 파일(<code>.ts</code>)을 먼저 작성해야 함.</p>
<h3 id="단일-파일-컴파일">단일 파일 컴파일</h3>
<pre><code class="language-bash">npx tsc src/index.ts</code></pre>
<blockquote>
<p>💡터미널에서 폴더 경로 찾을 때 <code>tap</code> 키 이용하면 자동완성 됨</p>
</blockquote>
<pre><code class="language-bash">npx tsc src/ 
//여기까지 치고 tap </code></pre>
<h3 id="전체-프로젝트-컴파일">전체 프로젝트 컴파일</h3>
<ul>
<li><code>index.ts</code> 파일을 <code>dist/index.js</code>로 컴파일</li>
<li><code>tsconfig.json</code> 설정에 따라 프로젝트 내 모든 TypeScript 파일 컴파일</li>
</ul>
<pre><code class="language-bash">npx tsc</code></pre>
<hr />
<h2 id="typescript를-브라우저-없이-바로-실행하는-방법">TypeScript를 브라우저 없이 바로 실행하는 방법</h2>
<h3 id="방법-1-typescript-파일을-javascript로-매번-컴파일해서-실행">방법 1: TypeScript 파일을 JavaScript로 매번 컴파일해서 실행</h3>
<p>TypeScript 파일(<code>.ts</code>)을 JavaScript 파일(<code>.js</code>)로 컴파일한 후 브라우저나 Node.js로 실행하는 방법</p>
<ul>
<li><strong>단점</strong>: 매번 컴파일해야 하므로 번거로움</li>
<li><strong>장점</strong>: 브라우저가 아닌 Node.js에서도 JavaScript처럼 동작 확인 가능</li>
</ul>
<pre><code class="language-bash">npx tsc [파일명].ts  # TypeScript 파일을 JavaScript로 컴파일
node [파일명].js     # 컴파일된 JavaScript 파일 실행</code></pre>
<h3 id="방법-2-ts-node와-code-runner-확장으로-typescript-파일을-즉시-실행">방법 2: <code>ts-node</code>와 <code>Code Runner</code> 확장으로 TypeScript 파일을 즉시 실행</h3>
<p><code>Code Runner</code>와 <code>ts-node</code>를 이용해 컴파일 없이 TypeScript 파일을 바로 실행하는 방법</p>
<ol>
<li><p><strong><code>ts-node</code> 설치 및 설정</strong></p>
<ul>
<li><p><code>ts-node</code>는 TypeScript 파일을 즉시 실행할 수 있는 도구. 프로젝트의 <code>devDependencies</code>에 추가</p>
<pre><code class="language-bash">npm install ts-node --save-dev</code></pre>
</li>
<li><p><strong>설치 확인</strong>: <code>npx ts-node -v</code> 실행</p>
</li>
<li><p><code>ts-node</code> 버전이 표시되면 설치 완료. (중간에 <code>y</code>를 입력하라는 메시지가 뜨면 <code>y</code> 입력)</p>
</li>
<li><p><strong>package.json 결과</strong>:</p>
<pre><code class="language-json">  &quot;devDependencies&quot;: {
      &quot;ts-node&quot;: &quot;^10.9.2&quot;,
      &quot;typescript&quot;: &quot;^5.6.3&quot;
  }</code></pre>
</li>
<li><p><code>ts-node</code>와 <code>typescript</code>가 <code>devDependencies</code>에 함께 설치되어야 함</p>
</li>
</ul>
</li>
<li><p><strong>VSCode 설정 (Code Runner 설정)</strong></p>
<ul>
<li><p>VSCode의 설정 파일에 <code>ts-node</code>를 이용해 TypeScript 파일을 바로 실행할 수 있도록 세팅</p>
</li>
<li><p>설정 파일(<code>settings.json</code>)에 다음 코드를 추가:</p>
<pre><code class="language-json">  &quot;code-runner.clearPreviousOutput&quot;: true,
  &quot;code-runner.executorMap&quot;: {
    &quot;typescript&quot;: &quot;node_modules/.bin/ts-node&quot;
  }</code></pre>
</li>
<li><p><strong><code>code-runner.clearPreviousOutput</code>: true</strong> — 실행할 때마다 이전 출력 결과를 지움</p>
</li>
<li><p><strong><code>code-runner.executorMap</code> 설정</strong> — Code Runner가 TypeScript 파일을 실행할 때 <code>ts-node</code>를 사용하도록 설정</p>
</li>
</ul>
</li>
<li><p><strong>TypeScript 파일 실행</strong></p>
<ul>
<li>설정이 완료되면 <code>.ts</code> 파일에서 Code Runner를 실행</li>
<li>컴파일 과정 없이 즉시 결과 확인 가능</li>
</ul>
</li>
</ol>
<h2 id="typescript와-javascript-차이점-비교">TypeScript와 JavaScript 차이점 비교</h2>
<table>
<thead>
<tr>
<th>특성</th>
<th>JavaScript</th>
<th>TypeScript</th>
</tr>
</thead>
<tbody><tr>
<td>언어 유형</td>
<td>동적 언어</td>
<td>정적 언어</td>
</tr>
<tr>
<td>타입 체크</td>
<td>런타임에 수행</td>
<td>컴파일 시 수행</td>
</tr>
<tr>
<td>오류 검출</td>
<td>실행 시 발견</td>
<td>컴파일 시 발견</td>
</tr>
<tr>
<td>타입 지정</td>
<td>선택적, 동적</td>
<td>필수적, 정적</td>
</tr>
<tr>
<td>컴파일 과정</td>
<td>불필요</td>
<td>필요 (TS → JS)</td>
</tr>
<tr>
<td>개발 시 이점</td>
<td>빠른 프로토타이핑</td>
<td>강력한 타입 안정성</td>
</tr>
</tbody></table>
<hr />
<h2 id="요약">요약</h2>
<ul>
<li><strong>TypeScript 초기화</strong>: <code>npm init</code> → <code>npm install typescript</code> → <code>npx tsc --init</code>.</li>
<li><strong>컴파일</strong>: 단일 파일 → <code>npx tsc src/index.ts</code>, 전체 프로젝트 → <code>npx tsc</code>.</li>
<li><strong>실행</strong>: 컴파일 후 실행 → <code>node</code>, 바로 실행 → <code>ts-node</code>.</li>
</ul>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>