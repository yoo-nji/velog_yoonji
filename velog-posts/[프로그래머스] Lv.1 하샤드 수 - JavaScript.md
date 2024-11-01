<h2 id="📍-문제">📍 문제</h2>
<p>양의 정수 <code>x</code>가 하샤드 수이려면 <code>x</code>의 자릿수의 합으로 <code>x</code>가 나누어져야 합니다. 예를 들어 18의 자릿수 합은 1+8=9이고, 18은 9로 나누어 떨어지므로 18은 하샤드 수입니다. 자연수 <code>x</code>를 입력받아 <code>x</code>가 하샤드 수인지 아닌지 검사하는 함수, solution을 완성해주세요.</p>
<h3 id="제한-조건">제한 조건</h3>
<ul>
<li><code>x</code>는 1 이상, 10000 이하인 정수입니다.</li>
</ul>
<h3 id="입출력-예">입출력 예</h3>
<table>
<thead>
<tr>
<th>x</th>
<th>return</th>
</tr>
</thead>
<tbody><tr>
<td>10</td>
<td>true</td>
</tr>
<tr>
<td>12</td>
<td>true</td>
</tr>
<tr>
<td>11</td>
<td>false</td>
</tr>
<tr>
<td>13</td>
<td>false</td>
</tr>
</tbody></table>
<h3 id="입출력-예-설명">입출력 예 설명</h3>
<p><strong>입출력 예 #1</strong></p>
<p>10의 모든 자릿수의 합은 1입니다. 10은 1로 나누어 떨어지므로 10은 하샤드 수입니다.</p>
<p><strong>입출력 예 #2</strong></p>
<p>12의 모든 자릿수의 합은 3입니다. 12는 3으로 나누어 떨어지므로 12는 하샤드 수입니다.</p>
<p><strong>입출력 예 #3</strong></p>
<p>11의 모든 자릿수의 합은 2입니다. 11은 2로 나누어 떨어지지 않으므로 11는 하샤드 수가 아닙니다.</p>
<p><strong>입출력 예 #4</strong></p>
<p>13의 모든 자릿수의 합은 4입니다. 13은 4로 나누어 떨어지지 않으므로 13은 하샤드 수가 아닙니다.</p>
<h2 id="🥔-내-코드">🥔 내 코드</h2>
<pre><code class="language-jsx">function solution(x) {
 let str = String(x); 
 let sum = 0
  for (let i = 0; i &lt; str.length ; i++){
     sum += Number(str[i])
  } return x % sum === 0
}</code></pre>
<h2 id="✅-풀이-과정">✅ 풀이 과정</h2>
<p>숫자를 문자열로 변환하여 유사 배열 형태로 만든 후 반복문을 돌린다. 그리고 각 자릿수를 다시 숫자로 변환하여 sum에 더한다. 마지막으로 x를 sum으로 나눈 나머지가 0일 때 true를 반환하도록 했다</p>
<h2 id="💡-다른-사람의-코드">💡 다른 사람의 코드</h2>
<pre><code class="language-jsx">function solution(x) {
    let num = x;
    let sum = 0;
    do {
        sum += x%10;
        x = Math.floor(x/10);
    } while (x&gt;0);

    return !(num%sum);
}</code></pre>