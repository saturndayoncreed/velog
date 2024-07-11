<h2 id="🌵-브랜치branch">🌵 브랜치(branch)</h2>
<h3 id="브랜치란">브랜치란?</h3>
<blockquote>
<p><strong>브랜치(Branch)</strong> : 독립적으로 작업을 진행할 수 있는 가지를 의미한다. 기본 브랜치는 주로 main이나 master라고 부르며, 새로운 기능을 추가하거나 버그를 수정할 때 별도의 브랜치를 만들어서 작업하고, 나중에 main 브랜치에 병합(Merge)할 수 있다. <em>-ChatGPT</em></p>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/saturndayoncreed/post/77c8bda8-4312-4a5c-8ad7-74c9caf65d2c/image.png" /></p>
<h3 id="브랜치의-기능">브랜치의 기능</h3>
<blockquote>
<ul>
<li><strong>master(main) 브랜치</strong> : 깃으로 버전관리를 시작하면 생성되는 브랜치</li>
</ul>
</blockquote>
<ul>
<li><strong>분기(branch)하다</strong> : 기존의 master 브랜치를 유지하며 새로운 브랜치를 만드는 것</li>
<li><strong>병합(merge)하다</strong> : 새 브랜치에 있던 파일을 master 브랜치로 합치는 것</li>
</ul>


<h2 id="🧱-브랜치-만들기">🧱 브랜치 만들기</h2>
<ul>
<li><code>git branch</code> : 브랜치 확인, 생성</li>
<li><code>git branch (브랜치 이름)</code> : 브랜치 생성<pre><code class="language-c">$ git branch apple
</code></pre>
</li>
</ul>
<p>$ git branch
  apple</p>
<ul>
<li>master<pre><code></code></pre></li>
</ul>
<h3 id="브랜치-삭제">브랜치 삭제</h3>
<ul>
<li><code>git branch -d (브랜치명)</code> : 브랜치 삭제</li>
</ul>
<p>사용하지 않는 브랜치는 깃에서 삭제할 수 있다. 하지만 완전히 삭제되는 것이 아니라 다시 같은 이름의 브랜치를 만들면 이전의 내용을 확인할 수 있다.</p>
<pre><code class="language-c">$ git branch -d apple
Deleted branch apple (was 2765b82).</code></pre>
<h3 id="브랜치-이동">브랜치 이동</h3>
<ul>
<li><code>git checkout (브랜치명)</code> : (브랜치명)의 브랜치로 이동<pre><code class="language-c">seona@Fragile MINGW64 ~/manual (master)
$ git checkout apple
Switched to branch 'apple'
</code></pre>
</li>
</ul>
<p>seona@Fragile MINGW64 ~/manual (apple)</p>
<pre><code>&lt;/br&gt;

