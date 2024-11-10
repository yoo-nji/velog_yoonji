<h2 id="📍-문제">📍 문제</h2>
<h3 id="캘린더-구현">캘린더 구현</h3>
<p><strong>설명</strong>: 현재 날짜를 기반으로 간단한 캘린더를 표시합니다.</p>
<p>힌트: innerHTML, 테이블 태그를 문자열로 조합해서 만들면됨</p>
<p><strong>기본 제공 코드</strong>:</p>
<pre><code class="language-html">&lt;div id=&quot;calendar&quot;&gt;&lt;/div&gt;
&lt;button id=&quot;generateCalendarButton&quot;&gt;캘린더 생성&lt;/button&gt;
</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/fd54b871-1469-4610-bc08-dea6b707ba95/image.png" /></p>
<h2 id="🥔-내-코드">🥔 내 코드</h2>
<p>1차 실패 ❌</p>
<pre><code class="language-jsx">  // 현재 날짜 정보
  const now = new Date();
  // console.log(now);

  // 현재 정보(연도, 달, 일) 변수에 저장
  const year = now.getFullYear();
  const month = now.getMonth() + 1;
  const day = now.getDate();

  // 요일 구하기
  const days = ['일', '월', '화', '수', '목', '금', '토'];
  console.log(typeof days[now.getDay()]);

  //마지막 일 구하기
  const lastDay = new Date(year, month - 1, 0).getDate();
  console.log(lastDay); //31

  //캘린더에 활용할 새로운 Date 객체 복사
  const calenderDate = new Date(now);

  //캘린더 그리는 함수
  function makeCalendar() {
    const calendarCon = document.querySelector('#calendar');
    calendarCon.innerHTML = &quot;&quot;; //초기화
    let calendarInner = `
    &lt;table&gt;
    &lt;tr&gt;
      &lt;th&gt;일&lt;/th&gt;
      &lt;th&gt;월&lt;/th&gt;
      &lt;th&gt;화&lt;/th&gt;
      &lt;th&gt;수&lt;/th&gt;
      &lt;th&gt;목&lt;/th&gt;
      &lt;th&gt;금&lt;/th&gt;
      &lt;th&gt;토&lt;/th&gt;
    &lt;/tr&gt;`;

    // 1일 요일 인덱스 
    const firstDayIndex = new Date(year, month - 1, 1).getDay();

    //캘린더 그리기
    //1일부터 시작(초기값)
    let day = 1;

    calenderDate.setDate(day);
    // console.log(calenderDate);

    //첫줄 빈칸 + 날짜 채우기
    calendarInner += `&lt;tr&gt;`;
    //첫줄 생성 7번 반복
    for (let i = 0; i &lt; 7; i++) {
      if (i &lt; firstDayIndex) {
        calendarInner += ` &lt;td&gt; &lt;/td&gt;`;
      } else {
        calendarInner += ` &lt;td&gt;${day}&lt;/td&gt;`;
      }
      day++;
    }
    calendarInner += `&lt;/tr&gt;`;
    console.log(day);

    // 남은 날짜 채우기
    while (day &lt;= lastDay) {
      calendarInner += `&lt;tr&gt;`;
      for (let i = 0; i &lt; 7; i++) {
        if (day &gt; lastDay) { // 31일보다 크면 빈칸 
          calendarInner += `&lt;td&gt; &lt;/td&gt;`;
          day++;
        } else {
          calendarInner += `&lt;td&gt;${day}&lt;/td&gt;`;
          day++;
        }
      }
      calendarInner += `&lt;/tr&gt;`;
    }
    calendarInner += `&lt;/table&gt;`;

    console.log(calendarInner);
    calendarCon.innerHTML = calendarInner; //그리기
  }

  //버튼 클릭시 캘린더 만들기
  const btnEl = document.querySelector('#generateCalendarButton');
  btnEl.addEventListener('click', makeCalendar);</code></pre>
<p><strong>풀이</strong></p>
<ol>
<li>현재 날짜 정보 가져오기<ul>
<li>현재 연도, 월, 일 저장</li>
</ul>
</li>
<li>해당 월의 마지막 날짜 계산</li>
<li>캘린더 그리기 함수 (makeCalendar) 구현<ul>
<li>while 문으로 초기값 1(일)에서 마지막 값(날짜) 까지 반복해서 요소를 추가함</li>
<li>1일의 요일 인덱스 계산</li>
<li>첫 주 생성 (빈 칸 + 날짜) - 1일 인덱스로 빈칸 수 계산</li>
<li>for문으로 한 줄에 들어갈 7번의 <td> 태그 생성 후 <tr>로 감싸기</li>
<li>남은 날짜 채우기(날짜보다 크면 빈칸 처리)</li>
<li>완성된 캘린더 HTML을 페이지에 삽입</li>
</ul>
</li>
<li>버튼 클릭 이벤트에 캘린더 생성 함수 연결</li>
</ol>
<p><strong>문제점(강사님 피드백)</strong></p>
<ol>
<li>현재 정보를 변수로 저장해 이후 Date 객체의 매개변수로 사용할 경우, month 값에 1을 더하지 않아야 한다. ⇒ Date 객체는 월을 0부터 11로 표현하기 때문이다.
<img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/0c46f26e-7503-4cab-8353-dce8d2dcfb8f/image.png" /></li>
</ol>
<pre><code class="language-jsx"> // 현재 정보(연도, 달, 일) 변수에 저장
  const year = now.getFullYear();
  const month = now.getMonth() + 1;
  const day = now.getDate();</code></pre>
