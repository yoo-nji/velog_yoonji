<h1 id="git--github-특강">Git &amp; Github 특강</h1>
<blockquote>
<p>강사: 김동영 강사님
일시: 2024년 11월 12일 14:00 - 18:00(4시간)</p>
</blockquote>
<h2 id="git-사용-이유">Git 사용 이유</h2>
<ul>
<li><strong>Git</strong>: 버전 관리 시스템(VCS)으로, 파일의 변경 이력 기록 및 필요 시 되돌리기 가능한 소프트웨어</li>
</ul>
<h3 id="버전-관리의-필요성">버전 관리의 필요성</h3>
<ul>
<li><strong>변경 사항 기록</strong>: 누가, 언제, 무엇을 수정했는지 기록</li>
<li><strong>이유 명시</strong>: 커밋 메시지를 통해 수정의 의도 표현</li>
<li><strong>과거로 돌아가기</strong>: 특정 시점으로 되돌리기 가능, 추적 가능한 변경 내역 유지</li>
</ul>
<hr />
<h2 id="터미널-명령어-요약">터미널 명령어 요약</h2>
<table>
<thead>
<tr>
<th>명령어</th>
<th>설명</th>
<th>사용 예시</th>
</tr>
</thead>
<tbody><tr>
<td><strong>pwd</strong></td>
<td>현재 작업 중인 디렉토리 경로 확인</td>
<td><code>pwd</code></td>
</tr>
<tr>
<td><strong>ls</strong></td>
<td>현재 디렉토리 내 파일/폴더 목록 조회</td>
<td><code>ls -l</code>,<code>ls -a</code>,<code>ls -h</code></td>
</tr>
<tr>
<td><strong>mkdir</strong></td>
<td>새로운 디렉토리 생성</td>
<td><code>mkdir 디렉토리_이름</code></td>
</tr>
<tr>
<td><strong>cd</strong></td>
<td>특정 디렉토리로 이동</td>
<td><code>cd [디렉토리_경로]</code></td>
</tr>
</tbody></table>
<h2 id="git-설정-및-초기화">Git 설정 및 초기화</h2>
<h3 id="설치-및-초기-설정">설치 및 초기 설정</h3>
<ol>
<li><p><strong>설치</strong>: <a href="https://git-scm.com/">Git 다운로드 페이지</a>에서 설치</p>
</li>
<li><p><strong>초기 설정</strong>:</p>
<pre><code class="language-bash"> git config --global user.name &quot;Your Name&quot;
 git config --global user.email &quot;your.email@example.com&quot;</code></pre>