## 🔍 브랜치 정보 확인하기
### 다른 브랜치에서 커밋
새로 만든 apple 브랜치에서 커밋을 진행한 후 `git log --oneline`명령을 이용하여 로그를 확인해보았다. 여러 브랜치의 커밋 상태를 확인하기 위해 `--branches`옵션을 사용하였고, 브랜치와 커밋의 관계를 보기 쉽게 표시하기 위해 `--graph`옵션도 사용하였다.
```c
$ git log --oneline --branches --graph
* 6ead63d (HEAD -&gt; apple) apple content 4  #work 3 커밋 이후 apple content 4 커밋이 만들어짐
| * a5910d3 (master) master content 4  #work 3 이후 master content 4 커밋이 만들어짐
|/
* 55b8f77 (ms, google) work 3
* 2ac755d work2
* fec854d work.txt
</code></pre><h3 id="브랜치-사이-차이점">브랜치 사이 차이점</h3>
<ul>
<li><code>git log (브랜치1)..(브랜치2)</code> : (브랜치1에는 없고) 브랜치2에만 있는 커밋 확인</li>
</ul>
<p><code>git log master..apple</code>은 apple 브랜치에만 존재하는 커밋을 보여주고, <code>git log apple..master</code>은 master에만 존재하는 커밋을 보여준다.</p>
<pre><code class="language-c">$ git log master..apple
commit 6ead63db1efc604982e896d2b6ebefdab2c16bf8 (HEAD -&gt; apple)
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Thu Jul 4 17:29:10 2024 +0900

    apple content 4

$ git log apple..master
commit a5910d3c48f5fdabd524e4116d118ed18181968c (master)
Author: seona &lt;saturn1319@naver.com&gt;
Date:   Thu Jul 4 17:25:07 2024 +0900

    master content 4
</code></pre>


<h2 id="🪢-브랜치-병합merge">🪢 브랜치 병합(merge)</h2>
<ul>
<li><code>git merge (브랜치명)</code> : (브랜치명)의 브랜치를 현재 브랜치로 가져와 병합</li>
<li><code>git merge (브랜치명) --no-edit</code> : 기본 커밋 메세지 사용(편집기 열리지 않음)</li>
<li><code>git merge (브랜치명) --edit</code> : (편집기 열리지 않도록 사용한 후) 다시 편집기 열어 수정하고 싶을 때</li>
</ul>
<p>master 브랜치에 o2 브랜치를 가져와 병합하기 위해 <code>git checkout master</code>명령을 이용하여 master 브랜치로 체크아웃하고, <code>git merge (브랜치명)</code>명령으로 o2 브랜치를 병합했다. 이 때 vim 이 실행되면서 <code>'Merge branch o2'</code>라는 커밋메세지가 나타나는데, 이는 수정해도 되고 그냥 사용해도 무관하다.
 o2 work2 커밋이 master 브랜치와 병합되면서 Merge branch o2 커밋이 새로 생성된 것을 확인할 수 있다.</p>
<pre><code class="language-c">$ git merge o2

$ git log --oneline --branches --graph
*   316f162 (HEAD -&gt; master) Merge branch 'o2'
|\
| * 536b944 (o2) o2 work 2
* | 1717cbb master work 2
|/
* 101270d work 1
</code></pre>
<p>깃은 줄(row) 단위로 변경 여부를 확인하기 때문에 다른 위치를 수정했을 땐 문제없이 하나의 파일로 병합된다. 같은 문서 내 다른 위치(줄)에 입력한 내용들은 정상적으로 한 파일에 병합되는 기능을 가지고 있지만, 같은 문서 내 같은 위치(줄)에 작성된 내용은 충돌(CONFLICT)를 일으킨다.</p>
<pre><code class="language-c">$ git merge o2
Auto-merging work.txt
CONFLICT (content): Merge conflict in work.txt
Automatic merge failed; fix conflicts and then commit the result.</code></pre>
<p><code>&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD</code> ~ <code>=======</code> : 현재 브랜치에서 수정한 내용
<code>=======</code> ~ <code>&gt;&gt;&gt;&gt;&gt;&gt;&gt; (merge할 브랜치)</code> : (merge할 브랜치)에서 수정한 내용</p>
<p>충돌이 감지된 내용을 수정한 후, <code>&lt;</code>,<code>=</code>는 삭제 후 저장한다.</p>
<pre><code># title
content
&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD
master content 2    #현재 브랜치에서 수정한 내용
=======
o2 content         #merge할 브랜치에서 수정한 내용
&gt;&gt;&gt;&gt;&gt;&gt;&gt; o2
# title
content
</code></pre>

<h2 id="⚙️-브랜치-관리">⚙️ 브랜치 관리</h2>
<h3 id="수정중인-파일-감추기-및-되돌리기">수정중인 파일 감추기 및 되돌리기</h3>
<ul>
<li><code>git stash</code> : 수정중인 파일 보관</li>
<li><code>git stash list</code> : 보관 파일 목록을 stash 스택에서 확인</li>
<li><code>git stash pop</code> : stash 목록에서 가장 최근 항목(stash@{0}) 되돌리기</li>
<li><code>git stash apply</code> : stash 목록에서 가장 최근 항목을 되돌리지만, 저장했던 내용은 그대로 보관</li>
<li><code>git stash drop</code> : 가장 최근 항목 삭제</li>
</ul>
<p>수정 중인 파일을 커밋하기 전에 다른 파일을 수정해야 할 때, 커밋하지 않은 수정내용을 보관할 필요가 있을 때 <code>git stash</code>를 사용한다. 이 명령을 사용하기 위해서는 한 번이라도 커밋을 진행한 상태여야 한다.</p>