<h2 id="📍-문제">📍 문제</h2>
<p>경화는 과수원에서 귤을 수확했습니다. 경화는 수확한 귤 중 'k'개를 골라 상자 하나에 담아 판매하려고 합니다. 그런데 수확한 귤의 크기가 일정하지 않아 보기에 좋지 않다고 생각한 경화는 귤을 크기별로 분류했을 때 서로 다른 종류의 수를 최소화하고 싶습니다.</p>
<p>예를 들어, 경화가 수확한 귤 8개의 크기가 [1, 3, 2, 5, 4, 5, 2, 3] 이라고 합시다. 경화가 귤 6개를 판매하고 싶다면, 크기가 1, 4인 귤을 제외한 여섯 개의 귤을 상자에 담으면, 귤의 크기의 종류가 2, 3, 5로 총 3가지가 되며 이때가 서로 다른 종류가 최소일 때입니다.</p>
<p>경화가 한 상자에 담으려는 귤의 개수 <code>k</code>와 귤의 크기를 담은 배열 <code>tangerine</code>이 매개변수로 주어집니다. 경화가 귤 k개를 고를 때 크기가 서로 다른 종류의 수의 최솟값을 return 하도록 solution 함수를 작성해주세요.</p>
<hr />
<h3 id="제한사항">제한사항</h3>
<ul>
<li>1 ≤ <code>k</code> ≤ <code>tangerine</code>의 길이 ≤ 100,000</li>
<li>1 ≤ <code>tangerine</code>의 원소 ≤ 10,000,000</li>
</ul>
<hr />
<h3 id="입출력-예">입출력 예</h3>
<table>
<thead>
<tr>
<th>k</th>
<th>tangerine</th>
<th>result</th>
</tr>
</thead>
<tbody><tr>
<td>6</td>
<td>[1, 3, 2, 5, 4, 5, 2, 3]</td>
<td>3</td>
</tr>
<tr>
<td>4</td>
<td>[1, 3, 2, 5, 4, 5, 2, 3]</td>
<td>2</td>
</tr>
<tr>
<td>2</td>
<td>[1, 1, 1, 1, 2, 2, 2, 3]</td>
<td>1</td>
</tr>
</tbody></table>
<hr />
<h3 id="입출력-예-설명">입출력 예 설명</h3>
<p><strong>입출력 예 #1</strong></p>
<ul>
<li>본문에서 설명한 예시입니다.</li>
</ul>
<p><strong>입출력 예 #2</strong></p>
<ul>
<li>경화는 크기가 2인 귤 2개와 3인 귤 2개 또는 2인 귤 2개와 5인 귤 2개 또는 3인 귤 2개와 5인 귤 2개로 귤을 판매할 수 있습니다. 이때의 크기 종류는 2가지로 이 값이 최소가 됩니다.</li>
</ul>
<p><strong>입출력 예 #3</strong></p>
<ul>
<li>경화는 크기가 1인 귤 2개를 판매하거나 2인 귤 2개를 판매할 수 있습니다. 이때의 크기 종류는 1가지로, 이 값이 최소가 됩니다.</li>
</ul>
<h2 id="🥔-내-코드">🥔 내 코드</h2>
<pre><code class="language-jsx">function solution(k, tangerine) {
   let tangerineBox = 0 //귤 담을 바구니 초기화
   let result = 0

    //귤 크기를 분류하는 객체 생성
    const tangerineObj = {}
    tangerine.forEach((v)=&gt;{
      tangerineObj[v] = (tangerineObj[v] || 0) + 1
    })

    //크기별 귤 개수만 내림차순 정렬 배열
    const sortArr = Object.values(tangerineObj).sort((a, b) =&gt; b - a)    

    // 경화가 원하는 수만큼 귤을 담을 때까지
    while(tangerineBox &lt; k){
        tangerineBox += sortArr[0]
        sortArr.shift()
        result ++
    }
   return result
}</code></pre>
<h2 id="✅-풀이-과정">✅ 풀이 과정</h2>
<ol>
<li><strong>귤 객체 생성 및 개수 카운트</strong><ul>
<li>tangerineObj 객체를 생성하여 각 크기별 귤의 개수를 저장</li>
<li>forEach를 사용해 tangerine 배열을 순회하며 각 크기가 나올 때마다 카운트 증가</li>
<li>객체의 키는 귤의 크기, 값은 해당 크기의 귤 개수</li>
</ul>
</li>
<li><strong>크기별 귤 개수 정렬</strong><ul>
<li>Object.values() 객체메서드로 귤 개수만 추출하여 배열 생성</li>
<li>sort()를 사용해 내림차순으로 정렬 (많은 개수부터 선택하기 위함)</li>
</ul>
</li>
<li><strong>필요한 만큼의 귤 선택</strong><ul>
<li>while문을 사용해 tangerineBox(바구니에 담긴 귤 수)가 k(경희가 담으려는 귤 수)보다 작을 때까지 반복</li>
<li>가장 많은 개수의 귤부터 바구니에 담음 (sortArr[0])</li>
<li>담은 귤은 배열에서 제거 (shift())</li>
<li>서로 다른 종류의 수 카운트 (result 증가)</li>
</ul>
</li>
<li><strong>최종 결과 반환</strong><ul>
<li>k개의 귤을 담는데 필요한 최소 종류의 수(result) 반환</li>
</ul>
</li>
</ol>
<h2 id="💡-다른-사람의-코드">💡 다른 사람의 코드</h2>
<pre><code class="language-jsx">
function solution(k, tangerine) {
  let answer = 0;
  const tDict = {};
  tangerine.forEach((t) =&gt; tDict[t] = (tDict[t] || 0) + 1);
  const tArr = Object.values(tDict).sort((a, b) =&gt; b - a);
  for (const t of tArr) {
    answer++;
    if (k &gt; t) k -= t;
    else break;
  }
  return answer;
}</code></pre>
<h2 id="💬-마치며">💬 마치며</h2>
<p>나는 배열 요소를 제거하는 shift() 메서드를 사용했는데, for문과 break를 활용해 조건이 만족되면 반복문을 종료하는 방식도 있다는 것을 알게 되었다</p>