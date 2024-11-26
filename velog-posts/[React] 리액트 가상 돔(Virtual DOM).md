<h2 id="리액트를-사용-이유">리액트를 사용 이유</h2>
<blockquote>
<p><a href="https://npmtrends.com/">npm 트렌드</a>를 확인할 수 있는 사이트</p>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/4dea58ad-c463-41d7-a01d-b71247d3ced1/image.png" /></p>
<p>최근 5년간 react, svelte, vue 사용량 비교</p>
<p>npm 트렌드 사이트 확인 결과 리액트가 Vue, Svelte 등 다른 프레임워크보다 훨씬 많은 사용자 기반 보유 중</p>
<hr />
<h3 id="리액트의-주요-장점">리액트의 주요 장점</h3>
<ol>
<li><strong>강력한 커뮤니티 지원</strong><ul>
<li>풍부한 교육 자료, 튜토리얼, 예제 코드.</li>
<li>다양한 서드파티 라이브러리 및 도구 제공.</li>
</ul>
</li>
<li><strong>광범위한 생태계</strong><ul>
<li>모바일 앱 개발도 가능 (e.g., React Native).</li>
</ul>
</li>
<li><strong>✅ 가상 DOM</strong><ul>
<li>불필요한 DOM 조작을 줄여 성능 최적화.</li>
</ul>
</li>
</ol>
<hr />
<h2 id="웹-브라우저-렌더링">웹 브라우저 렌더링</h2>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/1601825e-0fd6-4673-a5e9-e357a0fd5244/image.png" /></p>
<p><strong><code>크리티컬 렌더링 패스:</code></strong>브라우저가 HTML, CSS, JS 파일을 처리하여 웹페이지를 화면에 렌더링하는 과정</p>
<ol>
<li>URL 입력 → 브라우저가 서버에 요청</li>
<li>서버가 HTML, CSS, JS 등의 파일을 응답</li>
<li>브라우저가 HTML을 파싱 → DOM 생성</li>
<li>CSS 파싱 → CSSOM 생성</li>
<li>DOM과 CSSOM 결합 → <strong>Render Tree 생성</strong></li>
<li><strong>레이아웃 배치</strong> → 각 요소의 위치와 크기 계산 🚨</li>
<li><strong>페인트(Paint)</strong> → 화면에 픽셀 단위로 그리기 🚨</li>
</ol>
<blockquote>
<p>🚨<strong>:</strong> <strong>계산 비용이 많이 드는 작업</strong></p>
<p>⇒ 성능에 큰 영향을 줌</p>
</blockquote>
<p>✅ 크리티컬 렌더링 패스 과정은 <strong>DOM이 업데이트될 때마다 반복적으로 발생</strong></p>
<h3 id="🤔-언제-업데이트되는가"><strong>🤔 언제 업데이트되는가?</strong></h3>
<p>JS를 이용해서 DOM을 수정할 때마다 업데이트가 발생</p>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/58afe16a-4289-473f-b5d0-174540641fa9/image.png" /></p>
<ol>
<li>DOM 수정 → JS로 DOM API를 사용해 요소 변경</li>
<li>스타일 재계산 → 변경된 요소와 관련된 스타일 계산</li>
<li>레이아웃 계산 → 요소의 크기와 위치 재계산 (리플로우)</li>
<li>실제 화면 업데이트 → 픽셀로 다시 그리기 (리페인트)</li>
</ol>
<h3 id="🚨-리플로우와-리페인트">🚨 리플로우와 리페인트</h3>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/a50ba7c5-ecea-4f69-9600-710e84d81328/image.png" /></p>
<ul>
<li><strong>리플로우</strong>: 레이아웃 배치가 다시 이루어지는 과정(예: <code>width</code>, <code>height</code> 변경 시 발생)</li>
<li><strong>리페인트</strong>: 색상, 배경 등 스타일 변경 시 발생⇒ 리플로우나 리페인트 작업이 많아지면 웹사이트가 응답 불가 상태가 될 수 있음</li>
</ul>
<p>추가) GPU가 관여할 수 있는 속성은 리플로우와 리페인트가 생략됨</p>
<ul>
<li>opacity</li>
<li>transform</li>
</ul>
<blockquote>
<p>💡 성능 최적화: <strong>리플로우와 리페인트를 줄이면 웹페이지의 성능이 향상됨</strong></p>
</blockquote>
<p>즉, DOM 업데이트를 한꺼번에 모아서 처리하면 DOM 수정 횟수를 최소화할 수 있음</p>
<p><strong>코드예제</strong></p>
<pre><code class="language-tsx">&lt;body&gt;
  &lt;button onclick=&quot;render()&quot;&gt;추가&lt;/button&gt;
  &lt;ul&gt;&lt;/ul&gt;
  &lt;script&gt;
      //❌ DOM에 li를 추가할 때마다 리플로우와 리페인팅 작업이 일어나게 됨
    function render() {
      const ulEl = document.querySelector('ul');
      for (let i = 0; i &lt; 300; i++) {
        ulEl.innerHTML += `&lt;li&gt;${i}&lt;/li&gt;`;
      }
    }

    //✅ 렌더링 성능 향상(ver)
    //리플로우 최소화
    function render2() {
      const ulEl = document.querySelector('ul');
      let liEls = &quot;&quot;;
      for (let i = 0; i &lt; 300; i++) {
        liEls += `&lt;li&gt;${i}&lt;/li&gt;`;
      }
      ulEl.innerHTML = liEls; //변수로 모아뒀다가 한 번에 변경
    }
  &lt;/script&gt;
&lt;/body&gt;</code></pre>
<p>하지만 서비스 규모가 커지면 모든 업데이트를 하나하나 관리하기가 어려움 😵‍💫</p>
<p><strong>👍 리액트에서는 이 코드적인 개선 과정을 생각하지 않아도 자동으로 처리해줌</strong> </p>
<hr />
<h2 id="리액트-렌더링">리액트 렌더링</h2>
<p>리액트는 <strong>가상 DOM을 사용</strong>해 DOM 조작을 효율적으로 관리함</p>
<h3 id="가상-dom이란">가상 DOM이란?</h3>
<p>실제 돔과 같은 내용을 담고 있는 <strong>복사본.</strong> 객체 형태로 메모리 안에 저장되어 있음.</p>
<p>실제 DOM 조작은 비용이 크기 때문에, 가상 DOM을 활용해 변경사항을 미리 계산한 후 모아서 한 번만 실제 DOM을 수정하도록 함. 이 과정을 재조정(Reconciliation)이라고 부름</p>
<blockquote>
<p><strong>🤔 그럼 이 가상 돔을 사용하면 항상 빠른 속도를 보장하는가?</strong>
⇒ ❌ 아닐수도 있음. 가상 돔을 생성하고 비교하는데도 연산이 소요되기 때문</p>
</blockquote>
<hr />
<h3 id="가상-dom의-처리-과정-재조정">가상 DOM의 처리 과정 (재조정)</h3>
<ol>
<li><strong>렌더 페이즈 (Render Phase)</strong><ul>
<li><strong>가상 DOM</strong> 생성</li>
<li><strong>이전 가상 DOM과 비교</strong>하여 변경사항 계산(디핑)</li>
<li><strong>비동기적</strong> 처리 가능</li>
</ul>
</li>
<li><strong>커밋 페이즈 (Commit Phase)</strong><ul>
<li>변경사항을 <strong>실제 DOM에 적용</strong></li>
<li><strong>동기적</strong> 처리, 중단 불가</li>
</ul>
</li>
</ol>