<h2 id="🔎-비동기-함수-qa">🔎 비동기 함수 Q&amp;A</h2>
<h3 id="q-자바스크립트가-싱글스레드를-갖고-있음에도-어떻게-비동기-처리를-하나요">Q: 자바스크립트가 싱글스레드를 갖고 있음에도 어떻게 비동기 처리를 하나요?</h3>
<blockquote>
<p>A: 자바스크립트는 싱글 스레드 기반 언어이지만, <strong>Web API</strong>를 통해 비동기 처리가 가능합니다.</p>
</blockquote>
<p>비동기 처리는 다음과 같은 순서로 이루어집니다</p>
<ol>
<li>비동기 작업이 발생하면, 자바스크립트는 이를 Web API에 <strong>위임</strong>합니다.</li>
<li>Web API는 <strong>별도의 스레드</strong>에서 작업을 수행합니다.</li>
<li>작업이 완료되면, 콜백 함수가 <strong>태스크 큐</strong>에 추가됩니다.</li>
<li>이벤트 루프는 콜 스택이 비었는지 확인하고, 비었다면 태스크 큐에서 콜백 함수를 가져와 실행합니다.<blockquote>
</blockquote>
이렇게 자바스크립트는 Web API를 활용해 비동기 작업을 처리하며, 메인 스레드가 멈추지 않고 다른 작업을 계속 수행할 수 있게 됩니다.</li>
</ol>
<h3 id="q-비동기-함수에-대해-설명해주세요">Q: 비동기 함수에 대해 설명해주세요.</h3>
<blockquote>
<p>A: 비동기 함수는 함수의 실행 결과가 <strong>즉시 반환되지 않고</strong>, 특정 조건(예: 작업 완료)이 충족될 때까지 기다리는 함수입니다.
주로 네트워크 요청, 파일 읽기, 타이머 설정 등 시간이 오래 걸리는 작업에서 사용됩니다.
비동기 함수는 일반적으로 <strong>콜백 함수</strong>나 <strong>Promise 객체</strong>를 반환합니다.</p>
</blockquote>
<ul>
<li><strong>콜백 함수</strong>: 비동기 작업이 완료되었을 때 호출됩니다.</li>
<li><strong>Promise 객체</strong>: 비동기 작업이 성공했는지 혹은 실패했는지를 나타냅니다.<blockquote>
</blockquote>
비동기 함수를 사용하면 서비스의 <strong>성능</strong>과 <strong>반응성</strong>을 유지할 수 있습니다. 다만, <strong>콜백 지옥</strong> 문제가 발생할 수 있으므로, 이를 방지하기 위해 <strong>Promise의 메서드</strong>(then, catch, finally)나 <strong>async/await</strong>을 사용하여 코드를 구성하는 것이 중요합니다.<blockquote>
</blockquote>
여러 비동기 함수가 실행될 경우, 자바스크립트는 <strong>이벤트 루프</strong>를 사용해 작업을 제어합니다. 이벤트 루프는 실행 대기 중인 비동기 함수의 콜백을 <strong>태스크 큐(Task Queue)</strong>에서 꺼내 실행하며, 이를 통해 비동기 함수의 실행 순서를 관리합니다.</li>
</ul>
<h3 id="q-이벤트-루프란-무엇인가요">Q: 이벤트 루프란 무엇인가요?</h3>
<blockquote>
<p>A: 여러 비동기 함수가 실행되면 브라우저와 자바스크립트 엔진이 함께 처리합니다. 여기서 이벤트 루프는 자바스크립트가 비동기 작업을 처리하기 위한 브라우저의 내장 기능입니다</p>
</blockquote>
<p>싱글 스레드 기반인 자바스크립트는 콜 스택과 태스크 큐를 사용하여 작업을 처리합니다</p>
<blockquote>
</blockquote>
<p>이벤트 루프의 동작 방식은 다음과 같습니다</p>
<blockquote>
</blockquote>
<ol>
<li>자바스크립트 엔진이 콜 스택에 있는 동기 작업을 실행합니다.</li>
<li>비동기 작업은 <strong>Web API</strong>로 전달됩니다.</li>
<li>Web API는 비동기 작업이 완료되면, 콜백 함수를 태스크 큐에 추가합니다.</li>
<li>이벤트 루프는 콜 스택이 비어 있는지 확인하고, 비었다면 태스크 큐에서 작업을 꺼내 실행합니다.<blockquote>
</blockquote>
즉, 이벤트 루프는 콜 스택과 태스크 큐를 반복적으로 확인하며, <strong>비동기 함수의 실행 순서를 제어</strong>합니다. 이를 통해 자바스크립트는 싱글 스레드 환경에서도 비동기 작업을 효과적으로 처리할 수 있습니다</li>
</ol>
<h3 id="q-asyncawait-사용-방법을-설명해주세요">Q: async/await 사용 방법을 설명해주세요.</h3>
<blockquote>
<p>A: async/await는 ES8부터 도입된 Promise 기반의 비동기 처리 문법입니다. 이는 비동기 코드를 동기적인 코드처럼 작성할 수 있어 가독성이 뛰어납니다. 함수 앞에 async 키워드를 붙여 async 함수로 정의하고, 함수 내부에서 Promise를 반환하는 부분 앞에 await 키워드를 사용합니다. 코드 실행 중 await 키워드를 만나면 비동기 작업이 완료될 때까지 기다렸다가 결과값을 받아 처리하며, async 함수는 항상 Promise 객체를 반환합니다.</p>
</blockquote>
<h3 id="q-promise와-asyncawait의-차이점을-설명해주세요">Q: Promise와 async/await의 차이점을 설명해주세요.</h3>
<blockquote>
<p>A: 첫 번째는 에러 처리 방식의 차이입니다. async/await는 일반적인 try...catch 문으로 에러 처리가 가능합니다. Promise의 경우 .catch()를 사용해야 하며, 에러가 발생한 정확한 위치를 파악하기가 상대적으로 어렵습니다. async/await는 에러가 발생한 코드의 위치를 더 명확하게 보여줍니다.</p>
</blockquote>
<p>두 번째는 코드 가독성입니다. Promise는 연속된 .then() 체이닝으로 인해 코드가 복잡해질 수 있습니다. 반면 async/await는 일반적인 동기 코드처럼 작성할 수 있어 코드의 흐름을 더 쉽게 이해할 수 있습니다.</p>
<hr />
<h2 id="동기-vs-비동기">동기 vs 비동기</h2>
<h3 id="동기-프로그래밍">동기 프로그래밍</h3>
<p>자바스크립트는 <strong>기본적으로 동기적</strong>(Synchronous)으로 동작하는 <strong>싱글 스레드 언어</strong></p>
<p>⇒ 🤔 왜? 코드를 실행시켜주는 <strong>자바스크립트 엔진은 한 번에 한가지 일만 할 수 있기 때문</strong></p>
<ul>
<li><strong>동기적인 실행 방식 장점:</strong> 코드의 실행 순서가 <strong><code>예측 가능</code></strong>하고 명확함</li>
<li><strong>동기적인 실행 방식 단점:</strong> 시간이 오래 걸리는 작업 수행 시 해당 작업이 완료될 때까지 다음 코드의 실행이 차단되는 <strong><code>블로킹</code></strong>(blocking) 현상 발생<ul>
<li>ex) 서버로부터 데이터를 받아오는 네트워크 통신</li>
</ul>
</li>
</ul>
<h3 id="비동기-프로그래밍">비동기 프로그래밍</h3>
<p>✅ 이러한 문제를 해결하는 게 <strong>비동기 프로그래밍</strong></p>
<p><strong>비동기 프로그래밍이란?</strong></p>
<p>시간이 오래 걸리는 작업이 실행되는 동안 다른 작업들을 계속 수행할 수 있게 해주는 프로그래밍 방식</p>
<p><strong>🤔 어떻게 이게 가능한가?</strong></p>
<p>⇒ <code>Web API</code></p>
<p>ex) setTimeout, fetch, Dom api</p>
<p>웹 API는 <strong>브라우저가 제공하는 멀티스레드 환경</strong>에서 실행됨. 브라우저는 자바스크립트 엔진과는 <strong>별도로 여러 작업을 동시</strong>에 처리할 수 있는 멀티스레드 환경을 가지고 있어서, 비동기 작업을 처리할 수 있음</p>
<p><strong>✅ 비동기 처리 동작 원리</strong></p>
<ol>
<li>자바스크립트 엔진의 메인 스레드가 코드를 실행하다가 비동기 작업을 만나면, 이를 Web API로 위임</li>
<li>Web API는 별도의 스레드에서 해당 작업을 수행</li>
<li>작업이 완료되면 콜백 함수를 태스크 큐(Task Queue)에 넣음</li>
<li>이벤트 루프는 콜 스택이 비어있는지 지속적으로 확인하고, 비어있다면 태스크 큐의 콜백 함수를 콜 스택으로 이동시켜 실행</li>
</ol>
<h3 id="동기-vs-비동기-프로그래밍-비교">동기 vs 비동기 프로그래밍 비교</h3>
<table>
<thead>
<tr>
<th>구분</th>
<th>동기적 수행</th>
<th>비동기적 수행</th>
</tr>
</thead>
<tbody><tr>
<td>처리 방식</td>
<td>한번에 하나씩</td>
<td>여러 작업 동시 진행 가능</td>
</tr>
<tr>
<td>실행 순서</td>
<td>순서대로 실행</td>
<td>순서가 보장되지 않음</td>
</tr>
<tr>
<td>예시</td>
<td>작업1 → 작업2 → 작업3</td>
<td>작업1, 작업2, 작업3 병렬 실행</td>
</tr>
</tbody></table>
<p><strong>예시 코드로 동기와 비동기 비교</strong></p>
<pre><code class="language-jsx">// 동기적 실행
console.log('첫 번째 작업 시작');
for (let i = 0; i &lt; 3000000000; i++) {} // 시간이 오래 걸리는 작업
console.log('첫 번째 작업 완료');
console.log('두 번째 작업');

