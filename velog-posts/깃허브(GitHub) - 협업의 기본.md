<h2 id="✌️-원격-저장소-복제">✌️ 원격 저장소 복제</h2>
<ul>
<li><code>git clone (원격저장소 주소) (복제할 경로)</code> : (복제할 경로)가 없다면 자동으로 디렉토리를 생성한 후 복제된다. 복제 과정에서 복제할 경로의 master 브랜치는 origin에 연결된다.</li>
</ul>
<p>만약 집 컴퓨터와 회사 컴퓨터에 원격 저장소를 복제하여 작업했다면, 작업 내용을 원격 저장소로 올리기 위해서는 <code>git push</code>, 작업 내용을 내려받기 위해서는 <code>git pull</code>을 사용한다.</p>
<h2 id="🥄-원격-브랜치-정보-가져오기">🥄 원격 브랜치 정보 가져오기</h2>
<ul>
<li><code>git fetch</code> : 원격 저장소의 정보를 가져온다. (<code>git pull</code>과 달리 merge 하지 않음)</li>
<li><code>git merge origin/(브랜치명)</code> : (브랜치명)에 있는 커밋과 병합</li>
<li><code>git merge FETCH_HEAD</code> : <code>git fetch</code>를 진행한 후 지역저장소에 반영되지 않은 최신 커밋 반영 </li>
</ul>
<p><code>git pull</code>은 원격 저장소의 최신 사항을 로컬 브랜치로 바로 merge하는 반면, <code>git fetch</code>는 원격 저장소의 최신 사항만 가져오고(FETCH_HEAD 브랜치로 가져옴) 로컬 브랜치에 merge하지 않는다는 것이 가장 큰 차이점이다. 즉, <code>git fetch</code>를 실행한 이후 최신사항을 적용하고 싶다면 <code>git merge</code>를 따로 수행해줘야 한다.</p>