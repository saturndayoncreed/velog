<h2 id="❔-ssh">❔ SSH?</h2>
<blockquote>
<p>SSH(Secure Shell Protocol) : 보안이 강화된 안전한 방법으로 정보를 교환하는 방식</p>
</blockquote>
<p>SSH 원격 접속 방법은 프라이빗 키(Private Key)와 퍼블릭 키(Public Key)를 사용하여 사용하고 있는 기기를 깃허브에 인증하는 방식이다. 이 방법은 터미널 창을 사용할 수 있는 상태라면 언제든 깃허브에 접속할 수 있다.</p>


<h2 id="🔑-ssh-키-생성">🔑 SSH 키 생성</h2>
<ul>
<li><code>ssh-keygen</code> : SSH 접속을 위한 프라이빗 키와 퍼블릭 키 생성</li>
</ul>
<p>파일 이름은 입력하지 않고 <code>Enter</code>를 눌렀다. 몇번 더 누르니  <code>~/.ssh</code> 경로에 <code>id_(???)</code> 파일(프라이빗 키)과, <code>id_(???).pub</code> 파일(퍼블릭 키)가 생성된 것을 확인할 수 있다.</p>
<pre><code class="language-c">$ ssh-keygen
Generating public/private (???) key pair.
Enter file in which to save the key (/c/Users/seona/.ssh/(???)):      #홈 디렉토리 안의 .ssh 디렉토리에 SSH키가 생성됨
Created directory '/c/Users/seona/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/seona/.ssh/id_(???)   #프라이빗 키 경로
Your public key has been saved in /c/Users/seona/.ssh/id_(???).pub    #퍼블릭 키 경로
</code></pre>
 


<h2 id="😺-깃허브에-퍼블릭-키-전송">😺 깃허브에 퍼블릭 키 전송</h2>
<p>퍼블릭 키 파일의 내용을 확인해보면 아래와 같은 형식이 읽어진다. 이 때, <code>ssh-(???) 긴 문자열</code>을 복사하여 깃허브&gt;설정&gt;SSH and GPG keys의 New SSH Key에 붙여넣기 한다.</p>
<pre><code class="language-c">$ cat id_(???).pub
ssh-(???) (긴 문자열)</code></pre>
<p>그럼 아래와 같이 키가 생성된 것을 확인할 수 있다.
<img alt="" src="https://velog.velcdn.com/images/saturndayoncreed/post/2120c41b-f669-4a55-a0c4-2290e29ef727/image.png" /></p>
<h2 id="🖇️-ssh-주소로-원격-저장소-연결">🖇️ SSH 주소로 원격 저장소 연결</h2>
<p>이번엔 저장소의 SSH주소를 복사한다.
<img alt="" src="https://velog.velcdn.com/images/saturndayoncreed/post/805298f9-c137-47e2-b90e-89efc29dc5f3/image.png" /></p>
<p>그리고 복사한 주소를 <code>git remote add origin</code>명령 뒤에 붙여넣기 한다. 오류메세지 없이 프롬프트가 표시되면 정상적으로 연결된 것이다.</p>
<pre><code class="language-c">$ git remote add origin git@github.com:saturndayoncreed/ssh-prac.git</code></pre>