// 실행 결과
// 첫 번째 작업 시작
// (약 3초 후)
// 첫 번째 작업 완료
// 두 번째 작업

// 비동기적 실행
console.log('첫 번째 작업 시작');
setTimeout(() =&gt; {
    console.log('첫 번째 작업 완료');
}, 3000);
console.log('두 번째 작업');

// 실행 결과
// 첫 번째 작업 시작
// 두 번째 작업
// (3초 후)
// 첫 번째 작업 완료</code></pre>
<p>위 예시의 동기적 실행 시 시간이 오래 걸리는 작업 완료까지 다음 작업이 블로킹됨. 반면 비동기적 실행 시 시간이 오래 걸리는 작업(setTimeout)을 Web API에 위임하고 바로 다음 작업 실행 가능함</p>
<hr />
<h2 id="비동기-처리-방식의-발전">비동기 처리 방식의 발전</h2>
<h2 id="1-콜백-함수">1. 콜백 함수</h2>
<p><strong>콜백 함수란?</strong></p>
<p>다른 함수에 매개변수로 전달되어 나중에 실행되는 함수</p>
<p>예제: fetchData 함수는 매개변수로 callback 함수를 받아, setTimeout이 완료된 후에 이 callback 함수를 실행</p>
<pre><code class="language-jsx">function fetchData(callback) {
    setTimeout(() =&gt; {
            console.log('서버에서 데이터를 받아왔어요');
        callback();
    }, 1000);
}