<ul>
<li><strong>설정 확인</strong>: <code>git config --global --list</code></li>
</ul>
</li>
</ol>
<h2 id="깃-명령어">깃 명령어</h2>
<p>Git의 모든 사용 가능한 명령어 목록</p>
<pre><code class="language-bash">git help -a</code></pre>
<h2 id="주요-git-명령어-요약">주요 Git 명령어 요약</h2>
<table>
<thead>
<tr>
<th>명령어</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>git init</strong></td>
<td>새 Git 저장소 초기화</td>
</tr>
<tr>
<td><strong>git status</strong></td>
<td>저장소 상태 확인</td>
</tr>
<tr>
<td><strong>git clone</strong></td>
<td>원격 저장소를 로컬로 복사</td>
</tr>
<tr>
<td><strong>git add</strong></td>
<td>변경사항 스테이징 영역에 추가</td>
</tr>
<tr>
<td><strong>git commit</strong></td>
<td>스테이징된 변경사항을 저장소에 기록</td>
</tr>
<tr>
<td><strong>git branch</strong></td>
<td>브랜치 생성/삭제/조회</td>
</tr>
<tr>
<td><strong>git switch</strong></td>
<td>브랜치 전환</td>
</tr>
<tr>
<td><strong>git reset</strong></td>
<td>커밋 되돌리기/스테이징 영역 리셋</td>
</tr>
<tr>
<td><strong>git push</strong></td>
<td>로컬 변경사항을 원격에 업로드</td>
</tr>
<tr>
<td><strong>git pull</strong></td>
<td>원격 변경사항을 가져와 병합</td>
</tr>
<tr>
<td><strong>git merge</strong></td>
<td>브랜치 병합</td>
</tr>
<tr>
<td><strong>git revert</strong></td>
<td>특정 커밋을 되돌리는 새로운 커밋 생성</td>
</tr>
</tbody></table>
<h2 id="github와-버전-관리-시스템">GitHub와 버전 관리 시스템</h2>
<h3 id="vcs-종류-비교">VCS 종류 비교</h3>
<ul>
<li><strong>중앙집중식 VCS</strong>:<ul>
<li>단일 중앙 저장소에 버전 정보 저장</li>
<li>예: SVN</li>
</ul>
</li>
<li><strong>분산 VCS (예: Git)</strong>:<ul>
<li>각 개발자가 전체 저장소의 복사본을 로컬에 보유</li>
<li><strong>장점</strong>: 오프라인 작업 가능, 빠르고 유연한 협업 가능</li>
</ul>
</li>
</ul>
<h3 id="git-log">git log</h3>
<p>git log 명령어: 커밋 히스토리 조회에 사용</p>
<pre><code class="language-bash">git log [옵션]</code></pre>
<p>주요 옵션:</p>
<ul>
<li>--oneline: 각 커밋을 한 줄로 요약하여 표시</li>
<li>--graph: 브랜치와 병합 히스토리를 아스키 그래프로 표시</li>
<li>--author=[이름]: 특정 작성자의 커밋만 표시</li>
<li>--since, --after: 특정 날짜 이후의 커밋만 표시</li>
<li>--until, --before: 특정 날짜 이전의 커밋만 표시</li>
</ul>
<p>예시:</p>
<pre><code class="language-bash">git log --oneline</code></pre>
<h3 id="git-show">git show</h3>
<p>git show 명령어: 특정 커밋의 상세 정보 표시</p>
<pre><code class="language-bash">git show [옵션] [커밋 해시]</code></pre>
<p>주요 기능:</p>
<ul>
<li>특정 커밋의 메타데이터(작성자, 날짜, 메시지 등) 표시</li>
<li>해당 커밋에서 변경된 파일 내용 확인</li>
<li>커밋 간의 차이점 확인</li>
</ul>
<p>예시:</p>
<pre><code class="language-bash">git show abc123</code></pre>
<h2 id="branch">Branch</h2>
<p>작업의 분기점</p>
<p>브랜치 생성</p>
<pre><code class="language-bash">git branch [브랜치명]</code></pre>
<p>브랜치 목록 확인</p>
<pre><code class="language-bash">git branch</code></pre>
<p>브랜치 전환</p>
<pre><code class="language-bash">git switch [브랜치명]
# 또는
git restore [브랜치명]</code></pre>
<p>브랜치 생성 및 전환</p>
<pre><code class="language-bash">git switch -c [브랜치명]
# 또는
git restore -c [브랜치명]</code></pre>
<p>브랜치 삭제</p>
<pre><code class="language-bash">git branch -d [브랜치명]</code></pre>
<p>브랜치 병합</p>
<pre><code class="language-bash">git merge [브랜치명]</code></pre>
<h3 id="conflict충돌">Conflict(충돌)</h3>
<pre><code class="language-dart"># 병합 중 충돌 발생 시, 충돌 해결 후
git add [충돌_해결된_파일]
git commit -m &quot;Merge branch 'feature'&quot;</code></pre>
<h2 id="merge-vs-rebase">Merge vs Rebase</h2>
<h3 id="merge">Merge</h3>
<ul>
<li><p><strong>기능</strong>: 병합할 브랜치의 변경 사항을 현재 브랜치에 통합</p>
<pre><code class="language-bash">  git merge branch_name</code></pre>
</li>
</ul>
<h3 id="rebase">Rebase</h3>
<ul>
<li><p><strong>기능</strong>: 브랜치의 시작점을 재설정하여 깔끔한 커밋 히스토리 생성</p>
<pre><code class="language-bash">  git rebase main</code></pre>
</li>
<li><p><strong>주의</strong>: 공개 저장소에 푸시된 커밋 리베이스 시 협업에 문제 발생 가능성 있음</p>
</li>
</ul>
<h2 id="git-되돌리기">Git 되돌리기</h2>
<h3 id="revert">Revert</h3>
<ul>
<li><p><strong>기능</strong>: 특정 커밋의 변경사항을 취소하는 새로운 커밋 생성</p>
<pre><code class="language-bash">  git revert commit_hash</code></pre>
</li>
<li><p><strong>장점</strong>: 히스토리 유지 및 협업 시 안전하게 사용 가능</p>
</li>
</ul>
<h3 id="reset">Reset</h3>
<ul>
<li><p><strong>기능</strong>: 커밋 기록을 되돌리거나 작업 디렉토리 상태를 되돌림</p>
<pre><code class="language-bash">  git reset --hard commit_hash</code></pre>
</li>
<li><p><strong>옵션</strong>:</p>
<ul>
<li><code>-soft</code>: 인덱스와 작업 디렉토리를 그대로 둔 채 HEAD 이동</li>
<li><code>-mixed</code>: HEAD와 인덱스 이동, 작업 디렉토리는 그대로</li>
<li><code>-hard</code>: HEAD, 인덱스, 작업 디렉토리 모두 리셋</li>
</ul>
</li>
</ul>
<h2 id="💬-마치며">💬 마치며</h2>
<p>데브코스 하면서 들은 첫 특강이었다 깃허브를 평소에 사용하긴 했지만 vscode 소스제어 이용해서 주로 사용하였는데 다양한 터미널 명령어를 배울 수 있었다
그리고 깃충돌도 평소에 해결해 볼 일이 없었는데 이번 특강을 통해서 체험?해 보았다 👍</p>
<p>프로젝트 시작되고 복습은 거의 못하고 있는 중... 이번 주말 잘 활용해 보자</p>