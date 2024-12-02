<h1 id="1-에셋-폴더">1. <strong>에셋 폴더</strong></h1>
<p><strong>특징</strong></p>
<ul>
<li>빌드 도구가 이미지를 <strong>최적화</strong>하고 관리함</li>
<li>사용하지 않는 이미지는 최종 번들에 포함되지 않는 <strong>트리쉐이킹</strong> 적용</li>
<li>빌드 시 이미지 이름이 해시값이 포함된 새로운 파일명으로 변환</li>
<li><strong>임포트(import)</strong>를 사용하여 이미지 추가</li>
</ul>
<hr />
<h2 id="에셋-폴더-사용법">에셋 폴더 사용법</h2>
<h3 id="1-이미지-임포트-및-렌더링">1) 이미지 임포트 및 렌더링</h3>
<pre><code class="language-tsx">import tree from &quot;./assets/images/tree.jpg&quot;;

export default function App() {
  return (
    &lt;&gt;
      {/* 이미지 렌더링 */}
      &lt;img src={tree} alt=&quot;tree&quot; /&gt;
    &lt;/&gt;
  );
}</code></pre>
<ul>
<li><strong>장점</strong>: 빌드 도구가 경로를 자동으로 관리하고, 이미지 최적화 및 캐싱 처리</li>
<li><strong>결과</strong>: 개발 모드에서 <code>'tree.jpg'</code>였던 경로가 <code>'assets/tree.123abc.jpg'</code>처럼 최적화된 경로로 변경</li>
</ul>
<blockquote>
<p>⚠️ <strong>주의: img src에 직접 경로 입력 시 빌드 후 <code>npm run preview</code> 로 확인시 이미지 깨짐</strong>
<code>&lt;img src=&quot;../src/assets/images/tree.jpg&quot; alt=&quot;&quot; /&gt;</code></p>
<ul>
<li>JSX는 JavaScript로 상대 경로 파싱 불가</li>
<li>해결: <code>import</code>로 이미지 불러옴</li>
</ul>
</blockquote>
<h3 id="✅-빌드와-프리뷰">✅ 빌드와 프리뷰</h3>
<p><code>npm run build</code> 명령어로 프로젝트를 빌드하면 최적화된 배포 파일 생성</p>
<p><code>npm run preview</code> 명령어로 빌드된 파일을 로컬에서 미리 확인 가능</p>
<p><strong>개발 모드와 빌드/프리뷰 모드의 차이</strong></p>
<ul>
<li>개발 모드: <code>index.html</code> 직접 사용</li>
<li>프리뷰 모드: <code>dist</code> 폴더의 최적화된 <code>index.html</code> 사용</li>
<li>프리뷰는 실제 배포 환경과 유사한 조건에서 테스트 가능</li>
</ul>
<hr />
<h3 id="2-백그라운드-이미지로-사용">2) 백그라운드 이미지로 사용</h3>
<pre><code class="language-tsx">&lt;div
  className=&quot;w-60 h-60&quot;
  style={{ backgroundImage: `url(${tree})` }}
&gt;&lt;/div&gt;;</code></pre>
<hr />
<h3 id="4-이미지-관리-파일-생성-💡">4) 이미지 관리 파일 생성 💡</h3>
<blockquote>
<p>🤔 이미지가 100개가 되면 코드가 너무 지저분해지지 않을까?</p>
</blockquote>
<p>이미지 개별 임포트가 번거롭다면 <strong>이미지 관리 파일</strong>로 한 곳에서 관리하여 코드를 깔끔하게 유지할 수 있음</p>
<p><strong>예시: 이미지 관리 파일 생성</strong></p>
<p><code>assets/images/images.ts</code></p>
<pre><code class="language-tsx">import tree from &quot;./tree.jpg&quot;;
import flower from &quot;./flower.jpg&quot;;

export const images = {
  tree,
  flower,
};</code></pre>
<p><strong>사용법</strong></p>
<pre><code class="language-tsx">import { images } from &quot;./assets/images/images&quot;;

