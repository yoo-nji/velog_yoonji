<h2 id="📚-til">📚 TIL</h2>
<p>프로젝트 마무리, 발표</p>
<h3 id="💫-트러블슈팅">💫 트러블슈팅</h3>
<p>합치는 과정에서 상단 경로를 표시해 주는 함수가 제대로 작동하지 않는 문제가 있었다.
(해결해 주신 팀원분께 감사합니다 🙇‍♀️)</p>
<pre><code class="language-js">export async function bread(getPostId) {
  // api 데이터
  const postData = await request({ method: &quot;GET&quot; });
  // console.log(postData);

  //data 경로 탐색
  function findId(postData, targetId, path = []) {
    for (const post of postData) {
      // 탈출 조건: 현재 데이터의 id가 목표 id와 일치하면 타이틀 반환
      if (post.id === targetId) return [...path, post.title];

      // documents 배열 탐색하여 재귀 호출
      if (post.documents) {
        const result = findId(post.documents, targetId, [...path, post.title]);
        if (result) return result; // 목표 ID를 찾으면 결과 반환
      }
    }
    return null; // 목표를 찾지 못한 경우
  }

  //배열값 3개만 가져와서 표시
  const pathTitle = (postId) =&gt; {
    const path = findId(postData, postId);
    if (path.length === 1) {
      return path;
    } else {
      return path.slice(-3).map((v) =&gt; {
        //5자 말줄임표로 하기로 했는데 공간이 많이 남아서 7로 했어요!
        return v.length &gt; 7 ? `${v.slice(0, 7)}...` : v;
      });
    }
  };

  return pathTitle(Number(getPostId));
}</code></pre>
<p><code>원인</code> SPA에서 서버에 ID 값을 전달할 때, 문자열 형식(&quot;12345&quot;)으로 보내어 서버에 있는 숫자 형식(12345)과 매칭되지 않아 오류 발생.
<code>해결</code> ID 값을 받아올 때 Number() 함수로 형 변환을 하여 문자열을 숫자로 변환한 뒤 재귀 함수에 넘겨, 서버에 저장된 숫자형 ID와 일치하도록 수정.</p>
<h2 id="💬-마치며">💬 마치며</h2>
<p>프로젝트가 일단 끝났다. 마무리도 각자 작업한 코드를 합치는 과정에서 에러가 많이 났는데 기능적으로 팀에 도움이 되지 못한 것 같아 아쉬웠다. 😵‍💫 
일단 내가 맡은 상단 경로 부분에서 제목이 실시간으로 변경되지 않는 것과 상위 경로를 눌렀을 때 해당 api를 호출하는 것까지 해서 마무리짓고 싶다.
그리고 추가적으로 spa, api 호출 부분도 연습삼아 조금씩 해 봐야지.</p>