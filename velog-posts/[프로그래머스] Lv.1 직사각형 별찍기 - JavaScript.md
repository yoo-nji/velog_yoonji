<h2 id="📍-문제">📍 문제</h2>
<h3 id="문제-설명"><strong>문제 설명</strong></h3>
<p>이 문제에는 표준 입력으로 두 개의 정수 n과 m이 주어집니다.</p>
<p>별(*) 문자를 이용해 가로의 길이가 n, 세로의 길이가 m인 직사각형 형태를 출력해보세요.</p>
<hr />
<h3 id="제한-조건">제한 조건</h3>
<ul>
<li>n과 m은 각각 1000 이하인 자연수입니다.</li>
</ul>
<hr />
<h3 id="예시">예시</h3>
<p>입력</p>
<p><code>5 3</code></p>
<p>출력</p>
<pre><code>*****
*****
*****</code></pre><h2 id="🥔-내-코드">🥔 내 코드</h2>
<pre><code class="language-jsx">process.stdin.setEncoding('utf8');
process.stdin.on('data', data =&gt; {
    const n = data.split(&quot; &quot;);
    const a = Number(n[0]), b = Number(n[1]);

    let rectangle = &quot;&quot;;
    for (let i = 0; i &lt; b; i++) {
        rectangle += &quot;*&quot;.repeat(a) + &quot;\n&quot;; // 가로 길이만큼 별 반복 후 줄바꿈
    }
    console.log(rectangle)
});</code></pre>
<h2 id="✅-풀이-과정">✅ 풀이 과정</h2>
<ol>
<li>rectangle 빈 변수 선언</li>
<li>for문 이용해서 가로 길이 b만큼 반복</li>
<li>세로는 repeat(a)로 반복 후 “\n”으로 줄바꿈</li>
</ol>
<h2 id="💡-다른-사람의-코드">💡 다른 사람의 코드</h2>
<pre><code class="language-jsx">process.stdin.setEncoding('utf8');
process.stdin.on('data', data =&gt; {
    const n = data.split(&quot; &quot;);
    const a = Number(n[0]), b = Number(n[1]);
    console.log((('*').repeat(a)+`\n`).repeat(b))
});</code></pre>
<h2 id="💬-마치며">💬 마치며</h2>
<p>오… repeat() 두 번 사용하는 방법도 있구나</p>