<h2 id="📍-문제">📍 문제</h2>
<p>무인도에 갇힌 사람들을 구명보트를 이용하여 구출하려고 합니다. 구명보트는 작아서 한 번에 최대 <strong>2명</strong>씩 밖에 탈 수 없고, 무게 제한도 있습니다.</p>
<p>예를 들어, 사람들의 몸무게가 [70kg, 50kg, 80kg, 50kg]이고 구명보트의 무게 제한이 100kg이라면 2번째 사람과 4번째 사람은 같이 탈 수 있지만 1번째 사람과 3번째 사람의 무게의 합은 150kg이므로 구명보트의 무게 제한을 초과하여 같이 탈 수 없습니다.</p>
<p>구명보트를 최대한 적게 사용하여 모든 사람을 구출하려고 합니다.</p>
<p>사람들의 몸무게를 담은 배열 people과 구명보트의 무게 제한 limit가 매개변수로 주어질 때, 모든 사람을 구출하기 위해 필요한 구명보트 개수의 최솟값을 return 하도록 solution 함수를 작성해주세요.</p>
<h3 id="제한사항">제한사항</h3>
<ul>
<li>무인도에 갇힌 사람은 1명 이상 50,000명 이하입니다.</li>
<li>각 사람의 몸무게는 40kg 이상 240kg 이하입니다.</li>
<li>구명보트의 무게 제한은 40kg 이상 240kg 이하입니다.</li>
<li>구명보트의 무게 제한은 항상 사람들의 몸무게 중 최댓값보다 크게 주어지므로 사람들을 구출할 수 없는 경우는 없습니다.</li>
</ul>
<h3 id="입출력-예">입출력 예</h3>
<table>
<thead>
<tr>
<th>people</th>
<th>limit</th>
<th>return</th>
</tr>
</thead>
<tbody><tr>
<td>[70, 50, 80, 50]</td>
<td>100</td>
<td>3</td>
</tr>
<tr>
<td>[70, 80, 50]</td>
<td>100</td>
<td>3</td>
</tr>
</tbody></table>
<h2 id="🥔-내-코드">🥔 내 코드</h2>
<pre><code class="language-jsx">function solution(people, limit) {
    // 무게 순으로 내림차순 정렬
    const peoples = people.sort((a, b) =&gt; b - a);

    let boat = 0;
    let i = 0; // 가장 무거운 사람
    let j = peoples.length - 1; // 가장 가벼운 사람
    console.log(i, j)

    while (i &lt;= j) {
        if (peoples[i] + peoples[j] &lt;= limit) {
            // 가장 가벼운 사람과 가장 무거운 사람 같이 탑승
            j--;
        }
        // 혼자 탑승
        i++;
        boat++;
    }

    return boat;
}</code></pre>
<h2 id="✅-풀이-과정">✅ 풀이 과정</h2>
<p><strong>1. 배열 정렬</strong></p>
<ul>
<li>사람들의 몸무게 배열을 내림차순으로 정렬(무거운 사람부터 시작)</li>
</ul>
<p><strong>2. 포인터 설정</strong></p>
<ul>
<li>i: 배열의 시작(가장 무거운 사람)부터 시작</li>
<li>j: 배열의 끝(가장 가벼운 사람)부터 시작</li>
</ul>
<ol>
<li><strong>보트 탑승 로직</strong></li>
</ol>
<ul>
<li><strong>반복문</strong> (<code>while (i &lt;= j)</code>):<ul>
<li><code>i</code>와 <code>j</code>가 교차할 때까지, 즉 모든 사람을 처리할 때까지 진행</li>
<li><strong>조건</strong>: <code>i &lt;= j</code>는 가장 무거운 사람의 인덱스 <code>i</code>가 가장 가벼운 사람의 인덱스 <code>j</code>보다 크거나 같을 때를 의미. 즉, 아직 처리되지 않은 사람이 남아 있는 동안 반복문 실행</li>
</ul>
</li>
<li><strong>조건 확인</strong> (<code>if (peoples[i] + peoples[j] &lt;= limit)</code>):<ul>
<li><code>peoples[i]</code>는 가장 무거운 사람의 몸무게, <code>peoples[j]</code>는 가장 가벼운 사람의 몸무게</li>
<li>두 사람의 몸무게 합이 구명보트의 제한 무게를 초과하지 않는지 확인<ul>
<li>제한 무게 초과하지 않을 시 두 사람을 같은 보트에 탑승</li>
<li>이 경우 <code>j--</code>로 가장 가벼운 사람을 보트에 태운 후 다음 가벼운 사람을 지정</li>
</ul>
</li>
<li><strong>제한 무게 초과 시 가장 무거운 사람은 혼자 탑승</strong>. 이 경우 <code>i++</code>로 무거운 사람을 보트에 태운 후 다음 무거운 사람을 지정</li>
</ul>
</li>
<li><strong>보트 사용</strong>:<ul>
<li>무거운 사람을 무조건 한 번은 보트에 태우므로 <code>i++</code> 항상 실행</li>
<li>보트를 사용했으므로 <code>보트</code> 변수에 1 추가</li>
</ul>
</li>
</ul>
<p><strong>5. 결과 반환</strong></p>
<ul>
<li>필요한 최소 보트 개수(boat) 반환</li>
</ul>
<h2 id="💡-다른-사람의-코드">💡 다른 사람의 코드</h2>
<pre><code class="language-jsx">
function solution(people, limit) {
    people.sort(function(a, b){return a-b});
    for(var i=0, j=people.length-1; i &lt; j; j--) {
        if( people[i] + people[j] &lt;= limit ) i++;
    }    
    return people.length-i;
}</code></pre>
<p><strong>풀이</strong></p>
<ul>
<li><strong>내림차순 정렬</strong> - 가장 무거운 사람부터 차례로 태우기 위해 정렬</li>
<li><strong>포인터</strong> <strong>설정</strong><ul>
<li>i: 가장 무거운 사람부터 시작 (앞)</li>
<li>j: 가장 가벼운 사람부터 시작 (뒤)</li>
</ul>
</li>
<li><strong>보트 탑승 로직</strong><ul>
<li>무거운 사람 + 가벼운 사람 ≤ limit: 두 명 함께 탑승 (j--)</li>
<li>limit 초과: 무거운 사람 혼자 탑승</li>
<li>매 경우 i++ 하여 다음 무거운 사람으로 이동</li>
</ul>
</li>
<li><strong>종료 조건</strong> - i가 j보다 커질 때까지 반복 (모든 사람 탑승 완료)</li>
</ul>
<h2 id="💬-마치며">💬 마치며</h2>
<p>기본 for문만 써 왔는데 <strong>for문 활용법</strong>을 새롭게 알게 됐다. for문에서 두 변수를 동시에 선언하고 조건문으로 활용할 생각은 안 해 봤는데 써먹어 봐야지…✏️ </p>
<p>그리고 변수를 따로 선언하지 않고 var로 <strong>호이스팅 처리</strong>한 점과, 보트 변수를 별도로 만들지 않고 전체 사람 수에서 매칭된 가벼운 사람 수를 빼서 결과를 낸 방식도 좀 신기했다.</p>