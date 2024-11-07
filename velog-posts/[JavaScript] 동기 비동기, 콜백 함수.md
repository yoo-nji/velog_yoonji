<h2 id="1-동기적-작업의-문제점">1. 동기적 작업의 문제점</h2>
<p><strong>자바스크립트 동기</strong>: 한 작업이 완료될 때까지 다음 작업을 기다리게 하는 방식</p>
<p>자바스크립트의 싱글 스레드 특성으로 인해, 오래 걸리는 동기 작업은 다른 모든 작업을 지연시킴</p>
<p>예: 긴 루프나 대기 시간이 있는 작업 실행 중 브라우저 응답 불가</p>
<p>예제</p>
<pre><code class="language-jsx">console.log(&quot;시작&quot;);

for (let i = 0; i &lt; 1000000000; i++) {
  // 긴 루프
}

console.log(&quot;끝&quot;);</code></pre>
<h3 id="실행-순서">실행 순서</h3>
<ol>
<li><code>&quot;시작&quot;</code> 출력</li>
<li>매우 긴 루프 실행 (이 과정에서 브라우저 응답 불가)</li>
<li><code>&quot;끝&quot;</code> 출력</li>
</ol>
<p>이 예제에서 긴 작업이 다른 작업을 차단하여 프로그램 전체가 멈춥</p>
<p><strong>⇒ 동기적 방식으로 긴 작업 처리는 <code>사용자 경험</code>을 저하시킴</strong></p>
<h2 id="비동기-작업-처리-방법"><strong>비동기 작업 처리 방법</strong></h2>
<p>자바스크립트는 이러한 문제를 해결하기 위해 <strong>비동기 처리 방식</strong>을 지원함. <strong>비동기 방식</strong>으로 코드를 작성하면 긴 작업이 있어도 다른 작업이 먼저 실행될 수 있도록 도움</p>
<h3 id="1-웹-api">1. 웹 API</h3>
<ul>
<li>브라우저가 제공하는 API로, 자바스크립트가 <strong>비동기 작업을 처리할 수 있도록 돕는 환경</strong>을 제공</li>
<li>setTimeout 같은 함수들은 브라우저의 웹 API로, 실제 작업을 수행한 후, 콜백 함수를 자바스크립트 엔진으로 다시 전달하여 실행하게 함</li>
</ul>
<pre><code class="language-jsx">console.log(&quot;시작&quot;);

setTimeout(() =&gt; {
  console.log(&quot;비동기 작업 완료&quot;);
}, 2000);

console.log(&quot;끝&quot;);</code></pre>
<p><strong>실행 순서</strong></p>
<ol>
<li><code>&quot;시작&quot;</code>과 <code>&quot;끝&quot;</code>은 동기적으로 실행됨</li>
<li><code>setTimeout</code>은 2초 후 실행되도록 예약되며, 콜백 함수는 <strong>태스크 큐</strong>에 추가됨</li>
<li>이벤트 루프는 콜 스택이 비워지면 태스크 큐의 콜백을 가져와 실행함</li>
</ol>
<p>이 예제에서 자바스크립트는 <code>setTimeout</code>의 콜백을 <strong>비동기</strong>로 처리하여 <code>&quot;끝&quot;</code>을 먼저 출력함</p>
<h3 id="2-콜백-함수">2. 콜백 함수</h3>
<ul>
<li>콜백 함수: 다른 함수에 매개변수로 전달되어 그 함수가 실행되는 동안 특정 시점에 호출되는 함수</li>
<li>예: setTimeout, setInterval, 이벤트 리스너</li>
</ul>
<pre><code class="language-jsx">// 'callback'이라는 이름은 관용적으로 많이 사용됨

function a(callback) {
    setTimeout(() =&gt; {
        console.log(&quot;a&quot;);
        callback();
    }, 0);
}

function b() {
    console.log(&quot;b&quot;);
}

a(b);</code></pre>
<h3 id="화살표-함수의-탄생-배경"><strong>화살표 함수의 탄생 배경</strong></h3>
<p><strong>화살표 함수의 도입 목적</strong></p>
<ul>
<li>콜백 문법의 간결화</li>
<li>중첩된 콜백의 가독성 개선</li>
</ul>
<p><strong>콜백 함수 사용 예제 비교</strong></p>
<pre><code class="language-jsx">function task1(callback) {
    console.log(&quot;task1&quot;);
    callback();
}

