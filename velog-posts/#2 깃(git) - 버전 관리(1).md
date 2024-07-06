<h2 id="🤸-깃으로-할-수-있는-것">🤸 깃으로 할 수 있는 것</h2>
<blockquote>
<ol>
<li>버전 관리 : 문서 수정 확인에 용이</li>
<li>백업 : 원격 저장소(GitHub)</li>
<li>협업 : 여러 사람이 함께 일할 수 있다</li>
</ol>
</blockquote>
<hr />
<p>위의 순서대로 난이도가 어려워지기 때문에 꼭 이 순서대로 배워야 한다.</p>


<h2 id="🧰-깃-저장소-만들기">🧰 깃 저장소 만들기</h2>
<h3 id="깃-초기화">깃 초기화</h3>
<ul>
<li><code>git init</code> : 현재 위치에 저장소(repository) 만들기</li>
</ul>
<p>깃을 사용할 수 있도록 디렉토리 초기화를 진행한다. 초기화 이후 <code>'Initialized empty Git repository...'</code>라는 메세지가 나타나면 해당 디렉토리에서 <code>git</code>을 사용할 수 있다. <code>'.git'</code>이라는 디렉토리가 생성된 것을 확인할 수 있는데, 이는 깃을 사용하면서 버전이 저장될 '저장소(repository)'이다.</p>
<pre><code class="language-c">$ git init
Initialized empty Git repository in C:/Users/seona/hello-git/.git/

$ ls -la
total 20
drwxr-xr-x 1 seona 197609 0 Jul  2 14:18 ./
drwxr-xr-x 1 seona 197609 0 Jul  2 11:22 ../
drwxr-xr-x 1 seona 197609 0 Jul  2 14:18 .git/</code></pre>


<h2 id="🖥️-버전-만들기">🖥️ 버전 만들기</h2>
<h3 id="01-스테이지와-커밋">01 스테이지와 커밋</h3>
<blockquote>
<ul>
<li>작업트리(working tree) : 파일 수정, 저장 등</li>
</ul>
</blockquote>
<ul>
<li>스테이지(stage) : 버전으로 만들 파일이 대기하는 곳</li>
<li>저장소(repository) : 커밋(commit) 명령을 통해 스테이지에서 대기하고 있던 파일들을 버전으로 만들어 저장</li>
</ul>



<h3 id="02-작업-트리-빔으로-문서-수정">02 작업 트리: 빔으로 문서 수정</h3>
<ul>
<li><code>git status</code> : git의 상태를 파악할 수 있음</li>
</ul>
<p>앞에서 깃을 초기화 했기 때문에 버전 관리가 가능하다. <code>git status</code>를 이용하여 <code>git</code>의 상태를 파악할 수 있다.</p>
<pre><code class="language-c">$ git status
On branch master 

No commits yet

nothing to commit (create/copy files and use &quot;git add&quot; to track) #현재 커밋할 파일이 없음</code></pre>
<p>이후 vim에서 파일을 생성하고 생성한 파일을 조회했다. 아래의 코드를 확인해보면 생성한 파일이 디렉토리 안에 만들어져있다.</p>
<pre><code class="language-c">$ vim hello.txt

$ ls -la
total 25
drwxr-xr-x 1 seona 197609 0 Jul  2 14:37 ./
drwxr-xr-x 1 seona 197609 0 Jul  2 14:37 ../
drwxr-xr-x 1 seona 197609 0 Jul  2 14:35 .git/
-rw-r--r-- 1 seona 197609 2 Jul  2 14:37 hello.txt #생성한 파일</code></pre>
<p>다시 한번 <code>git</code>의 상태를 확인해보면 아래와 같이 나타난다. <code>branch master</code>에 'hello.txt'라는 <code>untracked files</code>가 있다고 나타난다.</p>
<pre><code class="language-c">$ git status
On branch master

No commits yet

Untracked files:
  (use &quot;git add &lt;file&gt;...&quot; to include in what will be committed)
        hello.txt

nothing added to commit but untracked files present (use &quot;git add&quot; to track)</code></pre>


<h3 id="03-스테이지-수정한-파일-스테이징---git-add">03 스테이지: 수정한 파일 스테이징 - git add</h3>
<ul>
<li><code>git add</code> : 스테이징, 스테이지에 올리기</li>
<li><code>git add .</code> : 작업 트리에서 수정한 파일들 한꺼번에 스테이징</li>
</ul>
<p>작업한 파일을 만들거나 수정한 이후, 버전으로 만들고자 하는 파일을 스테이지에 추가한다. 깃에게 버전 만들 준비를 시키는 것을 <strong>스테이징(staging)</strong>, <strong>'스테이지에 올린다'</strong> 고 한다. </p>
<p><code>untracked files</code>가 <code>changes to be committed</code>로 바뀌었다. 그리고 'hello.txt' 파일 앞에 <code>new file</code>이라는 수식어가 추가적으로 나타난다. 이 문구들은 '새로운 파일 'hello.txt'를 커밋할 것이다.'라는 의미이다.</p>
<pre><code class="language-c">$ git add hello.txt
warning: in the working copy of 'hello.txt', LF will be replaced by CRLF the next time Git touches it