fetchData(() =&gt; {
    console.log('후처리...');
});</code></pre>
<p>실행 결과</p>
<pre><code>// 1초 후
서버에서 데이터를 받아왔어요
후처리...</code></pre><h2 id="2-promise">2. Promise</h2>
<p><strong>Promise란?</strong></p>
<p>비동기 처리에 사용되는 자바스크립트 객체로, 비동기 작업의 성공 또는 실패 상태(state)와 결과값(result)을 보관하고 관리함</p>
<p>⇒ Promise의 상태에 따라 적절한 처리를 할 수 있음</p>
<ul>
<li><strong>성공(fulfilled) 시:</strong> <code>.then()</code> 메서드를 통해 성공 결과값을 처리</li>
<li><strong>실패(rejected) 시:</strong> <code>.catch()</code> 메서드를 통해 에러를 처리</li>
</ul>
<p>이렇게 Promise의 상태를 기반으로 비동기 작업의 결과를 체계적으로 처리할 수 있음</p>
<p><strong>Promise의 3가지 상태</strong></p>
<ul>
<li><strong>대기(pending):</strong> 비동기 작업이 아직 완료되지 않은 <strong>초기 상태</strong>이며, 이때 result 값은 undefined입니다.</li>
<li><strong>이행(fulfilled):</strong> 비동기 작업이 성공적으로 완료된 상태</li>
<li><strong>거부(rejected):</strong> 비동기 작업이 실패한 상태</li>
</ul>
<h3 id="promise-기본형태"><strong>Promise 기본형태</strong></h3>
<p><strong>Promise 생성자, Executor 함수</strong></p>
<p><strong><code>Promise</code></strong>는 생성자 함수를 통해 생성되며, 함수를 전달받는데 이 함수를 <strong><code>Executor</code></strong>(실행자)라고 한다</p>
<p>이 실행자 함수는 인자로 <code>resolve</code>, <code>reject</code> 를 전달받는다</p>
<pre><code class="language-jsx">const promise = new Promise((resolve, reject) =&gt; {
    // 비동기 작업 수행
    if (/* 성공 조건 */) {
        resolve('성공 결과값');  // 성공 시 호출
    } else {
        reject(new Error('실패 사유'));  // 실패 시 호출
    }
});</code></pre>
<p><strong>Executor 함수의 매개변수</strong></p>
<ul>
<li><strong>resolve:</strong> 비동기 작업이 성공적으로 완료되었을 때 호출하는 함수</li>
<li><strong>reject:</strong> 비동기 작업이 실패했을 때 호출하는 함수</li>
</ul>
<p><strong>Promise의 결과</strong></p>
<ul>
<li><strong>성공 결과값:</strong> resolve 함수로 전달된 값</li>
<li><strong>실패 결과값:</strong> reject 함수로 전달된 에러 객체</li>
</ul>
<h2 id="promise의-특징">Promise의 특징</h2>
<h3 id="1-executor-함수는-promise가-생성되는-즉시-실행"><strong>1. Executor 함수는 Promise가 생성되는 즉시 실행</strong></h3>
<p>⇒ new Promise()가 호출되는 순간 내부의 코드가 실행된다</p>
<p>원하는 시점에서 Promise를 실행하고 싶다면? <strong>함수 안</strong>에 넣어주면 됨</p>
<pre><code class="language-jsx">function getData() {
    const promise = new Promise((resolve, reject) =&gt; {
        console.log('비동기 작업 시작!');
        // 비동기 작업 수행
        setTimeout(() =&gt; {
            resolve('작업 완료!'); // 이행 상태로 변경하며 값 전달
        }, 1000);
    });

    return promise;
}

