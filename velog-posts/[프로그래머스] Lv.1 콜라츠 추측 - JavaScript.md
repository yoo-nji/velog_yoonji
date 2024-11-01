<h2 id="📍-문제">📍 문제</h2>
<p>1937년 Collatz란 사람에 의해 제기된 이 추측은, 주어진 수가 1이 될 때까지 다음 작업을 반복하면, 모든 수를 1로 만들 수 있다는 추측입니다. 작업은 다음과 같습니다.</p>
<p><code>1-1. 입력된 수가 짝수라면 2로 나눕니다. 
1-2. 입력된 수가 홀수라면 3을 곱하고 1을 더합니다. 
2. 결과로 나온 수에 같은 작업을 1이 될 때까지 반복합니다.</code></p>
<p>예를 들어, 주어진 수가 6이라면 6 → 3 → 10 → 5 → 16 → 8 → 4 → 2 → 1 이 되어 총 8번 만에 1이 됩니다. 위 작업을 몇 번이나 반복해야 하는지 반환하는 함수, solution을 완성해 주세요. 단, 주어진 수가 1인 경우에는 0을, 작업을 500번 반복할 때까지 1이 되지 않는다면 –1을 반환해 주세요.</p>
<h3 id="제한-사항">제한 사항</h3>
<ul>
<li>입력된 수, <code>num</code>은 1 이상 8,000,000 미만인 정수입니다.</li>
</ul>
<h3 id="입출력-예">입출력 예</h3>
<table>
<thead>
<tr>
<th>n</th>
<th>result</th>
</tr>
</thead>
<tbody><tr>
<td>6</td>
<td>8</td>
</tr>
<tr>
<td>16</td>
<td>4</td>
</tr>
<tr>
<td>626331</td>
<td>-1</td>
</tr>
</tbody></table>
<h3 id="입출력-예-설명">입출력 예 설명</h3>
<p>입출력 예 #1</p>
<p>문제의 설명과 같습니다.</p>
<p>입출력 예 #2</p>
<p>16 → 8 → 4 → 2 → 1 이 되어 총 4번 만에 1이 됩니다.</p>
<p>입출력 예 #3</p>
<p>626331은 500번을 시도해도 1이 되지 못하므로 -1을 리턴해야 합니다.</p>
<h2 id="🥔-내-코드">🥔 내 코드</h2>
<pre><code class="language-jsx">function solution(num) {
  if (num === 1) return 0;
  else {
    for (let i = 1; i &lt;= 500; i++) {
      num = num % 2 === 0 ? num / 2 : num * 3 + 1;
      if (num === 1) return i;
    } return - 1;
  }
}</code></pre>
<h2 id="✅-풀이-과정">✅ 풀이 과정</h2>
<ol>
<li>if (num === 1) return 0;: 주어진 수가 처음부터 1이라면 바로 0을 반환합니다.</li>
<li>for문: 최대 500번 반복하며, 각 반복에서 수를 짝수/홀수에 따라 처리합니다.<ol>
<li>짝수일 경우: num / 2</li>
<li>홀수일 경우: num * 3 + 1</li>
</ol>
</li>
<li>if (num === 1) return i;: 1이 되면 해당 반복 회수를 반환합니다.</li>
<li>500번 반복해도 1이 되지 않을 경우: -1을 반환합니다.</li>
</ol>
<h2 id="💡-다른-사람의-코드">💡 다른 사람의 코드</h2>
<pre><code class="language-jsx">function solution(num) {
    var count = 0;

    while (count &lt; 500) {
        if (num === 1) {
            return count;
        }
        count ++;
        num = num % 2 === 0 ? num /2 : num *3 +1;
    }

    return -1;
}</code></pre>
<pre><code class="language-jsx">function solution(num) {
    let counter = 0;
    while (num !== 1){
        if(counter++ === 500) return -1;
        num = num%2 ? num*3+1 : num/2;
    }
    return counter;
}</code></pre>
<h2 id="💬-마치며">💬 마치며</h2>
<p>문장을 그대로 코드로 옮기다 보니 지저분해졌는데, 다른 분들의 코드를 보면서 더 깔끔하게 작성할 수 있다는 것을 깨달았다. 여러 번 return을 사용하는 대신 count 변수를 활용해 반복 횟수를 추적하는 방식이 더 명확하고 가독성이 좋다고 생각했다.</p>
<p>그리고 나는 반복문으로 for를 사용했지만, 다른 코드들은 while를 사용했다. 이번 문제처럼 500까지라는 조건이 있다면 while 루프가 더 적합했을 것 같다. 익숙함에 따라 반복문을 선택하는 습관을 버리고, 문제에 맞는 문법을 선택할 수 있도록 연습해야겠다.</p>