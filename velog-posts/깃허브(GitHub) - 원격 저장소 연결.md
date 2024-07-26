<h2 id="💾-깃허브--원격-저장소">💾 깃허브 = 원격 저장소</h2>
<blockquote>
<h3 id="깃허브로-할-수-있는-일">깃허브로 할 수 있는 일</h3>
</blockquote>
<ol>
<li>원격 저장소에서도 깃 사용</li>
<li>지역 저장소 백업</li>
<li>협업 프로젝트 사용</li>
<li>개발 이력을 남길 수 있다.</li>
<li>다른 사람의 코드 구경</li>
<li>오픈 소스 참가</li>
</ol>


<h2 id="🪡-지역-저장소를-원격-저장소에-연결">🪡 지역 저장소를 원격 저장소에 연결</h2>
<ul>
<li><code>git remote add origin (원격저장소 주소)</code> : 원격 저장소(remote)에 origin(원격 저장소 저장소)을 추가(add)</li>
<li><code>git remote -v</code> : 추가한 원격저장소 목록 확인</li>
</ul>
<p>지역 저장소를 깃허브에 생성한 <code>test-1</code> 리포지토리와 연결하기 위해 여러 접속방법 중 <code>…or push an existing repository from the command line(커맨드 라인에서 기존 저장소를 푸시)</code> 방법을 사용해보려 한다.
<img alt="" src="https://velog.velcdn.com/images/saturndayoncreed/post/ca67de28-dcc0-4351-a533-02ea2503fc6e/image.png" /></p>
<p>파란 상자 안에 있는 깃허브 리포지토리의 주소를 복사하고, <code>git remote add origin (리포지토리 주소)</code> 명령을 이용하여 원격 저장소에 <code>origin</code>을 추가한다. <code>origin</code>은 기본 원격 저장소를 가리킨다.</p>
<pre><code class="language-c">$ git remote add origin https://github.com/saturndayoncreed/test-1.git

$ git remote -v
origin  https://github.com/saturndayoncreed/test-1.git (fetch)
origin  https://github.com/saturndayoncreed/test-1.git (push)
</code></pre>


<h2 id="📤-파일-업로드">📤 파일 업로드</h2>
<ul>
<li><code>git push</code> : 지역 저장소의 커밋을 원격 저장소로 보냄</li>
<li><code>git push -u origin master</code> : 지역 저장소의 브랜치(master)를 원격저장소(origin)에 연결(-u), 처음 한번만 설정하면 됨</li>
</ul>
<p>푸시가 끝나면 지역 저장소의 커밋이 원격 저장소로 올라갔다는 뜻으로, 다시 깃허브로 돌아가 확인해보면 지역 저장소에 생성한 fi.txt 파일이 원격 저장소에도 업로드 된 것을 확인할 수 있다.
 이후 푸시를 진행할 땐, <code>git push</code>만 입력해도 푸시가 진행된다.</p>
<pre><code class="language-c">$ git push -u origin master</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/saturndayoncreed/post/d8950fe4-9f9f-414d-bbb5-2f4a8408269b/image.png" /></p>


<h2 id="📥-파일-다운로드">📥 파일 다운로드</h2>
<ul>
<li><code>git pull</code> : 원격 저장소의 소스를 지역 저장소로 가져옴</li>
<li><code>git pull origin master</code> : 원격 저장소(origin)의 내용을 master 브랜치로 가져옴</li>
</ul>