<ol>
<li><p>변수 day는 if 조건이 성립하지 않았을 때만 증가(++)해야 한다.</p>
<p> ⇒ 달력 첫 줄에서 1일의 요일과 일치하는 인덱스를 찾을 때까지는 빈칸으로 두어야 하기 때문이다.</p>
</li>
</ol>
<pre><code class="language-jsx">   //첫줄 생성 7번 반복
    for (let i = 0; i &lt; 7; i++) {
      if (i &lt; firstDayIndex) {
        calendarInner += ` &lt;td&gt; &lt;/td&gt;`;
      } else {
        calendarInner += ` &lt;td&gt;${day}&lt;/td&gt;`;
      }
      day++;
    }</code></pre>
<p>2차 성공 ✅</p>
<pre><code class="language-jsx">    // 현재 날짜 정보
  const now = new Date();
  // console.log(now);

  // 현재 정보(연도, 달, 일) 변수에 저장
  const year = now.getFullYear();
  const month = now.getMonth();
  const day = now.getDate();

  // 요일 구하기
  const days = ['일', '월', '화', '수', '목', '금', '토'];
  console.log(typeof days[now.getDay()]);

  //마지막 일 구하기
  const lastDay = new Date(year, month - 1, 0).getDate();
  console.log(lastDay); //31

  //캘린더에 활용할 새로운 Date 객체 복사
  const calenderDate = new Date(now);

  //캘린더 그리는 함수
  function makeCalendar() {
    const calendarCon = document.querySelector('#calendar');
    calendarCon.innerHTML = ''; //초기화
    let calendarInner = `
    &lt;table&gt;
    &lt;tr&gt;
      &lt;th&gt;일&lt;/th&gt;
      &lt;th&gt;월&lt;/th&gt;
      &lt;th&gt;화&lt;/th&gt;
      &lt;th&gt;수&lt;/th&gt;
      &lt;th&gt;목&lt;/th&gt;
      &lt;th&gt;금&lt;/th&gt;
      &lt;th&gt;토&lt;/th&gt;
    &lt;/tr&gt;`;

    // 1일 요일 인덱스
    const firstDayIndex = new Date(year, month, 1).getDay();

    //캘린더 그리기
    //1일부터 시작(초기값)
    let day = 1;

    calenderDate.setDate(day);
    // console.log(calenderDate);

    //첫줄 빈칸 + 날짜 채우기
    calendarInner += `&lt;tr&gt;`;
    //첫줄 생성 7번 반복
    for (let i = 0; i &lt; 7; i++) {
      if (i &lt; firstDayIndex) {
        calendarInner += ` &lt;td&gt; &lt;/td&gt;`;
      } else {
        calendarInner += ` &lt;td&gt;${day}&lt;/td&gt;`;
        day++;
      }
    }
    calendarInner += `&lt;/tr&gt;`;
    console.log(day);

    // 남은 날짜 채우기
    while (day &lt;= lastDay) {
      calendarInner += `&lt;tr&gt;`;
      for (let i = 0; i &lt; 7; i++) {
        if (day &gt; lastDay) {
          // 31일보다 크면 빈칸
          calendarInner += `&lt;td&gt; &lt;/td&gt;`;
          day++;
        } else {
          calendarInner += `&lt;td&gt;${day}&lt;/td&gt;`;
          day++;
        }
      }
      calendarInner += `&lt;/tr&gt;`;
    }
    calendarInner += `&lt;/table&gt;`;

    console.log(calendarInner);
    calendarCon.innerHTML = calendarInner; //그리기
  }

  //버튼 클릭시 캘린더 만들기
  const btnEl = document.querySelector('#generateCalendarButton');
  btnEl.addEventListener('click', makeCalendar);</code></pre>
<h2 id="💬-마치며">💬 마치며</h2>
<p>아마 여태 풀었던 문제 중 가장 오래 걸렸고 가장 긴 로직일 것 같다!  누군가에겐 작고 초라한 코드겠지만… 난 너무 뿌듯함 ✨ Date 객체랑 테이블태그가 익숙하지 않아서 몇가지 개념을 참고해서 풀었다. 온전한 내 힘은 아니었지만… 로직 자체를 만들어 낼 수 있었다는 거에 의미를 둬야지 🐌</p>