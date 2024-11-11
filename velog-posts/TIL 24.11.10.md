<h2 id="📍-문제">📍 문제</h2>
<h3 id="로또-번호-생성기">로또 번호 생성기</h3>
<p>버튼을 클릭하면 1 ~ 45의 랜덤한 숫자가 6개 선택이 되도록 해주세요.</p>
<p>✨ <strong>완성된 화면</strong></p>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/ac1d57bd-99c3-4c2f-b594-a4ed55dbcfeb/image.png" /></p>
<blockquote>
<p>기본 html, css 코드 제공 받음</p>
</blockquote>
<h2 id="🥔-내-코드">🥔 내 코드</h2>
<p>1차 시도 ❌</p>
<p>문제점: 숫자 중복 제거 로직이 빠져있음</p>
<pre><code class="language-jsx">function pickNumber() {
  // console.log(&quot;눌림&quot;);
  const liEls = document.querySelectorAll('#lucky-numbers &gt; li');

  let lottoNumber = () =&gt; Math.floor(Math.random() * 45) + 1;

  liEls.forEach((li) =&gt; {
    li.textContent = `${lottoNumber()}`;
  });
}</code></pre>
<p>2차 시도 ✅</p>
<pre><code class="language-jsx">function pickNumber() {
  // console.log(&quot;눌림&quot;);
  const liEls = document.querySelectorAll('#lucky-numbers &gt; li');

  let randomNumber = () =&gt; Math.floor(Math.random() * 45) + 1;

  const lottoNumber = new Set();
  while (lottoNumber.size &lt; 6) {
    lottoNumber.add(randomNumber());
  }
  const lottoNumberArr = [...lottoNumber];
  // console.log(lottoNumberArr);

  liEls.forEach((li) =&gt; {
    li.textContent = `${lottoNumberArr.pop()}`;
  });
}</code></pre>
<h2 id="✅-풀이-과정">✅ 풀이 과정</h2>
<ol>
<li>DOM 요소 선택: 'querySelectorAll'을 사용하여 로또 번호를 표시할 모든 'li' 요소 선택</li>
<li>랜덤 숫자 생성 함수: 'randomNumber' 화살표 함수로 1부터 45 사이의 랜덤 숫자 생성</li>
<li>중복 없는 숫자 생성: '<code>Set</code>' 객체를 사용하여 중복 없는 6개의 숫자 생성</li>
<li>배열로 변환: 'spread' 연산자를 사용하여 Set을 배열로 변환</li>
<li>번호 할당: 'forEach' 루프를 사용하여 각 'li' 요소에 생성된 번호 할당</li>
<li>'pop' 메서드 사용: 배열의 마지막 요소부터 차례로 가져와 번호 할당</li>
</ol>
<h2 id="💬-마치며">💬 마치며</h2>
<p>생각보다 너무 술술 풀렸는데 중복숫자라는 함정이 있었다. Set 객체 처음 사용해 보는데 앞으로도 유용하게 잘 쓸 듯 싶다!</p>