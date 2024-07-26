<p>프로그래머스 '자연수 뒤집어 배열로 만들기' 문제를 풀었다. 분명 맞게 작성했는데 결과가 계속 null로 떠서 찾아보다가 <code>reverse()</code>의 특성을 잘 모르고 쓴 것이 문제임을 알게 되었다! <code>reverse()</code>와 <code>reversed()</code>의 차이에 대해 알아보려 한다.
</p>
<h2 id="🌀-reverse와-reversed">🌀 reverse()와 reversed()</h2>
<table>
<thead>
<tr>
<th align="left">구분</th>
<th align="center"><strong><code>리스트.reverse()</code></strong></th>
<th align="right"><strong><code>reversed(리스트)</code></strong></th>
</tr>
</thead>
<tbody><tr>
<td align="left">사용 가능한 자료형</td>
<td align="center">리스트</td>
<td align="right">리스트, 튜플, 문자열 등</td>
</tr>
<tr>
<td align="left">반환</td>
<td align="center">NONE</td>
<td align="right">반복가능한(iterable) 객체</td>
</tr>
<tr>
<td align="left">원본 리스트</td>
<td align="center">순서 바뀜</td>
<td align="right">영향 X (별개의 리스트)</td>
</tr>
</tbody></table>


<h3 id="➿-reverse">➿ reverse()</h3>
<p>이 코드는 <code>NONE</code>이 출력된다. 왜 이럴까? </p>
<pre><code class="language-python">n = [1, 2, 3, 4]
turn = n.reverse()

print(turn)
--------------------
NONE</code></pre>
<p>하지만 아래의 코드는 정상적으로 리스트가 뒤집혀서 출력된다.</p>
<pre><code class="language-python">n = [1, 2, 3, 4]
n.reverse()

print(n)  #원본과 동일한 리스트
--------------------
[4, 3, 2, 1]</code></pre>
<p>이는 <code>reverse()</code>코드는 NONE을 반환하고, 리스트 자체의 순서를 반대로 바꿔주기 때문이다. 따라서 원본 리스트 n의 순서가 바뀌는 것이다.
</p>
<h3 id="➿-reversed">➿ reversed()</h3>
<p>이 코드는 <code>reversed()</code>를 사용하여 작성한 코드이다. 하지만 아래에는 에러코드가 출력된 것을 볼 수 있다.</p>
<pre><code class="language-python">n = [1, 2, 3, 4]
New = reversed(n)

print(New)
--------------------
&lt;list_reverseiterator object at 0x00000265E47B5548&gt;</code></pre>
<p><code>reversed()</code>코드는 반복가능한(iterable) 객체를 반환하기 때문에 이 역순을 사용하기 위해서는 다시 원하는 형태으로 반환해야 한다. 하지만 <code>reverse()</code>와는 달리 원본 리스트의 순서에는 영향이 없는 것을 확인할 수 있다.</p>
<pre><code class="language-python">n = [1, 2, 3, 4]
New = list(reversed(n))  #리스트로 받기
NNew = tuple

print(New)
print(NNew)
print(n)  #원본 리스트 출력
--------------------
[4, 3, 2, 1]
(4, 3, 2, 1)
[1, 2, 3, 4]  #원본 리스트에는 영향이 없다</code></pre>