<h2 id="생성자함수-정의">생성자함수 정의</h2>
<p><strong><code>생성자 함수</code></strong>는 새로운 객체를 생성할 때 사용되는 특수한 함수.</p>
<p>이 함수는 <strong><code>new</code> 키워드</strong>와 함께 호출되며, 호출 시 <strong>새로운 인스턴스</strong> 반환.</p>
<p>생성자 함수의 이름은 <strong>대문자로 시작</strong>하는 것이 관례. </p>
<p><strong>대문자로 시작하는 이유</strong></p>
<ol>
<li><strong>가독성 향상</strong>: 대문자로 시작하는 함수명을 보면 개발자들은 즉시 생성자 함수임을 인식 가능</li>
<li><strong>구분 용이</strong>: 일반 함수와 생성자 함수를 명확하게 구분 가능</li>
<li><strong>실수 방지</strong>: <code>new</code> 키워드 없이 호출하는 실수를 줄이는 데 도움</li>
</ol>
<p>예시</p>
<pre><code class="language-jsx">function Person(name, age) {
  this.name = name;
  this.age = age;
}

const person1 = new Person(&quot;윤지&quot;, 18);
console.log(person1.name); // 출력: 윤지
console.log(person1.age);  // 출력: 18</code></pre>
<ul>
<li>이 예제에서 <code>Person</code> 함수는 생성자 함수로 사용됨</li>
<li><code>new</code> 키워드로 객체 생성 시, <code>this</code>는 새로 생성된 객체를 가리킴</li>
<li><code>this.name</code>과 <code>this.age</code>는 새 객체의 속성으로 설정됨</li>
</ul>
<h3 id="생성자-함수의-장점">생성자 함수의 장점</h3>
<p>매개변수만 변경하여 동일한 구조의 객체를 쉽게 여러 개 생성 가능</p>
<p>이렇게 하면 같은 구조를 가진 여러 객체를 간단하게 생성할 수 있어 코드의 재사용성과 효율성 향상</p>
<pre><code class="language-jsx">const person1 = new Person(&quot;윤지&quot;, 18);
const person2 = new Person(&quot;민수&quot;, 25);
const person3 = new Person(&quot;지영&quot;, 30);</code></pre>
<h2 id="객체-정의-방식-비교">객체 정의 방식 비교</h2>
<h3 id="1-객체-리터럴-방식">1. 객체 리터럴 방식</h3>
<pre><code class="language-jsx">const person = {
  name: &quot;윤지&quot;,
  age: 18,
  introduce: function() {
    console.log(`안녕하세요, 제 이름은 ${this.name}이고 ${this.age}살입니다.`);
  }
};

person.introduce(); // 출력: 안녕하세요, 제 이름은 윤지이고 18살입니다.</code></pre>
<ul>
<li><strong>즉시 생성</strong>: 객체를 한 번만 생성할 때 적합</li>
<li><strong>메모리 효율성</strong>이 떨어질 수 있음. 각 객체마다 메서드가 따로 저장</li>
</ul>
<h3 id="2-생성자-함수를-사용한-객체-정의">2. 생성자 함수를 사용한 객체 정의</h3>
<pre><code class="language-jsx">function Person(name, age) {
  this.name = name;
  this.age = age;
  this.introduce = function() {
    console.log(`안녕하세요, 제 이름은 ${this.name}이고 ${this.age}살입니다.`);
  }
}

const person = new Person(&quot;윤지&quot;, 18);
person.introduce(); // 출력: 안녕하세요, 제 이름은 윤지이고 18살입니다.</code></pre>
<ul>
<li><strong>재사용성</strong>이 높아 여러 인스턴스를 쉽게 생성 가능</li>
<li>메서드가 각 인스턴스마다 복제되어 메모리 사용량 증가 가능성 존재. <strong>프로토타입</strong> 활용으로 이 문제 해결 가능</li>
</ul>
<h3 id="콘솔창에서-구분">콘솔창에서 구분</h3>
<pre><code class="language-jsx">function User(name, age) {
  this.name = name;
  this.age = age;
}

const u = new User(&quot;철수&quot;, 30);

console.log(u); // User { name: '철수', age: 30 }</code></pre>
<p>아래 사진: 위는 객체 리터럴, 아래는 생성자 함수로 생성된 객체</p>
<p>생성자 함수로 만든 객체: <strong>중괄호 앞에 User 표시</strong>됨</p>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/754c8055-8aed-43ae-bad5-8b926eca50eb/image.png" /></p>
<h2 id="프로토타입을-이용한-메모리-효율화">프로토타입을 이용한 메모리 효율화</h2>
<pre><code class="language-jsx">function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.introduce = function() {
  console.log(`안녕하세요, 제 이름은 ${this.name}이고 ${this.age}살입니다.`);
};

