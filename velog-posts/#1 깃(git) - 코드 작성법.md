<h2 id="⚙️-깃-환경-설정하기">⚙️ 깃 환경 설정하기</h2>
<ul>
<li><code>git config --global user.name &quot;(이름)&quot;</code> : 깃 환경에서 이름 지정</li>
<li><code>git config --global user.email &quot;(이메일)&quot;</code> : 깃 환경에서 이메일 지정</li>
<li><code>git config --unset --global user.name</code> : 유저 정보 제거</li>
<li><code>git congig --global --list</code> : 유저 등록 정보 확인</li>
</ul>
<pre><code class="language-c">$ git config --global user.name &quot;seona&quot;

$ git config -- global user.email &quot;saturn1319@naver.com&quot;
</code></pre>


<h2 id="🪡-리눅스-명령-연습하기">🪡 리눅스 명령 연습하기</h2>
<ul>
<li><code>-</code> : 리눅스 명령에 옵션을 추가하려면 붙임표와 함께 원하는 옵션을 나타내는 글자를 함께 입력한다.</li>
</ul>
<h3 id="01-디렉토리-살펴보기---pwd-ls">01 디렉토리 살펴보기 - pwd, ls</h3>
<ul>
<li><code>pwd</code> : 현재 위치의 경로</li>
<li><code>~</code> : 홈 디렉토리<pre><code class="language-c">$ pwd
/c/Users/seona #현재 위치 경로
</code></pre>
</li>
</ul>
<pre><code>- `ls` : 현재 디렉토리에 어떤 파일이나 디렉토리가 있는지 확인
- `ls -a` : 숨긴 파일과 디렉토리 표시
- `ls -l` : 파일과 디렉토리의 상세 정보까지 표시하는 옵션 추가
- `ls -r` : 파일의 정렬 순서를 거꾸로 표시
- `ls -t` : 파일 작성 시간 순으로(내림차순) 표시
```c
$ ls
 20220824_ImageWorkspace/
'3D Objects'/
 AppData/
'Application Data'@
...</code></pre><pre><code class="language-c">$ ls -la
total 19992
drwxr-xr-x 1 seona 197609        0 Jul  1 17:59  ./
drwxr-xr-x 1 seona 197609        0 Apr  4  2023  ../
...</code></pre>


<h3 id="02-디렉토리-이동---cd">02 디렉토리 이동 - cd</h3>
<ul>
<li><code>cd</code> : 터미널 창에서 디렉터리 사이를 이동할 때</li>
<li><code>cd (하위 디렉토리 명)</code> : 하위 디렉토리로 이동할 때</li>
<li><code>cd ~</code> : 홈 디렉토리로 이동</li>
<li><code>cd ./</code> : 현재 사용자가 작업중인 디렉토리</li>
<li><code>cd ../</code> : 현재 디렉토리의 상위 디렉토리</li>
</ul>


<h3 id="03-디렉토리-생성-및-삭제---mkdir-rm">03 디렉토리 생성 및 삭제 - mkdir, rm</h3>
<ul>
<li><code>mkdir</code> : 터미널 창에서 디렉토리 만들기(make directory)<pre><code class="language-c">$ cd Documents
</code></pre>
</li>
</ul>
<p>$ mkdir test</p>
<p>$ ls
'My Music'@  'My Pictures'@  'My Videos'@   test/</p>
<pre><code>- `rm` : 디렉토리 삭제
- `rm -r` : 디렉토리 안의 하위 디렉토리와 파일까지 함께 삭제
```c
$ rm -r test

$ ls
'My Music'@  'My Pictures'@  'My Videos'@
</code></pre> 

<h3 id="04-빔에서-문서-생성수정---vim">04 빔에서 문서 생성&amp;수정 - vim</h3>
<ul>
<li><code>vim (파일이름)</code> : 현재 디렉토리에 파일 생성(열기) </li>
</ul>
<p>리눅스의 기본 편집기인 빔(Vim)은 터미널에서 사용할 수 있는 대표적인 편집기이다. 터미널 창에서 입력만으로 사용이 가능하여 간편하게 사용할 수 있다.</p>
<pre><code>$ vim test.txt</code></pre><ul>
<li><code>i</code> : insert 모드가 되며 텍스트 수정 가능</li>
<li><code>a</code> : add, 마찬가지로 insert 모드로 전환</li>
<li><code>esc</code> : ex 모드가 되며 수정 불가</li>
<li><code>:w</code>, <code>:write</code> : 문서 저장</li>
<li><code>:q</code>, <code>:quit</code> : 편집기 종료</li>
<li><code>:wq (파일이름)</code> : 문서 저장 및 종료, 파일 이름을 함께 입력하면 해당 이름으로 저장</li>
<li><code>:q!</code> : 문서를 저장하지 않고 편집기 종료. 확장자 .swp인 임시파일 생성</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/saturndayoncreed/post/38ff3ba8-58f6-43b8-a794-e435736fed62/image.png" /></p>
<ul>
<li><code>cat (파일)</code> : 파일의 내용을 화면에 표시</li>
<li><code>cat (파일1, 파일2, ... 파일n)</code> : 파일 n개를 연결해서 새로운 파일 생성</li>
<li><code>cat 파일1 &gt;&gt; 파일2</code> : 파일1의 내용을 파일2의 끝에 연결<pre><code class="language-c">$ cat test.txt
hello git
</code></pre>
</li>
</ul>
<pre><code>&lt;/br&gt;

### ➕ 기본 편집기 변경

- `git config -- global core.editor &quot;(편집기 명)&quot;`,  `git config -- global core.editor (편집기 경로)` : 기본 편집기 변경(미 설정 시 기본 편집기는 vim)

물론 기본 편집기 변경도 가능하다. 만약 기본 편집기를 notepad++로 변경하기 위해서는 아래와 같은 코드를 입력하면 된다.
```c
$ git config -- global core.editor &quot;notepad++&quot;</code></pre>