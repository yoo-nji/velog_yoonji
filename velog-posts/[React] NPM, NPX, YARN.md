<h2 id="1-npmnode-package-manager">1. NPM(Node Package Manager)</h2>
<p><strong>NPM</strong>은 Node.js와 함께 제공되는 <strong>패키지 관리 도구</strong></p>
<p>Node.js 애플리케이션에서 필요한 패키지 설치, 제거, 업데이트, 실행 등을 간편하게 처리 가능</p>
<h3 id="주요-기능">주요 기능</h3>
<ol>
<li><strong>패키지 설치</strong><ul>
<li>실행 환경에서 필요한 패키지 설치(Dependencies)<ul>
<li><code>npm install &lt;package_name&gt; --save</code> (또는 생략 가능)</li>
</ul>
</li>
<li>개발 환경에서만 필요한 패키지 설치(DevDependencies)<ul>
<li><code>npm install &lt;package_name&gt; --save-dev</code> 또는 <code>-D</code></li>
</ul>
</li>
</ul>
</li>
<li><strong>패키지 제거</strong>: <code>npm uninstall &lt;package_name&gt;</code></li>
<li><strong>패키지 업데이트</strong>: <code>npm update &lt;package_name&gt;</code></li>
<li><strong>패키지 실행</strong>: <code>npm run &lt;script_name&gt;</code></li>
<li><strong>글로벌 패키지 관리</strong><ul>
<li>설치: <code>npm install -g &lt;package_name&gt;</code></li>
<li>제거: <code>npm uninstall -g &lt;package_name&gt;</code></li>
</ul>
</li>
<li><strong>패키지 초기화</strong>: <code>npm init</code>으로 프로젝트 초기화 및 <code>package.json</code> 파일 생성</li>
<li><strong>프로젝트 생성</strong>: <code>npm create &lt;package_name&gt;</code>으로 내부적으로 <code>npx</code>를 사용하여 프로젝트 생성</li>
</ol>
<hr />
<h3 id="dependencies와-devdependencies">Dependencies와 DevDependencies</h3>
<p><code>package.json</code> 파일에서 확인 가능</p>
<ul>
<li><strong>Dependencies</strong>: 애플리케이션 실행 또는 빌드 시 필요한 패키지<ul>
<li>예: React, Express</li>
</ul>
</li>
<li><strong>DevDependencies</strong>: 개발 환경에서만 필요한 패키지<ul>
<li>예: 린터, 테스트 도구</li>
</ul>
</li>
<li>프로젝트 설치 시 이 둘을 구분해서 설치 필요 ⇒ 빌드 시 참조하기 때문</li>
</ul>
<p>✅ but, 최근 빌드 도구의 발전으로 <strong>devDependencies에 설치된 패키지도 필요하다고 판단 시 자동으로 빌드</strong>에 포함
⇒ 하지만 명확한 구분 설치가 좋은 관행</p>
<blockquote>
<p>🤔 <strong>어디에 설치해야 되는지 구분 방법</strong>
<code>공식문서</code>에서 설치 방법 확인
ex) —save-dev, —save</p>
</blockquote>
<hr />
<h3 id="npm-특징">NPM 특징</h3>
<ul>
<li>node.js와 함께 설치</li>
<li>&quot;.npmrc&quot; 파일을 통해 설정 가능</li>
<li>&quot;package-lock.json&quot; 파일을 사용하여 패키지 버전을 고정(건들 ❌)</li>
</ul>
<h2 id="2-npxnode-package-execute">2. NPX(Node Package Execute)</h2>
<p>노드패키지 실행 담당</p>
<p>Node.js 설치 시 함께 제공되며, <strong>일회성 패키지 실행</strong>과 <strong>특정 버전 실행</strong>에 유용</p>
<h3 id="주요-기능-1">주요 기능</h3>
<ol>
<li><strong>일회성 패키지 실행</strong><ul>
<li>패키지가 없으면 설치 후 실행: <code>npx &lt;package_name&gt;</code></li>
<li>패키지가 존재하면 바로 실행</li>
</ul>
</li>
<li><strong>특정 버전 실행</strong><ul>
<li>예: <code>npx &lt;package_name&gt;@&lt;version&gt;</code></li>
</ul>
</li>
</ol>
<hr />
<h3 id="npx의-특징">NPX의 특징</h3>
<ul>
<li><strong>로컬/글로벌 설치 없이 실행 가능</strong>: 임시적으로 패키지를 설치하여 실행</li>
<li><strong>개발 의존성 감소</strong>: 불필요한 글로벌 설치를 줄이고 필요할 때만 패키지를 실행</li>
</ul>
<hr />
<h2 id="3-yarn">3. YARN</h2>
<p><strong>YARN</strong>은 페이스북에서 개발한 <strong>병렬 설치 기반 패키지 매니저</strong>임</p>
<p>npm은 싱글스레드 기반이라 한 번에 한 작업밖에 못해 시간이 오래 걸림</p>
<p><strong>YARN은 더 빠르고 안정적</strong>인 패키지 관리 환경 제공</p>
<h3 id="주요-기능-2">주요 기능</h3>
<ol>
<li><strong>패키지 설치</strong><ul>
<li>로컬: <code>yarn add &lt;package_name&gt;</code></li>
<li>전역: <code>yarn global add &lt;package_name&gt;</code></li>
</ul>
</li>
<li><strong>패키지 제거</strong><ul>
<li>로컬: <code>yarn remove &lt;package_name&gt;</code></li>
<li>전역: <code>yarn global remove &lt;package_name&gt;</code></li>
</ul>
</li>
<li><strong>패키지 업데이트</strong>: <code>yarn upgrade &lt;package_name&gt;</code></li>
<li><strong>패키지 실행</strong>: <code>yarn run &lt;script_name&gt;</code></li>
</ol>
<hr />
<h3 id="yarn의-특징">YARN의 특징</h3>
<ol>
<li><strong>병렬 설치</strong>: 패키지를 병렬로 설치하여 빠른 속도로 처리</li>
<li><strong>오프라인 모드</strong>: 이전 설치 패키지 재다운로드 없이 설치 가능</li>
<li><strong><code>yarn.lock</code> 파일</strong>: 더 확정적인 의존성 관리 지원</li>
</ol>
<h3 id="단점">단점</h3>
<ul>
<li><strong>호환성 이슈</strong>: 일부 NPM 패키지가 YARN에서 미지원 가능</li>
<li>기본적으로 NPM이 더 널리 사용</li>
</ul>
<hr />
<blockquote>
<p>💡프로젝트당 하나의 패키지 매니저만 사용 필요예: NPM 사용 중이면 YARN 혼용 금지</p>
</blockquote>
<h2 id="4-도구별-비교">4. 도구별 비교</h2>
<table>
<thead>
<tr>
<th><strong>기능/특징</strong></th>
<th><strong>NPM</strong></th>
<th><strong>NPX</strong></th>
<th><strong>YARN</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>기본 제공</strong></td>
<td>Node.js 기본 패키지 관리자</td>
<td>NPM에 포함 (v5.2.0 이상)</td>
<td>별도 설치 필요</td>
</tr>
<tr>
<td><strong>패키지 설치 속도</strong></td>
<td>보통</td>
<td>N/A</td>
<td>빠름</td>
</tr>
<tr>
<td><strong>의존성 고정 파일</strong></td>
<td><code>package-lock.json</code></td>
<td>N/A</td>
<td><code>yarn.lock</code></td>
</tr>
<tr>
<td><strong>병렬 설치 지원</strong></td>
<td>아니요</td>
<td>아니요</td>
<td>예</td>
</tr>
<tr>
<td><strong>오프라인 모드</strong></td>
<td>아니요</td>
<td>아니요</td>
<td>예</td>
</tr>
<tr>
<td><strong>패키지 실행</strong></td>
<td><code>npm run &lt;script_name&gt;</code></td>
<td><code>npx &lt;package_name&gt;</code></td>
<td><code>yarn run &lt;script_name&gt;</code></td>
</tr>
<tr>
<td><strong>사용 편의성</strong></td>
<td>보통</td>
<td>간편</td>
<td>높음</td>
</tr>
</tbody></table>
<h2 id="5-패키지-버전-읽는-법">5. 패키지 버전 읽는 법</h2>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/efcf1e24-dc0c-4140-b2d6-9330d0b23cd5/image.png" /></p>
<p>Node.js 패키지는 <strong>버전 관리</strong>를 통해 안정성과 호환성 유지. 버전은 항상 <strong>3자리 숫자</strong>로 표기</p>
<h3 id="버전-번호의-구성">버전 번호의 구성</h3>
<ol>
<li><strong>Major (주 버전)</strong>:<ul>
<li>패키지에 큰 변화가 있을 때 증가</li>
<li>이전 버전과 <strong>호환되지 않을</strong> 가능성이 높음</li>
</ul>
</li>
<li><strong>Minor (부 버전)</strong>:<ul>
<li>새로운 기능 추가</li>
<li>기존 기능과의 호환성 유지 ⇒ 추가된 기능을 쓰지 않는다면 전혀 영향 없음</li>
</ul>
</li>
<li><strong>Patch (패치)</strong>:<ul>
<li>기존 기능의 버그 수정(=많을수록 엉망)</li>
<li>기존 기능과의 호환성 유지</li>
</ul>
</li>
</ol>
<p><strong>예시</strong></p>
<pre><code class="language-scss">1.15.3
|  |  └ Patch (버그 수정)
|  └ Minor (새로운 기능 추가)
└ Major (큰 변화)</code></pre>
<p><strong>옵셔널 태그</strong>: 특정 버전 뒤에 의미를 추가로 부여. 예: <code>1.15.3-beta</code> (베타 버전)</p>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>