// 원하는 시점에 함수를 호출하여 Promise를 실행할 수 있음
getData()
    .then(result =&gt; console.log(result)) // (성공) 작업 완료!
    .catch(error =&gt; console.error(error)); // (실패)</code></pre>
<p>🤔 <strong>프로미스를 리턴하는 이유는?</strong></p>
<p>⇒ 프로미스 <code>상태</code>를 통해 함수에서 <strong>결과를 처리</strong>하기 위해서</p>
<p>❌ 만약 프로미스를 리턴하지 않으면, 데이터가 언제 도착할지 모르기 때문에 결과를 바로 사용할 수 없음</p>
<p>✅ 하지만 프로미스를 리턴하면, <code>.then()</code>을 사용해서 &quot;데이터가 도착하면 이렇게 처리해줘!&quot;라고 미리 약속할 수 있음</p>
<p><strong>Promise 메서드</strong></p>
<ul>
<li><p><strong>.then():</strong> Promise가 <strong><code>이행</code></strong>(fulfilled)되었을 때 실행할 콜백 함수를 등록</p>
</li>
<li><p><strong>.catch():</strong> Promise가 <strong><code>거부</code></strong>(rejected)되었을 때 실행할 콜백 함수를 등록</p>
</li>
<li><p><strong>.finally():</strong> Promise의 성공/실패 여부와 관계없이 제일 마지막에 실행할 콜백 함수를 등록</p>
<p>  ⇒ <strong><code>마무리작업</code></strong>: cleanup 작업이나 리소스 해제 등에 사용됨</p>
</li>
</ul>
<p><strong>Promise 메서드의 콜백 함수는 매개변수를 전달받을 수 있다</strong></p>
<ul>
<li><strong>.then(value =&gt; {}):</strong> resolve()로 전달된 값을 매개변수로 받음</li>
<li><strong>.catch(error =&gt; {}):</strong> reject()로 전달된 값을 매개변수로 받음</li>
<li><strong>.finally(() =&gt; {}):</strong> 상태와 관계없이 실행되는 콜백 함수는 매개변수를 전달받지 않음</li>
</ul>
<h3 id="2-promise의-체이닝"><strong>2. Promise의 체이닝</strong></h3>
<p><strong><code>.then()</code></strong> 메서드는 항상 새로운 Promise를 반환하기 때문에 메서드 체이닝이 가능함</p>
<pre><code class="language-jsx">promise
    .then(result =&gt; result * 2)
    .then(result =&gt; result + 1)
    .then(result =&gt; console.log(result));</code></pre>
