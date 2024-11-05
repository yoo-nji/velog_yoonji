<p>JavaScript의 <code>Date</code> 객체는 날짜와 시간 데이터를 다루는 <strong>내장 객체</strong>. 다양한 메서드와 속성을 제공하여 날짜 처리를 도움. 실무에서는 주로 날짜 라이브러리를 사용하지만, 이를 잘 활용하려면 <code>Date</code> 객체의 기본을 이해해야 함.</p>
<hr />
<h2 id="1-date-객체-생성-방법">1. Date 객체 생성 방법</h2>
<p><strong><code>Date</code> 객체를 인스턴스로 생성하는 이유</strong></p>
<ul>
<li><strong>날짜와 시간 정보를 얻고 조작할 수 있는 다양한 메서드를 사용하기 위함</strong></li>
<li>인스턴스 생성 시 <code>getFullYear()</code>, <code>getMonth()</code> 같은 메서드에 접근하여 날짜와 시간을 손쉽게 다룰 수 있음</li>
</ul>
<pre><code class="language-jsx">const now = new Date();
console.log(now); // 현재 날짜와 시간 출력</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/c9305bd5-d898-4831-b167-0f5c2652de7e/image.png" /></p>
<h3 id="문제점">문제점</h3>
<p><code>Date</code> 객체로 생성한 날짜와 시간은 기본 포맷으로 표시되어 원하는 형태로 나타나지 않을 수 있음</p>
<p><strong>예상 결과</strong>: &quot;2024.11.04 12:15:32&quot;</p>
<h2 id="2-원하는-형식으로-날짜-포맷팅하기">2. 원하는 형식으로 날짜 포맷팅하기</h2>
<p><code>Date</code> 객체를 원하는 날짜 형식으로 표시: <strong>개별 값을 추출</strong>하여 조합. 예를 들어, 월과 일처럼 한 자리 숫자인 경우</p>
<ul>
<li><code>String()</code>을 사용하여 숫자를 명시적으로 문자열로 변환한 후(숫자는 앞에 0이 올 수 없음),</li>
<li>문자열 메서드인 <code>padStart()</code>를 적용</li>
</ul>
<pre><code class="language-jsx">const now = new Date();
const year = now.getFullYear();
const month = String(now.getMonth() + 1).padStart(2, '0');
const date = String(now.getDate()).padStart(2, '0');

const formattedDate = `${year}.${month}.${date}`;
console.log(formattedDate); // 예: &quot;2024.11.04&quot;</code></pre>
<p>이 코드는 현재 날짜를 &quot;YYYY.MM.DD&quot; 형식으로 포맷팅. padStart() 메서드를 사용하여 월과 일이 한 자리 숫자일 경우 앞에 0을 추가</p>
<h2 id="3-특정-날짜-및-시간-설정">3. 특정 날짜 및 시간 설정</h2>
<p><code>Date</code> 객체 생성 시 원하는 날짜와 시간 지정 가능. 인수로 연도, 월, 일 등을 지정하면, 시간과 분은 자동으로 0으로 초기화됨</p>
<pre><code class="language-jsx">const specificDate = new Date(2024, 10, 4); // 2024년 11월 4일 (월은 0부터 시작)
const dayOfWeek = specificDate.getDay();

const days = ['일', '월', '화', '수', '목', '금', '토'];
console.log(`2024년 11월 4일은 ${days[dayOfWeek]}요일임`);
// 출력: &quot;2024년 11월 4일은 월요일임&quot;</code></pre>
<ul>
<li>getDay() 메서드를 사용하여 해당 날짜의 요일 정보를 얻음</li>
<li>미리 정의된 요일 배열을 통해 숫자를 해당하는 요일 문자열로 변환</li>
<li>변환된 요일 문자열을 포함하여 결과를 출력</li>
</ul>
<h2 id="4-날짜와-시간-가져오기">4. 날짜와 시간 가져오기</h2>
<p><code>Date</code> 객체는 날짜와 시간 정보를 <strong>가져오는 메서드</strong>와 <strong>설정하는 메서드</strong>를 제공</p>
<p>이름이 <code>get</code>으로 시작하는 메서드는 정보를 가져옴</p>
<p><code>set</code>으로 시작하는 메서드는 값을 설정</p>
<h3 id="주요-get-메서드">주요 <code>get</code> 메서드</h3>
<ul>
<li><strong>연도</strong>: <code>getFullYear()</code></li>
<li><strong>월</strong>: <code>getMonth()</code> (0부터 시작)</li>
<li><strong>날짜</strong>: <code>getDate()</code></li>
</ul>
<pre><code class="language-jsx">const now = new Date();
const year = now.getFullYear();
const month = now.getMonth() + 1;
const day = now.getDate();

console.log(`${year}.${String(month).padStart(2, '0')}.${String(day).padStart(2, '0')}`);</code></pre>
<ul>
<li><strong>시간, 분, 초</strong>: <code>getHours()</code>, <code>getMinutes()</code>, <code>getSeconds()</code></li>
</ul>
<pre><code class="language-jsx">const hours = now.getHours();
const minutes = now.getMinutes();
const seconds = now.getSeconds();

console.log(hours);   // 예: 12 (현재 시)
console.log(minutes); // 예: 30 (현재 분)
console.log(seconds); // 예: 45 (현재 초)

