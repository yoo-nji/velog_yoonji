<h2 id="📚-til">📚 TIL</h2>
<p>동기 비동기, 콜백함수
Promise
fatch</p>
<h2 id="💡-git-추가-수업-진행">💡 Git 추가 수업 진행</h2>
<ol>
<li><p>초기 준비 단계</p>
<ul>
<li>GitHub 회원가입: GitHub 공식 웹사이트에서 계정 생성</li>
<li>Git 설치: 운영 체제에 맞는 Git 클라이언트 다운로드 및 설치</li>
<li>Git 기본 설정: 사용자 이름과 이메일 주소 설정</li>
</ul>
</li>
<li><p>새 폴더 생성</p>
</li>
<li><p>Git 저장소 초기화: <code>git init</code> 명령어 입력 (이 폴더를 Git으로 관리하겠다는 의미)</p>
</li>
<li><p>.git 폴더 확인: <code>ls -la</code> 명령어로 .git 폴더 생성 확인</p>
</li>
<li><p>파일 업데이트 후 우측 아이콘에 1 표시 확인</p>
</li>
<li><p><code>git status</code> 입력</p>
<ol>
<li>untracked: 추적되지 않은 상태</li>
<li>tracked: 추적된 상태 (Git 커밋 준비 완료)</li>
</ol>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/68fcb11b-b1c4-43a8-8e0c-8cd26920e17d/image.png" /></p>
</li>
</ol>
<ol start="7">
<li>파일을 추적 상태로 등록하기<ol>
<li>VS Code 소스 컨트롤에서 &quot;+&quot; 버튼으로 추가, &quot;-&quot; 버튼으로 제거 (Shift 키로 다중 선택 가능)</li>
<li>터미널에서 <code>git add index.html</code>(파일 추가) 또는 <code>git rm --cached index.html</code>(추적 제거)<ol>
<li>✅ 모든 파일 추가: <code>git add .</code></li>
</ol>
</li>
</ol>
</li>
</ol>
<p><img alt="" src="https://velog.velcdn.com/images/yoon_ji/post/2c19c50a-912a-4108-b495-553719ac528a/image.png" /></p>
<ol start="8">
<li>Git 사용자 정보 등록<ol>
<li>사용자 이름 설정: <code>git config --global user.name &quot;Your Name&quot;</code></li>
<li>사용자 이메일 설정: <code>git config --global user.email &quot;youremail@example.com&quot;</code></li>
<li>주의: 이메일은 GitHub에 등록된 이메일과 일치해야 합니다.</li>
<li>설정된 사용자 정보 확인: <code>git config --list</code></li>
</ol>
</li>
<li>변경 사항 커밋하기<ol>
<li>터미널에서 <code>git commit -m &quot;커밋 메시지&quot;</code> 입력</li>
<li>커밋 메시지는 변경 사항을 간단히 설명하는 내용으로 작성 (예: <code>git commit -m &quot;초기 파일 추가&quot;</code>)</li>
</ol>
</li>
</ol>
<h3 id="github-저장소-생성">GitHub 저장소 생성</h3>
<ol>
<li>GitHub 웹사이트에 로그인</li>
<li>우측 상단의 '+' 버튼 클릭 후 'New repository' 선택</li>
<li>저장소 이름, 설명 입력 및 공개/비공개 설정</li>
<li>'Create repository' 버튼 클릭하여 저장소 생성</li>
<li>GitHub와 로컬 저장소 연결하기<ul>
<li>HTTPS 방식: GitHub 저장소 URL을 사용하여 연결
<code>git remote add origin https://github.com/username/repository.git</code></li>
<li>SSH 방식: SSH 키를 생성하고 GitHub 계정에 등록 후 연결
<code>git remote add origin git@github.com:username/repository.git</code></li>
</ul>
</li>
<li>원격 저장소로 푸시하기<ul>
<li>최초 푸시 시: <code>git push -u origin main</code></li>
<li>이후 푸시: <code>git push</code></li>
</ul>
</li>
</ol>
<p><strong>HTTPS와 SSH의 주요 차이점:</strong></p>
<ul>
<li>HTTPS: 사용하기 쉽지만 매번 인증 필요</li>
<li>SSH: 초기 설정이 복잡하지만 이후 인증 없이 사용 가능, 더 안전한 방식</li>
</ul>
<h3 id="ssh-키-생성">SSH 키 생성</h3>
<pre><code class="language-bash">cd ~/.ssh 
ssh-keygen -t rsa -C &quot;your_github_email@example.com&quot;</code></pre>
<pre><code class="language-bash"># ~/.ssh/config
# GitHub 기본 설정
Host github.com
    HostName github.com
    IdentityFile ~/.ssh/id_rsa
    User git</code></pre>
<h3 id="github에-ssh-키-추가">GitHub에 SSH 키 추가</h3>
<ol>
<li>생성된 공개 키 복사: <code>cat ~/.ssh/id_rsa.깃허브아이디.pub</code> </li>
<li>GitHub 설정 페이지에서 'SSH and GPG keys' 선택</li>
<li>'New SSH key' 버튼 클릭 후 복사한 키 붙여넣기</li>
<li>'Add SSH key' 버튼 클릭하여 저장</li>
</ol>
<h2 id="💬-마치며">💬 마치며</h2>
<p>🌪️ 폭풍같은 하루였다. 어려운 건 다 지나간 줄 알았는데 아니었어... 강사님이 코드 리딩해 주실 때는 분명 안다고 생각했는데 혼자 정리해 보면 또 헷갈린다. 반복이 답인 것 같다.
그래도 이전엔 아무것도 모르고 fatch.then.then을 공식마냥 썼는데(그마저도 gpt를 곁들인) Promise를 배우고 보니 조금은 이해할 수 있게 됐다. </p>