<h2 id="📚-til">📚 TIL</h2>
<p>리액트 Props, Children
컴포넌트 이벤트</p>
<h2 id="📦-패키지-설치-시-참고사항">📦 패키지 설치 시 참고사항</h2>
<h3 id="1-npm과-의존성-관리">1. <strong>npm과 의존성 관리</strong></h3>
<ul>
<li><strong>npm</strong>은 패키지 설치 시 해당 패키지와 <strong>의존성 패키지</strong>를 함께 설치함</li>
<li>의존성 패키지는 설치한 패키지의 정상 작동에 필요한 파일들로 구성됨</li>
<li>새로운 버전 출시 시 의존성 간의 <strong>호환성 문제</strong>로 인한 에러 발생 가능</li>
</ul>
<hr />
<h3 id="2-vite-업데이트600-관련-에러">2. <strong>Vite 업데이트(6.0.0) 관련 에러</strong></h3>
<ul>
<li>최근 <strong>Vite 6.0.0</strong> 버전 출시로 일부 라이브러리 설치 시 에러 발생<ul>
<li>Vite 자체 업데이트로 인해 기존 라이브러리들과의 <strong>호환성 문제</strong>가 원인</li>
</ul>
</li>
</ul>
<hr />
<h3 id="3-해결-방법">3. <strong>해결 방법</strong></h3>
<h3 id="31--legacy-peer-deps-옵션">3.1. <strong><code>-legacy-peer-deps</code> 옵션</strong></h3>
<ul>
<li><p><code>-legacy-peer-deps</code>는 <strong>npm</strong>에서 제공하는 옵션으로, 이전 버전의 의존성 규칙을 무시하고 패키지를 설치할 수 있음</p>
</li>
<li><p>사용법:</p>
<pre><code class="language-bash">  npm i [패키지 이름] --legacy-peer-deps</code></pre>
</li>
<li><p>특징:</p>
<ul>
<li>호환성을 <strong>최대한 유지</strong>하면서 설치를 진행함 (😇 <strong>순한맛 해결책</strong>)</li>
<li><strong>임시방편</strong>이므로, 이후에는 관련 라이브러리들이 최신 버전에 맞게 호환되도록 업데이트하는 것을 권장</li>
</ul>
</li>
</ul>
<h3 id="32--force-옵션">3.2. <strong><code>-force</code> 옵션</strong></h3>
<ul>
<li><p><code>-force</code>는 npm이 <strong>모든 의존성 충돌</strong>을 무시하고 강제로 패키지를 설치함</p>
</li>
<li><p>사용법:</p>
<pre><code class="language-bash">  npm i [패키지 이름] --force</code></pre>
</li>
<li><p>특징:</p>
<ul>
<li>모든 호환성을 무시하고 설치를 강행함 (🔥 <strong>매운맛 해결책</strong>)</li>
<li>예상치 못한 <strong>심각한 오류</strong>가 발생할 수 있어 신중한 사용이 필요함</li>
</ul>
</li>
</ul>
<hr />
<h3 id="4-불필요한-파일-삭제-명령어">4. <strong>불필요한 파일 삭제 명령어</strong></h3>
<h3 id="41-rm--rf-">4.1. <strong><code>rm -rf ./*</code></strong></h3>
<ul>
<li><p>현재 디렉토리의 모든 파일과 하위 디렉토리를 삭제함</p>
</li>
<li><p>사용법:</p>
<pre><code class="language-bash">  rm -rf ./*</code></pre>
</li>
<li><p><strong>주의사항:</strong></p>
<ul>
<li>이 명령어는 <strong>현재 디렉토리 내의 파일만</strong> 삭제하므로 상대적으로 안전함</li>
<li>하지만 사용 시 항상 신중해야 하며, <strong>중요한 파일이 삭제될 수 있으므로 백업 후 사용</strong>을 권장</li>
</ul>
</li>
</ul>
<h3 id="42--rm--rf-">4.2.  rm -rf /*</h3>
<ul>
<li>시스템의 루트 디렉토리(<strong>/</strong>)부터 시작해 <strong>모든 파일과 디렉토리</strong>를 삭제함</li>
<li>⚠️ 절대 사용 금지<h2 id="💬-마치며">💬 마치며</h2>
파일 여러개 왔다갔다 하려니까 중간중간 놓쳤다... 수업 마치고 실습 코드 다시 보니 이해가 됐다.
리액트, 타입스크립트 따로따로 보면 알겠는데 합쳐지니까 더 복잡해 보이는 느낌
그래도 연습문제 풀면서 감이 잡히는 것 같다 
리액트 훅 진짜 걱정됨 😰 유튜브에서 강의 찾아봐도 아리송한 게 안 사라지는데 하다보면 감이 생기겠지 생각 중</li>
</ul>