// 시간, 분, 초를 모두 포함한 형식으로 출력
const formattedTime = `${String(hours).padStart(2, '0')}:${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
console.log(formattedTime); // 예: &quot;12:30:45&quot;</code></pre>
<h2 id="5-요일-가져오기">5. 요일 가져오기</h2>
<p><code>getDay()</code> 메서드는 일요일(0)부터 토요일(6)까지 요일을 숫자로 반환. 이를 문자열로 변환하려면 배열 사용</p>
<pre><code class="language-jsx">const days = ['일', '월', '화', '수', '목', '금', '토'];
console.log(days[now.getDay()] + '요일'); // 현재 요일 출력</code></pre>
<h2 id="6-tolocalestring을-활용한-날짜와-시간-포맷팅">6. toLocaleString()을 활용한 날짜와 시간 포맷팅</h2>
<p><code>toLocaleString()</code> 메서드로 날짜와 시간을 현지화된 형식으로 표시 가능</p>
<pre><code class="language-jsx">const date = new Date();
console.log(date.toLocaleString('ko-KR')); // 예: &quot;2024. 11. 4. 오후 12:48:00&quot;</code></pre>
<p><strong>옵션 사용 예시</strong></p>
<pre><code class="language-jsx">const options = { year: 'numeric', month: '2-digit', day: '2-digit', hour: '2-digit', minute: '2-digit', second: '2-digit' };
console.log(date.toLocaleString('ko-KR', options)); // 예: &quot;2024.11.04 12:48:00&quot;</code></pre>
<h2 id="7-날짜-설정">7. 날짜 설정</h2>
<p><code>Date</code> 객체의 특정 구성 요소 변경 시 <strong>set 메서드</strong> 사용. 기존 <code>Date</code> 객체의 시분초는 유지되면서 날짜나 시간만 변경됨</p>
<h3 id="주요-set-메서드">주요 <code>set</code> 메서드</h3>
<ul>
<li><strong>연도 설정</strong>: <code>setFullYear(year)</code></li>
<li><strong>월 설정</strong>: <code>setMonth(month)</code> (0부터 시작)</li>
<li><strong>일 설정</strong>: <code>setDate(date)</code></li>
<li><strong>시간, 분, 초 설정</strong>: <code>setHours(hours)</code>, <code>setMinutes(minutes)</code>, <code>setSeconds(seconds)</code></li>
</ul>
<pre><code class="language-jsx">const date = new Date();

// 연도를 2025로 설정
date.setFullYear(2025);

// 월을 6월(5)로 설정
date.setMonth(5);

// 일을 15일로 설정
date.setDate(15);

// 시간을 14시 30분 0초로 설정
date.setHours(14, 30, 0);

console.log(date); // 2025-06-15T14:30:00 (정확한 출력은 시스템 시간대에 따라 다를 수 있음)</code></pre>
<p>이러한 set 메서드들로 Date 객체의 특정 구성 요소를 원하는 값으로 변경 가능. 특정 날짜나 시간 설정, 날짜 계산 수행 시 유용함</p>
<h3 id="⚠️-날짜-계산-시-주의점">⚠️ 날짜 계산 시 주의점</h3>
<p>6일 뒤의 날짜 계산 시 <code>getDate() + 6</code>을 바로 사용하면 월을 넘어설 때 오류 발생 가능. 이때는 <code>setDate()</code> 사용이 안전함</p>
<pre><code class="language-jsx">const date = new Date(); // 현재 날짜
console.log(date); // 예: Mon Nov 04 2024 12:46:00 GMT+0900 (한국 표준시)

// 6일 후의 날짜 계산
date.setDate(date.getDate() + 6);
console.log(date); // 예: Sun Nov 10 2024 12:46:00 GMT+0900 (한국 표준시)</code></pre>
<h2 id="8-날짜-연산-예제">8. 날짜 연산 예제</h2>
<h3 id="날짜-간격-계산">날짜 간격 계산</h3>
<p>두 날짜 간의 간격 계산 시 밀리초로 계산된 값을 사용하여 일 단위로 변환 가능</p>
<pre><code class="language-jsx">const startDate = new Date('2024-10-30');
const endDate = new Date('2024-11-30');
const diffTime = endDate - startDate; // 밀리초 단위
const diffDays = diffTime / (1000 * 60 * 60 * 24); // 일 수로 변환
console.log(Math.ceil(diffDays)); // 두 날짜 사이의 일 수</code></pre>
<p>Math.ceil() 사용 이유: 부분적인 날짜를 완전한 하루로 계산하기 위함. 예를 들어, 실제 차이가 30.1일이라면 31일로 올림하여 계산. 이 코드의 출력값은 31임</p>
<h3 id="그-달의-마지막-일-구하기">그 달의 마지막 일 구하기</h3>
<p>그 달의 마지막 일 구할 때는 <strong>다음 달의 첫 번째 날에서 하루를 빼는 방법</strong> 사용. 이때 <code>0</code>을 <code>Date</code> 객체의 일(day)로 지정하면 자동으로 전달의 마지막 날이 됨</p>
<pre><code class="language-jsx">// 11월의 마지막 날 구하기
const lastDayOfMonth = new Date(2024, 11, 0); // 11은 12월을 의미, 0은 전달의 마지막 날
console.log(lastDayOfMonth.getDate()); // 30 (2024년 11월의 마지막 날)</code></pre>
<h2 id="8-날짜-라이브러리">8. 날짜 라이브러리</h2>
<p>실제 프로젝트에서는 <code>Date</code> 객체만으로 날짜 처리가 어려워 주로 라이브러리 사용. </p>
<p><code>moment</code>나 <code>date-fns</code> 같은 라이브러리는 다양한 포맷팅과 날짜 계산 기능을 제공하여 더욱 편리함</p>
<ul>
<li><a href="https://momentjs.com/">moment.js</a></li>
<li><a href="https://date-fns.org/">date-fns</a> ✅</li>
</ul>
<blockquote>
<p>📚 자세한 내용은 <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date">MDN Date 객체 문서</a>를 참고</p>
</blockquote>