export default function App() {
  return (
    &lt;&gt;
      &lt;img src={images.tree} alt=&quot;tree&quot; /&gt;
      &lt;img src={images.flower} alt=&quot;flower&quot; /&gt;
    &lt;/&gt;
  );
}</code></pre>
<hr />
<h1 id="2-퍼블릭-폴더">2. <strong>퍼블릭 폴더</strong></h1>
<p><strong>특징</strong></p>
<ul>
<li>빌드 도구가 <strong>관여하지 않고</strong> 이미지를 있는 그대로 복사함</li>
<li>모든 파일이 최종 번들에 포함되며, <strong>사용하지 않아도 번들 크기에 영향</strong>을 줌</li>
<li>파일 이름이 그대로 유지되며, <strong>절대 경로</strong>로 접근 필요</li>
<li><strong>정적 자산</strong>(예: 파비콘, robots.txt 등) 관리에 적합</li>
</ul>
<hr />
<h2 id="퍼블릭-폴더-사용법">퍼블릭 폴더 사용법</h2>
<h3 id="1-이미지-렌더링">1) 이미지 렌더링</h3>
<pre><code class="language-tsx">export default function App() {
  return (
    &lt;&gt;
      &lt;img src=&quot;/tree_p.jpg&quot; alt=&quot;tree&quot; /&gt;
    &lt;/&gt;
  );
}</code></pre>
<ul>
<li><strong>절대 경로</strong>(<code>/</code>)를 사용해야 이미지가 올바르게 표시됨</li>
<li>빌드 후에도 경로가 변하지 않음</li>
</ul>
<hr />
<h3 id="2-백그라운드-이미지로-사용-1">2) 백그라운드 이미지로 사용</h3>
<pre><code class="language-tsx">&lt;div
  className=&quot;w-60 h-60&quot;
  style={{ backgroundImage: &quot;url('/tree_p.jpg')&quot; }}
&gt;&lt;/div&gt;;
</code></pre>
<hr />
<h2 id="3-에셋-폴더와-퍼블릭-폴더-비교">3. <strong>에셋 폴더와 퍼블릭 폴더 비교</strong></h2>
<table>
<thead>
<tr>
<th><strong>특징</strong></th>
<th><strong>에셋 폴더</strong></th>
<th><strong>퍼블릭 폴더</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>빌드 도구 관리</strong></td>
<td>✅ 빌드 도구가 이미지 최적화 및 경로 관리</td>
<td>❌ 빌드 도구가 관여하지 않음</td>
</tr>
<tr>
<td><strong>최적화</strong></td>
<td>✅ <strong><code>트리쉐이킹</code></strong> 적용</td>
<td>❌ 모든 이미지가 번들에 포함됨</td>
</tr>
<tr>
<td><strong>파일 이름</strong></td>
<td>✅ 해시값 포함 (캐싱 및 버전 관리)</td>
<td>❌ 원본 파일 이름 그대로 유지</td>
</tr>
<tr>
<td><strong>사용 방법</strong></td>
<td><code>import</code>로 이미지 추가</td>
<td>절대 경로(<code>/</code>)로 이미지 추가</td>
</tr>
<tr>
<td><strong>사용 사례</strong></td>
<td>고정된 이미지를 프로젝트 내부에서 관리할 때</td>
<td>파비콘, robots.txt 등 정적 자산 관리</td>
</tr>
</tbody></table>
<hr />
<h2 id="4-css-이미지-사용">4. <strong>CSS 이미지 사용</strong></h2>
<p>CSS 파일에서 이미지를 사용할 때는 경로 작성</p>
<pre><code class="language-css">.bg {
  background-image: url(&quot;../assets/images/tree.jpg&quot;);
}</code></pre>
<blockquote>
<p>출처: <a href="https://www.sucoding.kr">수코딩</a></p>
</blockquote>