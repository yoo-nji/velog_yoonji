<h2 id="가비지-컬렉션과-클로저">가비지 컬렉션과 클로저</h2>
<h3 id="가비지-컬렉션">가비지 컬렉션</h3>
<p><strong><code>가비지 컬렉션이란?</code></strong> 자바스크립트의 자동 메모리 관리 시스템으로, <strong>사용되지 않는 객체를 감지해 메모리에서 해제</strong>하는 과정을 말한다. 실행 컨텍스트가 콜 스택에서 제거될 때 관련 변수들이 가비지 컬렉션의 대상이 된다.</p>
<p>장점: 개발자의 직접적인 메모리 관리 불필요</p>
<h3 id="클로저">클로저</h3>
<p><strong><code>클로저</code></strong>: <strong>내부 함수가 외부 함수의 변수(자유 변수)에 접근</strong>할 수 있는 구조. 이러한 접근 권한은 내부 함수가 외부 함수의 스코프를 기억하기 때문에 가능하며, 주로 <strong>캡슐화</strong>가 필요한 로직에 사용됨</p>
<p><strong>클로저는 하나의 현상으로 이해 가능</strong></p>
<p>클로저는 내부 함수가 외부 변수에 접근하는 기능을 넘어서는 개념. 이를 <strong>클로저 현상</strong>이라 부르며, 함수와 그 환경(스코프) 간의 관계를 설명함</p>
<p>대표적인 예로, 함수 종료 이후에도 특정 변수에 대한 참조가 유지되는 구조. 이러한 현상이 바로 클로저임</p>
<p>즉, 클로저는 함수가 자신이 생성된 환경을 기억하고 접근할 수 있는 특별한 성질을 의미. 이는 단순한 기능 이상의 의미를 가지며, 변수의 은닉화나 메모리 관리와 같은 다양한 실무적 문제를 해결하는 데 활용됨</p>
<p><strong>클로저 현상 예시</strong></p>
<p>counter 함수가 종료된 이후에도 내부 함수는 여전히 count 변수에 접근 가능. </p>
<pre><code class="language-jsx">function counter() {
  let count = 0;
  return function () {
    count++;
    console.log(count);
  };
}

const increment = counter();// 클로저 생성
increment(); // 1
increment(); // 2</code></pre>
<p>⚠️ 클로저가 불필요하게 남아 있으면 <strong>메모리 누수(memory leak)</strong> 발생 가능. 클로저 사용 시 <strong>의도적인 참조 해제</strong> 필요</p>
<p><strong>메모리 누수를 방지 예제 코드</strong></p>
<ol>
<li><p><strong>사용 후 참조 해제</strong></p>
<p> 더 이상 필요 없는 클로저 함수나 객체는 null로 설정해 참조를 끊어줌</p>
</li>
<li><p><strong>WeakMap/WeakSet 활용</strong></p>
<p> 클로저 내에서 불필요한 객체 참조를 줄이기 위해 <strong>WeakMap</strong> 사용. 참조가 끊기면 가비지 컬렉션이 즉시 해제 가능</p>
</li>
</ol>
<pre><code class="language-jsx">let cache = new WeakMap();
function getData(key) {
  if (!cache.has(key)) {
    cache.set(key, `Data for ${key}`);
  }
  return cache.get(key);
}

let obj = {};
console.log(getData(obj)); // Data for [object Object]
obj = null; // 참조가 끊기면 가비지 컬렉션으로 해제</code></pre>
<h2 id="클로저-사용-패턴">클로저 사용 패턴</h2>
<h3 id="1-은닉화">1. 은닉화</h3>
<p>변수를 외부에서 직접 접근할 수 없게 만들어 데이터 보호 가능</p>
<pre><code class="language-jsx">function counter() {
  let count = 0;
  return {
    increment: function () {
      count++;
      return count;
    },
    decrement: function () {
      count--;
      return count;
    },
  };
}

let mycount = counter();
console.log(mycount.increment()); // 출력: 1
console.log(mycount.increment()); // 출력: 2
console.log(mycount.decrement()); // 출력: 1

// 더 이상 mycount 객체가 필요 없을 때 메모리 해제를 위해 null로 설정
mycount = null;</code></pre>
<h3 id="2-함수-팩토리">2. 함수 팩토리</h3>
<p>특정 동작을 하는 함수를 쉽게 생성 가능</p>
<pre><code class="language-jsx">function makeMultiple(multiplier) {
  return function (x) {
    return x * multiplier;
  };
}

let double = makeMultiple(2);
let triple = makeMultiple(3);

console.log(double(5)); // 출력: 10 (5 * 2)
console.log(triple(5)); // 출력: 15 (5 * 3)

double = null;
triple = null;</code></pre>
<h3 id="3-비동기-프로그래밍에서-클로저">3. 비동기 프로그래밍에서 클로저</h3>
<p>비동기 작업에서 데이터를 안전하게 관리하는 데 유용</p>
<pre><code class="language-jsx">function fetchData(url) {
  let result;
  return function (callback) {
    setTimeout(() =&gt; {
      result = &quot;Fetched... Success&quot;;
      callback(result);
    }, 1000);
  };
}

let fetchFromNaver = fetchData(&quot;https://www.naver.com&quot;);
fetchFromNaver((data) =&gt; console.log(data)); // 1초 후 &quot;Fetched... Success&quot; 출력</code></pre>
<h3 id="4-메모이제이션-패턴">4. 메모이제이션 패턴</h3>
<p>함수의 결과를 캐싱하고 재사용함으로써 성능 최적화 가능</p>
<pre><code class="language-jsx">function memoization(fn) {
  const cache = {};
  return function (...args) {
    const key = JSON.stringify(args);
    if (cache[key]) {
      console.log('캐시된 결과 반환');
      return cache[key];
    }
    const result = fn(...args);
    cache[key] = result;
    console.log('새로운 결과 계산 및 캐싱');
    return result;
  };
}

function slowFunction(num) {
  for (let i = 0; i &lt; 1000000000; i++); // 시간이 오래 걸리는 작업 시뮬레이션
  return num * 2;
}

let memoizedFn = memoization(slowFunction);
console.log(memoizedFn(5)); // 새로운 결과 계산 및 캐싱
console.log(memoizedFn(5)); // 캐시된 결과 반환 (빠름)
console.log(memoizedFn(10)); // 새로운 결과 계산 및 캐싱

memoizedFn = null;</code></pre>