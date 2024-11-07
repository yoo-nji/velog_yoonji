<h2 id="📚-til">📚 TIL</h2>
<p>fetch api
async await</p>
<h2 id="💡-추가-학습-내용">💡 추가 학습 내용</h2>
<ul>
<li><p><code>//</code> 주석 이용해서 아래처럼 깔끔하게 줄바꿈 할 수 있다</p>
<p>  <img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/1f237c16-4a51-49e0-8436-2a7102efca9b/image.png" /></p>
</li>
</ul>
<ul>
<li><code>tip</code>: 매개변수를 받아서 그대로 전달하는 경우, 해당 함수를 직접 전달할 수 있다(아래 코드처럼 생략 가능)</li>
</ul>
<pre><code class="language-jsx">  const promise = new Promise((resolve, _) =&gt; {
    setTimeout(() =&gt; {
      resolve(&quot;1번 성공!&quot;);
    }, 2000);
  });

  promise//
    .then((result) =&gt; { console.log(result); });

  //!!tip: 매개변수를 받아서 똑같이 전달하는 용도라면 생략 가능하다
  promise//
    .then(console.log);</code></pre>
<ul>
<li><p>console.time()과 console.timeEnd()를 사용하면 실행 시간을 확인할 수 있음</p>
<ul>
<li><p><strong>console.time()</strong>: 타이머 시작. 측정할 코드 블록 직전에 사용함</p>
</li>
<li><p><strong>console.timeEnd()</strong>: 타이머 종료 및 경과 시간 콘솔 출력. 측정할 코드 블록 직후에 사용함</p>
</li>
<li><p>console.time() 사용 예시:</p>
<pre><code class="language-jsx">  console.time('Loop time');
  for(let i = 0; i &lt; 1000000; i++) {
    // 시간을 측정할 코드
  }
  console.timeEnd('Loop time');
  // 출력: Loop time: 3.716ms</code></pre>
</li>
</ul>
</li>
</ul>
<h2 id="💬-마치며">💬 마치며</h2>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/6915634d-75df-47d1-b8ae-4bb8127d5503/image.jpeg" /></p>
<p>체크리스트를 지우고 지워도 매일 늘어난다... 세균마냥 막 번식함
그래도 해야지 주말 알바를 하고 있어서 체력과 시간 모두 부족한 것 같다 왜 매니저님이 ot 때 알바 비추하셨는지 알 것 같다.</p>
<p>오늘 fatch 이용해서 api 호출해서 데이터를 가공하는 걸 연습했는데 그동안 배운 메서드, 프로미스 개념이 도움이 된 것 같다!
async await 예제로 강사님께서 팀원들과 풀이해 보라는 미션을 주셨는데, 분명 안다고 생각했는데 설명하려니 말문이 턱 막히고 실수한 것도 많아서 팀원분이 실수를 찾아 주셨다...ㅎ 나 때문에 더 혼란스러워진 건 아닌지 ^.^ 말하는 것도 연습이 필요하다는 걸 요즘 엄청 느끼는 중! 🗯️</p>