<p>각 <code>.then()</code>은 이전 .then()의 <strong>반환값</strong>을 받아 처리하고 새로운 Promise를 반환</p>
<p><code>.catch()</code>도 Promise를 반환해 체이닝이 가능하며, 이를 통해 <strong>비동기 작업과 에러를 순차적으로 처리</strong>할 수 있음</p>
<h3 id="fetch-api">fetch API</h3>
<p><strong><code>fetch()</code></strong> <strong>프로미스를 리턴</strong>하는 브라우저에서 제공하는 비동기 함수(<code>Web API</code>)</p>
<ul>
<li>특정 서버로부터 데이터를 받아올 때 사용</li>
<li>문자열 형식으로 서버에 데이터를 전송</li>
</ul>
<pre><code class="language-jsx">// GET
fetch('url')
  .then(response =&gt; response.json())
  .then(data =&gt; console.log(data))
  .catch(err =&gt; console.log(err))</code></pre>
<ol>
<li><code>fetch('url')</code>: 특정 URL에 요청</li>
<li><code>.then(response =&gt; response.json())</code>: 서버로부터 받은 응답(Response)을 JSON 형태로 파싱</li>
<li><code>.then(data =&gt; console.log(data))</code>: 파싱된 데이터를 콘솔에 출력</li>
<li><code>.catch(err =&gt; console.log(err))</code>: 요청 중 에러가 발생하면 에러를 콘솔에 출력</li>
</ol>
<h2 id="promise-static-메서드">Promise Static 메서드</h2>
<ol>
<li><strong>Promise.all()</strong></li>
</ol>
<p>Promise.all()은 배열로 여러 Promise를 전달받아 동시에 병렬로 실행하고, 모든 Promise가 완료되면 결과값을 배열로 반환함</p>
<p>✅ <strong>성공 조건</strong>: 모든 Promise가 성공적으로 이행되어야 전체가 성공으로 처리</p>
<p><strong>⇒ 하나라도 실패하면 전체가 실패</strong>로 처리</p>
<pre><code class="language-jsx">const promise1 = Promise.resolve(3);
const promise2 = new Promise(resolve =&gt; setTimeout(() =&gt; resolve('foo'), 2000));

