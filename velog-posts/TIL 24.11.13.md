<h2 id="📚-til">📚 TIL</h2>
<h3 id="프로젝트-진행-시작">프로젝트 진행 시작</h3>
<p>나는 노션 클로닝 프로젝트에서 에디터 부분을 맡았다. 팀원분이 API 모듈을 만들어 주셔서 그걸 이용해 봤는데 코드가 훨씬 깔끔해졌다! 모듈이 요런 거구나 배웠음</p>
<h3 id="기능-구현">기능 구현</h3>
<ol>
<li>삭제 기능 - 에디터 부분에서 휴지통을 눌렀을 때 삭제됨!</li>
</ol>
<pre><code class="language-js">import { request } from &quot;../../api/api.js&quot;;

const deleteBtn = document.querySelector(&quot;.deleteBtn&quot;);

const deletePost = (e) =&gt; {
  e.preventDefault();
  // documentId 받아오기
  const currentUrl = window.location.href;
  const documentId = currentUrl.split(&quot;/&quot;).pop();
  // 해당 id 삭제
  request({ method: &quot;DELETE&quot; }, documentId);
};

deleteBtn.addEventListener(&quot;click&quot;, deletePost);</code></pre>
<ol start="2">
<li>에디터 상단 경로 표시<pre><code class="language-js">import { request } from &quot;../../api/api.js&quot;;
</code></pre>
</li>
</ol>
<p>const breadCrumbCon = document.querySelector(&quot;.breadCrumb&quot;);</p>
<p>// api 데이터
const postData = await request({ method: &quot;GET&quot; });
// console.log(postData);</p>
<p>//data 경로 탐색
function findId(postData, targetId, path = []) {
  for (const post of postData) {
    // 탈출 조건: 현재 데이터의 id가 목표 id와 일치하면 타이틀 반환
    if (post.id === targetId) return [...path, post.title];</p>
<pre><code>// documents 배열 탐색하여 재귀 호출
if (post.documents) {
  const result = findId(post.documents, targetId, [...path, post.title]);
  if (result) return result; // 목표 ID를 찾으면 결과 반환
}</code></pre><p>  }
  return null; // 목표를 찾지 못한 경우
}</p>
<p>//배열값 3개만 가져와서 표시
const pathTitle = () =&gt; {
  const path = findId(postData, 140046);
  if (path.length === 1) { return path; }
  else {
    return path
      .slice(-3)
      .map(v =&gt; {
        return v.length &gt; 7 ? <code>${v.slice(0, 7)}...</code> : v;
      });
  }
};</p>
<p>//dom에 표시
let breadCrumbInner = <code>&lt;ul&gt;</code>;
pathTitle().forEach(title =&gt; {
  breadCrumbInner += <code>&lt;li&gt;&lt;a&gt;${title}&lt;/a&gt;&lt;/li&gt;</code>;
});
breadCrumbInner += <code>&lt;/ul&gt;</code>;</p>
<p>breadCrumbCon.innerHTML = breadCrumbInner;</p>
<pre><code>
경로 / 표시는 어떻게 할까 하다가 css 선택자를 활용했다
```css
.breadCrumb &gt; li:not(:last-child)::after {
  content: &quot; /&quot;;
  margin-left: 9px;
}</code></pre><ol>
<li>게시물 삭제</li>
</ol>
<ul>
<li>deleteBtn 요소에 클릭 이벤트 리스너 추가</li>
<li>deletePost 함수로 현재 URL에서 documentId 추출</li>
<li>추출된 documentId로 DELETE 요청 보내 해당 게시물 삭제</li>
</ul>
<ol start="2">
<li>상단 경로(breadcrumb) 표시</li>
</ol>
<ul>
<li>request 함수로 GET 요청하여 postData 가져옴</li>
<li>findId 함수로 postData를 재귀적 탐색하여 특정 ID의 경로 찾음</li>
<li>pathTitle 함수로 현재 페이지의 경로를 최대 3개까지 가져와 표시</li>
<li>각 경로 항목은 7자 초과 시 말줄임표로 처리</li>
<li>breadCrumbInner에 HTML 형태로 경로 구성하여 화면에 표시</li>
</ul>
<h2 id="💬-마치며">💬 마치며</h2>
<p>종일 프로젝트 진행한 하루^.^ 깃허브를 사용하지 않아서 zip으로 주고받았는데 이게 맞나...? 싶었다. 방금 전에 내가 뭘 수정하고 넘긴 건지도 기억이 안 나는 현상... 깃허브의 소중함을 알게 됐다. 매번 헷갈렸던 재귀함수를 프로젝트에 사용해 볼 수 있어서 좋았다. </p>