const person1 = new Person(&quot;윤지&quot;, 18);
const person2 = new Person(&quot;민수&quot;, 25);

person1.introduce(); // 출력: 안녕하세요, 제 이름은 윤지이고 18살입니다.
person2.introduce(); // 출력: 안녕하세요, 제 이름은 민수이고 25살입니다.</code></pre>
<p><strong>프로토타입</strong> 사용 시 <strong>모든 인스턴스가 같은 메서드를 공유</strong>하여 메모리 사용 절약됨</p>
<h2 id="예제-동물병원-차트-생성자-함수">예제: 동물병원 차트 생성자 함수</h2>
<pre><code class="language-jsx">function 동물차트(이름, 종류, 나이, 주인) {
  this.이름 = 이름;
  this.종류 = 종류;
  this.나이 = 나이;
  this.주인 = 주인;
  this.방문기록 = [];

  this.방문추가 = function(날짜, 이유, 치료) {
    this.방문기록.push({ 날짜, 이유, 치료 });
  }

  this.마지막방문 = function() {
    if (this.방문기록.length &gt; 0) {
      return this.방문기록[this.방문기록.length - 1];
    }
    return &quot;방문 기록 없음&quot;;
  }
}

const 고양이 = new 동물차트(&quot;나비&quot;, &quot;고양이&quot;, 3, &quot;김철수&quot;);
const 강아지 = new 동물차트(&quot;멍멍이&quot;, &quot;개&quot;, 5, &quot;이영희&quot;);

고양이.방문추가(&quot;2024-10-25&quot;, &quot;정기검진&quot;, &quot;예방접종&quot;);
강아지.방문추가(&quot;2024-10-28&quot;, &quot;다리 부상&quot;, &quot;붕대&quot;);

console.log(고양이.이름); // 출력: 나비
console.log(강아지.마지막방문()); // 출력: { 날짜: '2024-10-28', 이유: '다리 부상', 치료: '붕대' }</code></pre>
<p>이 예제에서 <strong>생성자 함수</strong>를 사용해 동물병원 차트 구현. 객체마다 독립적인 방문 기록 관리 가능함</p>
<h2 id="time-생성자함수">Time 생성자함수</h2>
<p><strong>시간 객체</strong>를 생성하는 생성자 함수 정의. 각 인스턴스는 시간을 표시하는 기능 제공</p>
<pre><code class="language-jsx">function Time(hour, minute, seconds) {
  this.hour = hour;
  this.minute = minute;
  this.seconds = seconds;

  this.getTime = function () {
    return `${this.hour}:${this.minute}:${this.seconds}`;
  };
}

const time1 = new Time(15, 30, 27);
console.log(time1.getTime());</code></pre>
<pre><code class="language-jsx">// Time 생성자 함수 정의
function Time(hours, minutes, seconds) {
  this.hours = hours;
  this.minutes = minutes;
  this.seconds = seconds;

  this.toString = function() {
    return `${this.padZero(this.hours)}:${this.padZero(this.minutes)}:${this.padZero(this.seconds)}`;
  };

  this.padZero = function(num) {
    return num.toString().padStart(2, '0');
  };
}

// Time 객체 생성 및 사용 예제
const currentTime = new Time(14, 30, 0);
console.log(currentTime.toString()); // &quot;14:30:00&quot;

const lateNight = new Time(23, 59, 59);
console.log(lateNight.toString()); // &quot;23:59:59&quot;</code></pre>
<h2 id="인스턴스와-instanceof-연산자">인스턴스와 <code>instanceof</code> 연산자</h2>
<p>인스턴스: 생성자 함수를 통해 생성된 객체</p>
<p><strong><code>instanceof</code></strong> 연산자: 객체가 특정 생성자 함수로부터 만들어졌는지 확인 가능</p>
<p>예시: Person 생성자 함수로 만든 person1, person2은 모두 Person의 인스턴스</p>
<pre><code class="language-jsx">const person1 = new Person(&quot;윤지&quot;, 18);
const person2 = new Person(&quot;민수&quot;, 25);

console.log(person1 instanceof Person); // 출력: true
console.log(person2 instanceof Person); // 출력: true</code></pre>
<p>각 인스턴스는 생성자 함수에서 정의한 속성과 메서드를 가지며, <strong>서로 독립적인 객체</strong>임. 한 인스턴스의 변경이 다른 인스턴스에 영향을 미치지 않음</p>