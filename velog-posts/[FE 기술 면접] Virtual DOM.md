<h3 id="📌-virtual-dom-개념-정리">📌 <a href="https://velog.io/@yoon_ji/React-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EA%B0%80%EC%83%81-%EB%8F%94Virtual-DOM">Virtual DOM 개념 정리</a></h3>
<hr />
<h3 id="q1-virtual-dom이란-무엇인가요">Q1: Virtual DOM이란 무엇인가요?</h3>
<p>A: Virtual DOM은 실제 DOM을 추상화한 가벼운 복사본으로, 메모리에 객체 형태로 존재합니다. 변경 사항이 발생했을 때 실제 DOM에 직접 반영하지 않고, Virtual DOM에서 먼저 처리한 후 필요한 부분만 실제 DOM에 업데이트하여 효율적인 렌더링을 가능하게 합니다.</p>
<h3 id="q2-virtual-dom을-사용하는-이유는-무엇인가요">Q2: Virtual DOM을 사용하는 이유는 무엇인가요?</h3>
<p>A: DOM을 직접 조작하면 브라우저 렌더링이 빈번하게 발생하여 성능이 저하될 수 있습니다. Virtual DOM을 사용하면 실제 DOM 조작을 최소화하여 성능을 개선할 수 있습니다.</p>
<h3 id="q3-virtual-dom이-항상-더-나은-성능을-보장하나요">Q3: Virtual DOM이 항상 더 나은 성능을 보장하나요?</h3>
<p>A: 반드시 그렇지는 않습니다. Virtual DOM을 생성하고 비교하는 과정에서도 연산 비용이 발생하기 때문입니다. 상황에 따라 성능 차이가 있을 수 있습니다.</p>