<p><strong><code>브라우저 저장소란?</code></strong></p>
<p>웹 브라우저에서 데이터를 임시로 저장할 수 있는 공간</p>
<h2 id="1-cookie"><strong>1. Cookie</strong></h2>
<p><strong>특징</strong>:</p>
<ul>
<li><strong>HTTP 요청 시 자동으로 서버에 전송</strong>되어 클라이언트와 서버 간 통신에 활용됨</li>
<li>서버가 쿠키를 통해 사용자 식별 및 세션 유지 가능</li>
<li><strong>용량 제한</strong>: 약 4KB</li>
<li><strong>만료 기간</strong>: 설정 가능하며, 지정한 기간 경과 시 자동 삭제</li>
</ul>
<p><strong>장점</strong>:</p>
<ul>
<li>서버와 클라이언트 간 정보 공유로 <strong>로그인 상태 유지</strong>와 <strong>사용자 맞춤 정보 제공</strong>에 유용</li>
</ul>
<p><strong>단점</strong>:</p>
<ul>
<li>용량이 매우 제한적임 (4KB)</li>
<li>HTTP 요청마다 쿠키가 포함되어 네트워크 트래픽 증가 가능</li>
</ul>
<blockquote>
<p><strong>💡 왜 문제가 될까?</strong></p>
<ul>
<li><strong>쿠키의 용량 제한</strong>은 약 4KB이나, 모든 요청마다 전송되어 <strong>빈번한 요청</strong> 발생 시 네트워크 속도에 영향을 미칠 수 있음</li>
</ul>
</blockquote>
<p><strong>사용 예시</strong>:</p>
<ul>
<li><strong>광고 차단</strong>: &quot;7일간 보지 않기&quot; 정보 저장 (쿠키 만료 기간으로 설정)</li>
<li><strong>세션 유지</strong>: 로그인 상태 유지 및 인증 정보 서버 전달</li>
</ul>
<hr />
<h2 id="2-localstorage와-sessionstorage-소개"><strong>2. LocalStorage와 SessionStorage 소개</strong></h2>
<p>HTML5에서는 브라우저에 데이터를 저장하기 위한 <strong>LocalStorage</strong>와 <strong>SessionStorage</strong> API를 제공함</p>
<p>이들은 <strong>클라이언트 측에서만</strong> 데이터를 저장하고, 서버와 통신하지 않는다는 점에서 쿠키와 다름</p>
<p>둘의 차이는 <strong>데이터의 소멸 시점</strong>에 있음:</p>
<ul>
<li><strong>LocalStorage</strong>: 브라우저를 닫아도 데이터 유지됨</li>
<li><strong>SessionStorage</strong>: 현재 탭(세션)이 닫히면 데이터 삭제됨</li>
</ul>
<hr />
<h3 id="21-localstorage"><strong>2.1 LocalStorage</strong></h3>
<p><strong>특징</strong>:</p>
<ul>
<li>데이터를 <strong>도메인별</strong>로 저장하며, 같은 도메인 내의 모든 탭과 공유됨</li>
<li>사용자가 명시적으로 삭제하기 전까지 데이터 유지됨</li>
<li><strong>저장 용량</strong>: 약 5MB</li>
</ul>
<p><strong>장점</strong>:</p>
<ul>
<li>장기적 데이터 저장에 적합함</li>
<li>인증 토큰이나 사용자 설정 등 서버와 관련 없는 데이터 관리에 유용함</li>
</ul>
<p><strong>보안 주의</strong></p>
<ul>
<li>사용자가 브라우저 개발자 도구로 쉽게 접근할 수 있어서 민감한 데이터(ex. 비밀번호)를 로컬스토리지에 저장 시 보안 취약점 발생 가능함</li>
</ul>
<p>아래 이미지처럼 크롬 개발자모드에서 로컬스토리지에 저장된 데이터를 확인할 수 있다<br /><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/1d8fd6a6-e932-47d5-bbcf-f7efe13b7448/image.png" /></p>
<p><strong>사용 예시</strong>:</p>
<ul>
<li><strong>자동 로그인</strong></li>
</ul>
<hr />
<h3 id="22-sessionstorage"><strong>2.2 SessionStorage</strong></h3>
<p><strong>특징</strong>:</p>
<ul>
<li><strong>현재 탭에서만 유효</strong>하며, 다른 탭이나 창과 데이터 공유 불가</li>
<li>탭 종료 시 데이터 삭제</li>
<li><strong>저장 용량</strong>: 약 5MB</li>
</ul>
<p><strong>장점</strong>:</p>
<ul>
<li>세션(탭) 동안만 필요한 데이터 저장에 유용</li>
<li>각 탭이 독립적으로 데이터를 관리하여 안전</li>
</ul>
<p><strong>사용 예시</strong>:</p>
<ul>
<li><strong>폼 데이터 임시 저장</strong></li>
</ul>
<hr />
<h2 id="localstorage-sessionstorage-cookie-비교"><strong>LocalStorage, SessionStorage, Cookie 비교</strong></h2>
<table>
<thead>
<tr>
<th><strong>항목</strong></th>
<th><strong>LocalStorage</strong></th>
<th><strong>SessionStorage</strong></th>
<th><strong>Cookie</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>유지 기간</strong></td>
<td>영구적</td>
<td>탭 종료 시까지</td>
<td>만료 기간 설정 가능</td>
</tr>
<tr>
<td><strong>데이터 접근</strong></td>
<td>클라이언트 측</td>
<td>클라이언트 측</td>
<td>클라이언트와 서버 모두</td>
</tr>
<tr>
<td><strong>저장 용량</strong></td>
<td>약 5MB</td>
<td>약 5MB</td>
<td>약 4KB</td>
</tr>
<tr>
<td><strong>HTTP 요청 포함 여부</strong></td>
<td>미포함</td>
<td>미포함</td>
<td>HTTP 요청 시 자동 전송</td>
</tr>
<tr>
<td><strong>사용 목적</strong></td>
<td>장기 데이터 저장</td>
<td>일시적 데이터 저장</td>
<td>서버와 클라이언트 간 데이터 교환</td>
</tr>
<tr>
<td><strong>주요 사용 용도</strong></td>
<td>자동 로그인, 사용자 설정</td>
<td>폼 임시 저장, 페이지 상태</td>
<td>인증 정보, 광고 차단, 팝업 상태 유지</td>
</tr>
</tbody></table>
<hr />
<h2 id="선택-기준"><strong>선택 기준</strong></h2>
<ul>
<li><strong>Cookie</strong>:서버와 클라이언트 간 데이터 교환 필요 시<ul>
<li>사용예: 로그인 세션 유지, 사용자 맞춤 광고</li>
</ul>
</li>
<li><strong>LocalStorage</strong>:서버와 관계없이 데이터를 브라우저에 영구적<ul>
<li>저장예: 인증 토큰 저장, 사용자 인터페이스 설정</li>
</ul>
</li>
<li><strong>SessionStorage</strong>:브라우저 탭 실행 중 필요한 데이터<ul>
<li>저장예: 임시 폼 데이터 저장, 세션 기반 작업</li>
</ul>
</li>
</ul>
<blockquote>
<p>참고: <a href="https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-localStorage-sessionStorage">https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-localStorage-sessionStorage</a></p>
</blockquote>