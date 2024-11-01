<h2 id="📍-문제">📍 문제</h2>
<p>String형 배열 seoul의 element중 &quot;Kim&quot;의 위치 x를 찾아, &quot;김서방은 x에 있다&quot;는 String을 반환하는 함수, solution을 완성하세요. seoul에 &quot;Kim&quot;은 오직 한 번만 나타나며 잘못된 값이 입력되는 경우는 없습니다.</p>
<h3 id="제한-사항">제한 사항</h3>
<ul>
<li>seoul은 길이 1 이상, 1000 이하인 배열입니다.</li>
<li>seoul의 원소는 길이 1 이상, 20 이하인 문자열입니다.</li>
<li>&quot;Kim&quot;은 반드시 seoul 안에 포함되어 있습니다.</li>
</ul>
<h3 id="입출력-예">입출력 예</h3>
<table>
<thead>
<tr>
<th>seoul</th>
<th>return</th>
</tr>
</thead>
<tbody><tr>
<td>[&quot;Jane&quot;, &quot;Kim&quot;]</td>
<td>&quot;김서방은 1에 있다&quot;</td>
</tr>
</tbody></table>
<h2 id="🥔-내-코드">🥔 내 코드</h2>
<pre><code class="language-jsx">const solution = (seoul) =&gt; {
 let results = &quot;&quot;
 for (let i in seoul) {
     if (seoul[i] === &quot;Kim&quot;) {
        results = `김서방은 ${i}에 있다`;
        break; // Kim을 찾으면 반복문 종료
     } 
 }
 return results;
}</code></pre>
<h2 id="✅-풀이-과정">✅ 풀이 과정</h2>
<p>빈 변수 results를 만들고 for...in을 통해 배열을 순환. 인덱스 값을 사용하기 위해 for...in을 선택했다. 조건문을 이용해 &quot;Kim&quot;을 찾으면 결과 문자열을 생성하고 하고 반복문 종료 마지막으로 results를 반환</p>
<h2 id="💡-다른-사람의-코드">💡 다른 사람의 코드</h2>
<pre><code class="language-jsx">const solution = (arr) =&gt; `김서방은 ${arr.findIndex(s =&gt; s === 'Kim')}에 있다`;</code></pre>