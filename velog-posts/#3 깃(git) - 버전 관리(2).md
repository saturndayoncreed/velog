<h2 id="👀-버전-업데이트마다-파일-상태-알아보기">👀 버전 업데이트마다 파일 상태 알아보기</h2>
<h3 id="작업트리-tracked-파일-untracked-파일">작업트리: tracked 파일, untracked 파일</h3>
<p>'hello.txt'파일을 수정하고, 새로운 'hello2.txt'파일을 생성했다. <code>git status</code>를 사용하여 상태를 확인했다. </p>
<blockquote>
<ul>
<li>tracked 파일 : 한번이라도 커밋된 파일 (계속해서 수정상태를 추적)</li>
</ul>
</blockquote>
<ul>
<li>untracked 파일 :  한번도 깃에서 버전관리 되지 않은 파일(수정 사항 추적하지 않음)</li>
</ul>
<ol>
<li>hello.txt (= tracked 파일)
1) 'Changes not staged for commit:' : 변경된 파일이 아직 스테이징되지 않음
2) 'modified:   hello.txt' : hello.txt가 수정됨</li>
<li>hello2.txt (= untracked 파일)
1) 'Untracked files:' : 한번도 깃에서 버전관리 하지 않음<pre><code class="language-c">$ vim hello.txt
</code></pre>
</li>
</ol>
<p>$ vim hello2.txt</p>
<p>$ git status
On branch master
Changes not staged for commit:
  (use &quot;git add ...&quot; to update what will be committed)
  (use &quot;git restore ...&quot; to discard changes in working directory)
        modified:   hello.txt</p>
<p>Untracked files:
  (use &quot;git add ...&quot; to include in what will be committed)
        hello2.txt</p>