Promise.all([promise1, promise2])
  .then(values =&gt; console.log(values)) // [3, 'foo']
  .catch(error =&gt; console.log(error));</code></pre>
<ol>
<li><strong>Promise.allSettled()</strong></li>
</ol>
<p>Promise.allSettled()는 각 <strong>Promise의 성공/실패 상태와 결과를 모두 확인 가능</strong></p>
<pre><code class="language-jsx">const promises = [
  new Promise((resolve) =&gt; resolve(&quot;성공&quot;)),
  new Promise((resolve, reject) =&gt; reject(&quot;실패&quot;))
];

Promise.allSettled(promises)
  .then(data =&gt; console.log(data));

// 콘솔 출력:
// [
//   { status: &quot;fulfilled&quot;, value: &quot;성공&quot; },
//   { status: &quot;rejected&quot;, reason: &quot;실패&quot; }
// ]</code></pre>
<p><strong>Promise.race()</strong></p>
<p>Promise.race()는 여러 Promise 중 가장 먼저 완료되는 Promise의 결과값을 반환</p>
<p>⇒ 경주에서 <strong>가장 먼저 도착한 Promise의 결과</strong>만 사용됨(성공 실패 여부 상관없음)</p>
<pre><code class="language-jsx">const promise1 = new Promise(resolve =&gt; setTimeout(() =&gt; resolve('1등'), 2000));
const promise2 = new Promise(resolve =&gt; setTimeout(() =&gt; resolve('2등'), 1000));

Promise.race([promise1, promise2])
  .then(result =&gt; console.log(result)) // '2등'
  .catch(error =&gt; console.log(error));</code></pre>
<p><strong>Promise.any()</strong></p>
<p>Promise.any()는 여러 Promise 중 가장 먼저 <strong>성공</strong>하는 Promise의 결과값을 반환</p>
<p>⇒ race()와 비슷하지만, 실패는 무시하고 <strong>첫 번째 성공만 반환</strong>한다는 점이 다름</p>
<pre><code class="language-jsx">const promise1 = Promise.reject('실패1');
const promise2 = new Promise(resolve =&gt; setTimeout(() =&gt; resolve('성공!'), 1000));
const promise3 = Promise.reject('실패2');

Promise.any([promise1, promise2, promise3])
  .then(result =&gt; console.log(result)) // '성공!'
  .catch(error =&gt; console.log(error));</code></pre>
<h2 id="3-asyncawait">3. Async/Await</h2>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/475a7452-bfc3-4adf-a0ab-46406a85905f/image.png" /></p>
<p><strong><code>Async/Await</code>는 프로미스 체이닝의 한계를 극복하기 위해 도입된 문법</strong></p>
<ul>
<li>프로미스는 <code>.then()</code>이 계속 이어지면서 코드가 복잡해지는 문제가 있음 ⇒ <strong>프로미스 체이닝</strong></li>
<li>Async/Await를 사용하면 비동기 코드를 <strong>동기 코드처럼 작성</strong>할 수 있어 가독성이 좋아짐</li>
</ul>
<p><strong>사용 방법</strong></p>
<ul>
<li><p><code>async</code>: 함수 앞에 <code>async</code> 를 붙여 비동기 함수임을 선언, 이 함수는 항상 <strong>Promise를 리턴</strong>함</p>
</li>
<li><p><code>await</code>: <strong>async 함수</strong> 내에서 비동기함수를 기다렸다가 다음 작업을 실행하고 싶을 때, 비동기함수 앞에 붙여줌</p>
<p>  ⇒ 비동기함수의 Promise가 처리될 때까지 기다렸다가 다음 작업을 실행</p>
</li>
</ul>
<p>⚠️ await는 반드시 async 함수 내부에서만 사용할 수 있음</p>
<h3 id="✅-프로미스체이닝-vs-asyncawait-방식-비교">✅ 프로미스체이닝 vs <strong>Async/Await 방식 비교</strong></h3>
<p><strong>fetchData 함수를 사용하는 두 가지 방식을 비교</strong></p>
<pre><code class="language-jsx">// 데이터를 가져오는 Promise를 반환하는 함수
function fetchData() {
  return new Promise((resolve) =&gt; {
    setTimeout(() =&gt; {
      console.log(&quot;데이터를 받아왔습니다.&quot;);
      resolve(&quot;데이터&quot;);
    }, 1000);
  });
}</code></pre>
<ol>
<li><strong>Promise 체이닝 방식</strong></li>
</ol>
<pre><code class="language-jsx">// Promise 체이닝을 사용한 방식
fetchData()
  .then((data) =&gt; {
    console.log(data);
    return fetchData();  // 두 번째 데이터 요청
  })
  .then((data) =&gt; {
    console.log(data);
    console.log(&quot;Promise 체이닝 완료&quot;);
  });</code></pre>
