<h2 id="📍-문제">📍 문제</h2>
<p>array의 각 element 중 divisor로 나누어 떨어지는 값을 오름차순으로 정렬한 배열을 반환하는 함수, solution을 작성해주세요.</p>
<p>divisor로 나누어 떨어지는 element가 하나도 없다면 배열에 -1을 담아 반환하세요.</p>
<h3 id="제한사항">제한사항</h3>
<ul>
<li>arr은 자연수를 담은 배열입니다.</li>
<li>정수 i, j에 대해 i ≠ j 이면 arr[i] ≠ arr[j] 입니다.</li>
<li>divisor는 자연수입니다.</li>
<li>array는 길이 1 이상인 배열입니다.</li>
</ul>
<h3 id="입출력-예">입출력 예</h3>
<table>
<thead>
<tr>
<th>arr</th>
<th>divisor</th>
<th>return</th>
</tr>
</thead>
<tbody><tr>
<td>[5, 9, 7, 10]</td>
<td>5</td>
<td>[5, 10]</td>
</tr>
<tr>
<td>[2, 36, 1, 3]</td>
<td>1</td>
<td>[1, 2, 3, 36]</td>
</tr>
<tr>
<td>[3,2,6]</td>
<td>10</td>
<td>[-1]</td>
</tr>
</tbody></table>
<h3 id="입출력-예-설명">입출력 예 설명</h3>
<p>입출력 예#1</p>
<p>arr의 원소 중 5로 나누어 떨어지는 원소는 5와 10입니다. 따라서 [5, 10]을 리턴합니다.</p>
<p>입출력 예#2</p>
<p>arr의 모든 원소는 1으로 나누어 떨어집니다. 원소를 오름차순으로 정렬해 [1, 2, 3, 36]을 리턴합니다.</p>
<p>입출력 예#3</p>
<p>3, 2, 6은 10으로 나누어 떨어지지 않습니다. 나누어 떨어지는 원소가 없으므로 [-1]을 리턴합니다.</p>
<h2 id="🥔-내-코드">🥔 내 코드</h2>
<p>1차 </p>
<pre><code class="language-jsx">const solution = (arr, divisor) =&gt; {
  const result = arr.filter((num) =&gt; num % divisor === 0).sort((a, b) =&gt; a - b);
  if (!result[0]) return [-1];
  return result;
};</code></pre>
<p>2차</p>
<pre><code class="language-bash">const solution = (arr, divisor) =&gt; {
    const result = arr.filter((num)=&gt; num % divisor === 0).sort((a, b) =&gt; a - b)
    return result[0] ? result : [- 1]
    }</code></pre>
<h2 id="✅-풀이-과정">✅ 풀이 과정</h2>
<ol>
<li>filter로 조건에 맞는 요소 필터링: arr.filter((num) =&gt; num % divisor === 0)</li>
<li>sort로 배열 오름차순 정렬: sort((a, b) =&gt; a - b)</li>
<li>빈 배열 처리: 삼항 연산자(result[0] ? result : [-1]) 사용</li>
</ol>
<ul>
<li>result[0]이 truthy면 result 반환, falsy면 [-1] 반환</li>
<li>빈 배열의 첫 요소는 undefined로, falsy 값</li>
</ul>
<h2 id="💡-다른-사람의-코드">💡 다른 사람의 코드</h2>
<pre><code class="language-jsx">function solution(arr, divisor) {
    var answer = arr.filter(v =&gt; v%divisor == 0);
    return answer.length == 0 ? [-1] : answer.sort((a,b) =&gt; a-b);
}</code></pre>
<h2 id="💬-마치며">💬 마치며</h2>
<p>1차 방식대로 풀었다가 다른 분의 풀이를 보고 2차 삼항연산자를 이용해서 값을 리턴하도록 했다</p>
<p>삼항연산자 꽤나 유용하게 쓰이는 것 같다</p>