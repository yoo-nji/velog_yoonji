<h2 id="📍-문제">📍 문제</h2>
<p>얀에서는 매년 달리기 경주가 열립니다. 해설진들은 선수들이 자기 바로 앞의 선수를 추월할 때 추월한 선수의 이름을 부릅니다. 예를 들어 1등부터 3등까지 &quot;mumu&quot;, &quot;soe&quot;, &quot;poe&quot; 선수들이 순서대로 달리고 있을 때, 해설진이 &quot;soe&quot;선수를 불렀다면 2등인 &quot;soe&quot; 선수가 1등인 &quot;mumu&quot; 선수를 추월했다는 것입니다. 즉 &quot;soe&quot; 선수가 1등, &quot;mumu&quot; 선수가 2등으로 바뀝니다.</p>
<p>선수들의 이름이 1등부터 현재 등수 순서대로 담긴 문자열 배열 <code>players</code>와 해설진이 부른 이름을 담은 문자열 배열 <code>callings</code>가 매개변수로 주어질 때, 경주가 끝났을 때 선수들의 이름을 1등부터 등수 순서대로 배열에 담아 return 하는 solution 함수를 완성해주세요.</p>
<hr />
<h3 id="제한사항">제한사항</h3>
<ul>
<li>5 ≤ <code>players</code>의 길이 ≤ 50,000<ul>
<li><code>players[i]</code>는 i번째 선수의 이름을 의미합니다.</li>
<li><code>players</code>의 원소들은 알파벳 소문자로만 이루어져 있습니다.</li>
<li><code>players</code>에는 중복된 값이 들어가 있지 않습니다.</li>
<li>3 ≤ <code>players[i]</code>의 길이 ≤ 10</li>
</ul>
</li>
<li>2 ≤ <code>callings</code>의 길이 ≤ 1,000,000<ul>
<li><code>callings</code>는 <code>players</code>의 원소들로만 이루어져 있습니다.</li>
<li>경주 진행중 1등인 선수의 이름은 불리지 않습니다.</li>
</ul>
</li>
</ul>
<hr />
<h3 id="입출력-예">입출력 예</h3>
<table>
<thead>
<tr>
<th>players</th>
<th>callings</th>
<th>result</th>
</tr>
</thead>
<tbody><tr>
<td>[&quot;mumu&quot;, &quot;soe&quot;, &quot;poe&quot;, &quot;kai&quot;, &quot;mine&quot;]</td>
<td>[&quot;kai&quot;, &quot;kai&quot;, &quot;mine&quot;, &quot;mine&quot;]</td>
<td>[&quot;mumu&quot;, &quot;kai&quot;, &quot;mine&quot;, &quot;soe&quot;, &quot;poe&quot;]</td>
</tr>
</tbody></table>
<hr />
<h3 id="입출력-예-설명">입출력 예 설명</h3>
<p>입출력 예 #1</p>
<p>4등인 &quot;kai&quot; 선수가 2번 추월하여 2등이 되고 앞서 3등, 2등인 &quot;poe&quot;, &quot;soe&quot; 선수는 4등, 3등이 됩니다. 5등인 &quot;mine&quot; 선수가 2번 추월하여 4등, 3등인 &quot;poe&quot;, &quot;soe&quot; 선수가 5등, 4등이 되고 경주가 끝납니다. 1등부터 배열에 담으면 [&quot;mumu&quot;, &quot;kai&quot;, &quot;mine&quot;, &quot;soe&quot;, &quot;poe&quot;]이 됩니다.</p>
<h2 id="🥔-내-코드">🥔 내 코드</h2>
<h3 id="첫번째-시도">첫번째 시도</h3>
<p>시간초과 실패 ❌</p>
<p><strong>이유:</strong> 중첩 반복문 사용 ⇒ 시간 복잡도 O(n^2)</p>
<p><strong>풀이:</strong></p>
<ul>
<li>배열 <code>players</code>를 <code>arr</code>로 복사</li>
<li>임시 변수 <code>temp</code> 선언</li>
<li><code>callings</code> 배열을 순회하며 각 호출에 대해:<ul>
<li>호출된 선수 <code>winner</code> 찾기</li>
<li><code>arr</code> 배열을 순회하며 <code>winner</code>의 위치 찾기</li>
<li>찾은 위치에서 앞 선수와 위치 교환</li>
</ul>
</li>
<li>최종 순위가 반영된 <code>arr</code> 반환</li>
</ul>
<pre><code class="language-jsx">function solution(players, callings) {
    let arr = players
    let temp

    for(i = 0; i &lt; callings.length; i++){
        let winner = callings[i]
        for(j = 0; j &lt; arr.length; j++){
            if(winner === arr[j]){
                temp = arr[j - 1]
                arr[j - 1] = arr[j]
                arr[j] = temp
                break;
            }
        }  
    }   return arr

}</code></pre>
<h3 id="두번째-시도">두번째 시도</h3>
<p>시간 초과 실패❌</p>
<p><strong>이유</strong>: forEach 루프와 indexOf 메서드를 사용하여 시간 복잡도를 개선하려 했지만, indexOf 메서드 자체가 O(n) 시간 복잡도를 가지고 있어 여전히 비효율적임</p>
<p><strong>개선점:</strong></p>
<ul>
<li><code>forEach</code> 루프 사용: 중첩 반복문을 제거하여 코드를 간결하게 만듦</li>
<li><code>indexOf</code> 메서드 사용: 선수의 위치를 찾는 데 사용됨</li>
<li>시간 복잡도 개선 시도: 중첩 반복문 제거로 일부 개선됨</li>
<li><strong>여전히 비효율적</strong>: indexOf 메서드가 O(n) 시간 복잡도를 가져 큰 입력 데이터에 대해 비효율적</li>
</ul>
<pre><code class="language-jsx">function solution(players, callings) {
  let temp;
  callings.forEach((call) =&gt; {
    const playersIndex = players.indexOf(call);
    if (playersIndex &gt; 0) {
      temp = players[playersIndex - 1];
      players[playersIndex - 1] = players[playersIndex];
      players[playersIndex] = temp;
      // console.log(players);
    }
  });
  return players ;
}</code></pre>
<h3 id="세번째-시도">세번째 시도</h3>
<p>성공 🎉</p>
<ul>
<li>객체를 사용하여 선수의 위치를 O(1) 시간에 조회</li>
<li>배열 검색 대신 인덱스 접근으로 시간 복잡도 개선</li>
</ul>
<pre><code class="language-jsx">function solution(players, callings) {
  // 선수의 이름을 키로 하고 위치를 값으로 가지는 객체 생성
  const positions = {};
  players.forEach((player, index) =&gt; {
    positions[player] = index;
  });

  // 각 호출에 대해 선수 위치 교환
  callings.forEach((call) =&gt; {
    const currentIndex = positions[call]; // 현재 호출된 선수의 위치
    if (currentIndex &gt; 0) { // 맨 앞에 있는 선수가 아닌 경우만 교환 수행
      const prevPlayer = players[currentIndex - 1];

      // 선수 배열에서 위치 교환
      players[currentIndex - 1] = call;
      players[currentIndex] = prevPlayer;

      // 위치 객체에서도 위치 업데이트
      positions[call] = currentIndex - 1;
      positions[prevPlayer] = currentIndex;
    }
  });

  return players;
}</code></pre>
<h2 id="✅-풀이-과정">✅ 풀이 과정</h2>
<ol>
<li>초기 설정: 선수들의 현재 위치를 빠르게 조회할 수 있는 객체(positions) 생성. 이 객체는 선수 이름을 키로, 해당 선수의 인덱스를 값으로 가짐</li>
<li>호출 처리: callings 배열을 순회하며 각 호출에 대해 다음 작업 수행:<ul>
<li><ul>
<li>해당 선수와 바로 앞 선수의 위치 교환</li>
</ul>
</li>
<li><ul>
<li>players 배열과 positions 객체를 모두 업데이트하여 변경된 순위 반영</li>
</ul>
</li>
</ul>
</li>
<li>결과 반환: 최종적으로 업데이트된 players 배열 반환</li>
</ol>
<h2 id="💡-다른-사람의-코드">💡 다른 사람의 코드</h2>
<pre><code class="language-jsx">function solution(players, callings) {
    let idx;
    let name1;
    let name2;
    const idxList = {}

    players.forEach((name,index)=&gt;idxList[name]=index)
    for(let call of callings){
        idx = idxList[call]
        name1 = players[idx]
        name2 = players[idx-1]
        idxList[call]-=1
        idxList[name2]+=1
        players[idx] = name2
        players[idx-1] = name1
    }    

    return players;
}
</code></pre>
<h2 id="💬-마치며">💬 마치며</h2>
<p>초기 for문을 이용한 접근 방식에서 배열 메서드 그리고 객체를 활용까지 해 보면서  시간 복잡도의 중요성과 자료구조 선택의 영향을 실감할 수 있었다.</p>