<p>no changes added to commit (use &quot;git add&quot; and/or &quot;git commit -a&quot;)</p>
<pre><code>
두 파일 모두 스테이징 해준 후 상태를 확인해보면, 마지막 버전 이후 수정된 'hello.txt'는 `modified:`로 표시되고, 한번도 버전관리하지 않은 'hello2.txt'는 `new file:`로 표시된다.
```c
$ git status
On branch master
Changes to be committed:
  (use &quot;git restore --staged &lt;file&gt;...&quot; to unstage)
        modified:   hello.txt
        new file:   hello2.txt</code></pre><p>여기서 <code>git log</code>를 사용하여 커밋 로그를 확인하면 'message3'라는 커밋 메세지가 붙은 커밋과 관련된 파일은 보이지 않는다. 이때 <code>git log --stat</code>를 사용하여 커밋에 관련된 파일까지 함께 조회할 수 있다.</p>
<pre><code>$ git log --stat
commit f353c1fe9231f24926269a7ca87480b219f3744b
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Tue Jul 2 16:01:23 2024 +0900

    message3

 hello.txt  | 1 +
 hello2.txt | 4 ++++
 2 files changed, 5 insertions(+)
...</code></pre>

<h3 id="tracked-파일-unmodified-modified-staged-상태">tracked 파일: unmodified, modified, staged 상태</h3>
<blockquote>
<ul>
<li>unmodified : 수정되지 않은 상태 OR 커밋 후 수정이 없는 상태</li>
</ul>
</blockquote>
<ul>
<li>modified : 파일 수정 + 스테이징 되지 않음</li>
<li>staged : (커밋 직전 단계) 스테이징됨</li>
</ul>
<p><code>unmodified 상태</code> : 'nothing to commit, working tree clean'</p>
<pre><code class="language-c">#수정되지 않은 상태
$ git status
On branch master
nothing to commit, working tree clean #수정되지 않음(unmodified)</code></pre>
<pre><code class="language-c">#커밋 후 수정이 없는 상태
$ git commit -m &quot;delete b,c,d&quot;
[master 69081db] delete b,c,d
 1 file changed, 3 insertions(+), 3 deletions(-)

$ git status
On branch master
nothing to commit, working tree clean</code></pre>
<p><code>modified 상태</code> : 'Changes not staged for commit: '</p>
<pre><code class="language-c">$ vim hello2.txt

$ git status
On branch master
Changes not staged for commit: #수정됨, 스테이징 안됨
  (use &quot;git add &lt;file&gt;...&quot; to update what will be committed)
  (use &quot;git restore &lt;file&gt;...&quot; to discard changes in working directory)
        modified:   hello2.txt

no changes added to commit (use &quot;git add&quot; and/or &quot;git commit -a&quot;)</code></pre>
<p><code>staged 상태</code> : 'Changes to be committed:'</p>
<pre><code class="language-c">$ git add hello2.txt

$ git status
On branch master
Changes to be committed:
  (use &quot;git restore --staged &lt;file&gt;...&quot; to unstage)
        modified:   hello2.txt</code></pre>


<h2 id="🔙-작업-되돌리기">🔙 작업 되돌리기</h2>
<h3 id="작업트리-수정한-파일-되돌리기---git-restore">작업트리: 수정한 파일 되돌리기 - git restore</h3>
<ul>
<li><code>git restore (파일이름)</code> : 작업트리에서 수정한 내용을 취소(되돌리기)</li>
</ul>
<p>vim에서 'hello.txt'의 '3'을 'three'로 수정한 후 저장한다. 그리고 <code>git restore hello.txt</code>를 이용하여 수정사항을 되돌리고 <code>git cat hello.txt</code>로 내용을 확인해보면, 'three'로 변경했던 파일 내용이 다시 '3'으로 변경되어 있는 것을 알 수 있다.</p>
<pre><code class="language-c">$ git restore hello.txt

$ cat hello.txt
1
2
3
</code></pre>


<h3 id="스테이징-되돌리기---git-restore---staged">스테이징 되돌리기 - git restore --staged</h3>
<ul>
<li><code>git restore --staged (파일이름)</code> : 스테이징 되돌리기</li>
</ul>
<p><code>git add</code>를 사용하여 스테이징을 진행한다. 그리고 <code>git restore --staged</code>로 스테이징을 취소해보았다. 이후 <code>git status</code>로 상태를 확인해보면 <code>Changes not staged for commit:</code> 문구로 스테이징 이전으로 돌아온 것을 확인할 수 있다.  </p>
<pre><code class="language-c">$ git restore --staged hello2.txt

$ git status
On branch master
Changes not staged for commit:
  (use &quot;git add &lt;file&gt;...&quot; to update what will be committed)
  (use &quot;git restore &lt;file&gt;...&quot; to discard changes in working directory)
        modified:   hello2.txt

no changes added to commit (use &quot;git add&quot; and/or &quot;git commit -a&quot;)</code></pre>
  

<h3 id="최신-커밋-되돌리기---git-reset-head">최신 커밋 되돌리기 - git reset HEAD^</h3>
<ul>
<li><code>git reset HEAD^</code> : 최신 커밋 철회, 취소 파일은 작업 트리에만 남음<ul>
<li><code>git reset --soft HEAD^</code> : 최근 커밋하기 전 상태로 돌려놓음</li>
<li><code>git reset --mixed HEAD^</code> : 커밋된 파일들을 작업 트리로 돌려놓음</li>
<li><code>git reset --hard HEAD^</code> : 커밋된 파일들 중 tracked 파일들을 작업트리에서 삭제</li>
<li><code>git reset HEAD~(취소할 커밋 개수)</code> : 작성한 개수만큼의 커밋을 삭제</li>
</ul>
</li>
</ul>
<p>&quot;message4&quot;로 커밋 메세지를 설정하고, <code>git commit -am &quot;message4&quot;</code>로 스테이징과 커밋을 함께 진행하였다.</p>
<pre><code class="language-c">$ git commit -am &quot;message4&quot;
[master eeb95b0] message4
 1 file changed, 5 insertions(+), 4 deletions(-)

$ git log
commit eeb95b09e26e45e5e11ccdc423982edadf05f6f6 (HEAD -&gt; master)
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Wed Jul 3 13:52:19 2024 +0900

    message4
  ...</code></pre>
<p>  그리고 <code>git reset HEAD^</code>로 커밋을 취소해주었다. <code>git log</code>로 확인했을 때 커밋 메세지가 &quot;message4&quot;로 설정된 커밋이 삭제된 것을 볼 수 있다. <code>git reset HEAD^</code>의 <code>HEAD^</code>는 현재 HEAD가 가리키는 브랜치의 최신 커밋을 의미한다.</p>
<pre><code class="language-c">$ git reset HEAD^
Unstaged changes after reset:
M       hello2.txt

$ git log
commit 69081dbe34babde95abd4149ade39677e2d89c81 (HEAD -&gt; master)
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Tue Jul 2 16:20:15 2024 +0900

    delete b,c,d
...</code></pre>
  

<h3 id="특정-커밋으로-되돌리기---git-reset-커밋해시">특정 커밋으로 되돌리기 - git reset (커밋해시)</h3>
<ul>
<li><code>git reset (커밋해시)</code> : (커밋해시)로 이동, 이후 커밋 모두 삭제</li>
<li><code>git reset --hard (커밋해시)</code> : (커밋해시) 이후의 커밋을 모두 삭제</li>
<li><code>git reset --mixed (커밋해시)</code> : (커밋해시) 이후의 커밋을 삭제하지만 변경이력은 남아있음.
<code>git reset --soft (커밋해시)</code> : (커밋해시) 이후의 커밋을 모두 삭제, 하지만 스테이징 되어 있음</li>
</ul>
<p>새로운 파일을 생성한 후, 수정-커밋을 총 4번(커밋메세지 : R1~R4) 반복하였다. 그 이후 <code>git log</code>로 지금까지 만든 커밋을 확인해보았다.</p>
<pre><code class="language-c">$ git log
commit f9d3ccc39f506715eb2f921e8bd842fcdea337be (HEAD -&gt; master)
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Wed Jul 3 14:39:40 2024 +0900

    R4

commit a49f5e6cdb15eef6e80c44d0fad1299a1016cd08
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Wed Jul 3 14:39:17 2024 +0900

    R3
...
</code></pre>
<p>  <code>git reset --hard (R2의 커밋해시)</code>를 이용하여 R2로 이동하고 이후의 커밋을 삭제해보았다.<code>git log</code>를 이용하여 커밋을 확인해보면 아래와 같이 R3와 R4의 커밋은 삭제된 것을 알 수 있다.</p>
<pre><code class="language-c">$ git reset --hard a1ecd116e68dd74c05dca6e735d4b08f66014439
HEAD is now at a1ecd11 R2

$ git log
commit a1ecd116e68dd74c05dca6e735d4b08f66014439 (HEAD -&gt; master)
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Wed Jul 3 14:38:33 2024 +0900

    R2
...</code></pre>
  

<h3 id="커밋을-삭제하지-않고-되돌리기---git-revert">커밋을 삭제하지 않고 되돌리기 - git revert</h3>
<ul>
<li><code>git revert (커밋해시)</code> : (커밋해시)의 커밋만 삭제, <code>Revert (커밋해시의 커밋메세지)</code>에는 (커밋해시)가 삭제되었다는 이력이 남음</li>
<li><code>git revert (커밋해시)..(커밋해시)</code> : 여러개를 revert</li>
<li><code>git revert --no-commit (커밋해시)</code> : revert한 결과를 stage 상태만 유지, commit하지 않음</li>
</ul>
<p>파일을 수정하고 커밋메세지를 &quot;R3&quot;로 설정한 후 커밋을 진행한다. 이 때 <code>git log</code>로 커밋을 확인해보면 아래와 같이 나타난다.</p>
<pre><code class="language-c">$ vim rev.txt

$ git commit -am &quot;R3&quot;
[master 5ba1f21] R3
 1 file changed, 1 insertion(+)

$ git log
commit 5ba1f219838fb3905a27b9185fe1e369e56197e5 (HEAD -&gt; master)
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Wed Jul 3 15:13:44 2024 +0900

    R3
...
</code></pre>
<p>  이 때 가장 최근의 R3 버전을 삭제하고 R2 버전으로 되돌아가기 위해 <code>git revert (R3의 커밋해시)</code>를 사용한다. 해당 명령어를 사용하면 git설치 초기에 설정한 기본 편집기가 나타나며 커밋 메세지를 작성할 수 있다.</p>
<pre><code class="language-c">$ git revert 5ba1f219838fb3905a27b9185fe1e369e56197e5
[master ec9a740] Revert &quot;R3&quot;
 1 file changed, 1 deletion(-)

$ git log
commit ec9a740a51e5de56097745840a9b45b6f52b2b43 (HEAD -&gt; master)
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Wed Jul 3 15:28:40 2024 +0900

    Revert &quot;R3&quot;  #R3 커밋이 삭제되었다는 메세지만 남는다

    This reverts commit 5ba1f219838fb3905a27b9185fe1e369e56197e5.

commit 5ba1f219838fb3905a27b9185fe1e369e56197e5
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Wed Jul 3 15:13:44 2024 +0900

    R3  #커밋 이력은 남음
...</code></pre>
<p><code>git revert</code>는 히스토리가 남기 때문에 실제 개발이나 협업에서 사용하기에 적절한 명령이라고 할 수 있다. <code>git reset</code>보다는 <code>git revert</code>를 사용하는 것이 더 안전하다고 볼 수 있겠다</p>