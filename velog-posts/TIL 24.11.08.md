<h2 id="📚-til">📚 TIL</h2>
<p><a href="https://velog.io/@yoon_ji/JavaScript-SPA">SPA</a>
NodeJS(포스팅예정)</p>
<h2 id="💡-추가-학습-내용">💡 추가 학습 내용</h2>
<p>폼에서 이벤트 리스너를 폼의 제출(submit) 이벤트에 연결하는 것이 좋음. 이렇게 하면 사용자가 엔터 키를 눌러도 폼을 제출할 수 있어 편리함.</p>
<pre><code class="language-jsx">&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
  &lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot; /&gt;
    &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot; /&gt;
    &lt;title&gt;Document&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;form id=&quot;myForm&quot;&gt;
      &lt;input
        type=&quot;text&quot;
        name=&quot;name&quot;
        placeholder=&quot;이름 입력&quot;
        autocomplete=&quot;off&quot;
      /&gt;
      &lt;button type=&quot;submit&quot;&gt;제출&lt;/button&gt;
    &lt;/form&gt;
    &lt;script&gt;
      document
        .getElementById(&quot;myForm&quot;)
        .addEventListener(&quot;submit&quot;, function (e) {
          e.preventDefault();
          const value = e.currentTarget.firstElementChild.value;
          alert(`폼이 제출되었습니다! 입력한 이름 ${value}`);
        });
    &lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;</code></pre>
<h2 id="💬-마치며">💬 마치며</h2>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/0ccf3bf2-7634-4d0a-b041-985e47c448d7/image.png" />
강사님 가취가욥!(다급) 이라고 속으로만 999번 외친 하루였다.
자바스크립트로 SPA 구현하는 법을 배웠는데, 프레임워크에서 지원하는 거라고 듣기만 했지 바닐라 자바스크립트로 구현하는 건 처음 봐서 신기했다. 이렇게도 할 수 있군 🤔 NodeJS 부분은 순식간에 지나가 버려서 주말 복습이 필요할 것 같다.</p>