<ol>
<li><strong>async/await 방식</strong></li>
</ol>
<pre><code class="language-jsx">// async/await를 사용한 방식
async function getData() {
  console.log(&quot;Async/Await 시작&quot;);

  const data1 = await fetchData();  // 첫 번째 데이터 기다리기
  console.log(data1);

  const data2 = await fetchData();  // 두 번째 데이터 기다리기
  console.log(data2);

  console.log(&quot;Async/Await 완료&quot;);
}

getData();</code></pre>
<p>async/await를 사용하면 순서대로 작업이 진행되는 것처럼(동기) 직관적으로 코드를 작성할 수 있다</p>
<p>⇒ 가독성 ⬆️</p>
<h3 id="에러-처리-방법"><strong>에러 처리 방법</strong></h3>
<p>Promise와 async/await의 에러 처리 방식을 비교</p>
<ol>
<li><strong>Promise</strong></li>
</ol>
<pre><code class="language-jsx">// Promise의 에러 처리
fetchData()
  .then(data =&gt; {
    console.log(data);
  })
  .catch(error =&gt; {
    console.error('에러 발생:', error);
  });</code></pre>
<ol>
<li><strong>async/await</strong></li>
</ol>
<pre><code class="language-jsx">// async/await의 에러 처리
async function getData() {
  try {
      // 비동기 작업 시도
    const data = await fetchData();
    console.log(data);
  } catch (error) {
      // 에러 발생 시 실행되는 코드
    console.error('에러 발생:', error);
  } finally {
    // 성공/실패 여부와 관계없이 항상 실행되는 코드
    console.log('작업 완료');
  }
}</code></pre>
<p><code>async/await</code>는 try-catch 구문 사용</p>
<ul>
<li><strong>try</strong>: 비동기 작업을 포함한 실행할 코드 블록</li>
<li><strong>catch</strong>: try 블록에서 에러가 발생했을 때 실행되는 코드 블록</li>
<li><strong>finally</strong>: 에러 발생 여부와 관계없이 마지막에 실행되는 코드 블록 (선택사항)</li>
</ul>
<hr />
<p>출처
<a href="https://youtu.be/rY3sRxQZG6U?si=C7KuzJAwtDE9479P">유튜브 별코딩 비동기 프로그래밍</a>
<a href="https://velog.io/@kados22/FE-%EA%B8%B0%EC%88%A0-%EB%A9%B4%EC%A0%91-JS-%EB%B9%84%EB%8F%99%EA%B8%B0-%EC%B2%98%EB%A6%AC%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94">https://velog.io/@kados22/FE-기술-면접-JS-비동기-처리에-대해-설명해주세요</a>
<a href="https://studyhard-everyday.tistory.com/33">https://studyhard-everyday.tistory.com/33</a></p>