function task2() {
    console.log(&quot;task2&quot;);
}</code></pre>
<p>기존 콜백 함수</p>
<pre><code class="language-jsx">// 함수 호출
task1(function() {
    task2();
});</code></pre>
<p>화살표 함수를 사용한 콜백</p>
<pre><code class="language-jsx">// 함수 호출: 화살표 함수로 간결하게 표현
task1(() =&gt; {
    task2();
});</code></pre>
<h2 id="콜백을-사용하여-순서-보장하기">콜백을 사용하여 순서 보장하기</h2>
<p>콜백을 사용하면 작업 순서 보장 가능. 각 작업 완료 후 콜백 호출하여 다음 작업 시작하면 순차적 실행 가능</p>
<p>아래 코드는 여러 콜백 함수를 연달아 사용하는 '콜백 드리블' 방식의 예시. 이 방법은 작업들을 순차적으로 연결</p>
<pre><code class="language-jsx">function task1(callback) {
    console.log(&quot;task1&quot;);
    callback();
}

function task2(callback) {
    console.log(&quot;task2&quot;);
    callback();
}

function task3(callback) {
    setTimeout(() =&gt; {
        console.log(&quot;task3&quot;);
        callback();
    }, 0);
}

function task4() {
    console.log(&quot;task4&quot;);
}

// 함수 호출
task1(() =&gt; {
    task2(() =&gt; {
        task3(() =&gt; {
            task4();
        });
    });
});</code></pre>
<h3 id="전체-코드-실행-순서">전체 코드 실행 순서</h3>
<p>이 코드는 콜백 함수를 이용해 작업의 순서를 보장. 실행 순서는 다음과 같음:</p>
<ol>
<li><code>task1</code> 실행 → <code>&quot;task1&quot;</code> 출력 → <code>task2</code> 호출</li>
<li><code>task2</code> 실행 → <code>&quot;task2&quot;</code> 출력 → <code>task3</code> 호출</li>
<li><code>task3</code> 실행 → <code>setTimeout</code>에 의해 비동기 처리 → 태스크 큐에 추가</li>
<li>콜 스택이 비워진 후 → <code>&quot;task3&quot;</code> 출력 → <code>task4</code> 호출</li>
<li><code>task4</code> 실행 → <code>&quot;task4&quot;</code> 출력 → 전체 작업 완료</li>
</ol>
<p>이러한 방식으로 콜백 함수를 사용하면 비동기 작업을 포함한 모든 작업이 원하는 순서대로 실행됨</p>
<p><strong>결과</strong></p>
<pre><code>task1
task2
task3
task4</code></pre><h3 id="콜백이-없는-경우의-문제">콜백이 없는 경우의 문제</h3>
<pre><code class="language-jsx">function task1() {
    console.log(&quot;task1&quot;);
}

function task2() {
    console.log(&quot;task2&quot;);
}

function task3() {
    setTimeout(() =&gt; {
        console.log(&quot;task3&quot;);
    }, 0);
}

function task4() {
    console.log(&quot;task4&quot;);
}

task1();
task2();
task3();
task4();</code></pre>
<p><code>task3</code>은 비동기 함수로, 0초 지연 설정에도 불구하고 태스크 큐에 추가되어 대기함.</p>
<p>따라서 다른 동기 작업들이 먼저 실행된 후에 처리되어 다음과 같은 순서로 출력</p>
<pre><code>task1
task2
task4
task3</code></pre><p>이렇게 되면 원하는 순서와 다르게 <strong>task3</strong>이 마지막에 출력됨 ⇒ <strong>비동기 함수가 순서를 흐트러뜨린 것</strong></p>
<h1 id="콜백지옥">콜백지옥</h1>
<p>콜백 함수는 비동기 작업의 순차 실행에 유용하지만, <strong>중첩이 많아지면 가독성이 떨어지는 '콜백 지옥'</strong> 문제가 발생함</p>
<p>중첩된 콜백은 코드를 복잡하게 만들고 유지보수를 어렵게 함. 이 문제 해결을 위해 <strong>Promise</strong>가 도입됨</p>
<pre><code class="language-jsx">// 함수 호출
task1(() =&gt; {
  task2(() =&gt; {
    task3(() =&gt; {
      task4();
    });
  });
});</code></pre>