$ git status
On branch master

No commits yet

Changes to be committed:
  (use &quot;git rm --cached &lt;file&gt;...&quot; to unstage)
        new file:   hello.txt</code></pre>


<h3 id="04-저장소-스테이지에-올라온-파일-커밋---git-commit">04 저장소: 스테이지에 올라온 파일 커밋 - git commit</h3>
<ul>
<li><code>git commit</code> : 파일 커밋</li>
<li><code>git commit -m</code> : 커밋 메세지 작성</li>
<li><code>git commit --amend</code> : 가장 최근의 커밋 메세지 수정</li>
</ul>
<p><strong>커밋(commit)</strong> 은 깃에서 스테이지에 있는 파일로 버전을 만드는 것을 의미한다. 커밋할 땐 버전의 변경사항도 함께 기록하는 것이 좋다.</p>
<pre><code class="language-c">$ git commit -m &quot;message1 &quot;
[master (root-commit) c23ba70] message1
 1 file changed, 1 insertion(+) #파일 1개가 변경되었고, 파일에 1개의 내용이 추가됨
 create mode 100644 hello.txt</code></pre>
<ul>
<li><code>git log</code> : 저장소에 저장된 버전 확인</li>
</ul>
<p><code>git log</code>에서는 커밋한 버전에 대한 설명(커밋한 사람, 만든 시간정보, 커밋 메세지)이 나타난다. 이 과정을 거치면 'hello.txt' 파일 버전이 저장소에 만들어진다.</p>
<pre><code class="language-c">$ git log
commit c23ba70355af9968476887cbc9e20c3da57f589d (HEAD -&gt; master)
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Tue Jul 2 15:08:05 2024 +0900

    message1
</code></pre>


<h3 id="05-스테이징과-커밋-한번에-처리---git-commit--am">05 스테이징과 커밋 한번에 처리 - git commit -am</h3>
<ul>
<li><code>git commit -am &quot;커밋메세지&quot;</code>, <code>git commit -a -m &quot;커밋메세지&quot;</code> : (한번이라도 커밋한 적 있는 파일에 대해) 스테이징+커밋 한번에 처리</li>
</ul>
<p>vim으로 'hello.txt'의 내용을 수정하고, 수정한 내용을 <code>git commit -am</code> 명령을 이용하여 스테이징과 커밋을 한번에 처리한다.</p>
<pre><code class="language-c">$ vim hello.txt

$ git commit -am &quot;message2&quot;
warning: in the working copy of 'hello.txt', LF will be replaced by CRLF the next time Git touches it
[master 04ef746] message2
 1 file changed, 1 insertion(+)</code></pre>


<h2 id="📑-커밋-내용-확인">📑 커밋 내용 확인</h2>
<h3 id="커밋-기록-확인---git-log">커밋 기록 확인 - git log</h3>
<ul>
<li><code>git log</code> : 커밋 기록 확인</li>
<li><code>git log --stat</code> : 커밋 기록 + 커밋에 관련된 파일도 함께 확인</li>
<li><code>git log (브랜치1)..(브랜치2)</code> : (브랜치1에는 없고) 브랜치2에만 있는 커밋 확인 </li>
<li><code>git log --oneline</code> : 한 줄에 한 커밋씩 나타남</li>
<li><code>git log --oneline --branches</code> : 각 브랜치의 커밋을 함께 확인</li>
<li><code>git log --oneline --branches --graph</code> : 브랜치와 커밋의 관계를 그래프 형태로 표현</li>
</ul>
<p>① 커밋 해시(commit hash), 깃 해시(git hash) : 커밋을 구별하는 아이디
② (Head -&gt; master) : 최신 버전을 나타내는 표시
③ 커밋 메세지 : 버전 설명을 위해 작성한 메세지
④ 커밋 로그 : <code>git log</code>를 사용했을 때 나오는 정보들
<img alt="" src="https://velog.velcdn.com/images/saturndayoncreed/post/79ff1009-cee4-4f4c-9c5c-399dfc94e926/image.png" /></p>
<h3 id="변경-사항-확인---git-diff">변경 사항 확인 - git diff</h3>
<ul>
<li><code>git diff</code> : 작업 트리 파일과 스테이지 파일 비교, 스테이지에 있는 파일과 저장소에 있는 최신 커밋 비교</li>
</ul>
<p>'hello.txt'파일을 수정했을 때, 버전의 최신 파일과 어떻게 다른지 알고싶다면 <code>git diff</code> 명령을 사용하여 확인할 수 있다.</p>
<pre><code class="language-c">$ git diff
warning: in the working copy of 'hello.txt', LF will be replaced by CRLF the next time Git touches it
diff --git a/hello.txt b/hello.txt
index 1191247..0b66db0 100644
--- a/hello.txt
+++ b/hello.txt
@@ -1,2 +1,2 @@
 1
-2 #파일에서 2가 삭제(-)됨
+two #파일에 two가 추가(+)됨</code></pre>