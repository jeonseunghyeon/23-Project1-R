
##  [03월 09일] 학습내용
<details>
<summary>Git 설치</summary>

1. 구글에서 Git을 검색 후 설치합니다
2. 설치 후 확인은 다음 명령으로 합니다 $ git --version

</details>

<details>
<summary>Git 사용자 설정</summary>

1. 현재 사용자 이름 확인
~~~
$ git config user.name
~~~
2. 현재 사용자 이메일 확인
~~~
$git config user.email
~~~
3. 사용자 이름 변경
~~~
$git config --global user.name {사용자 이름}
~~~
4. 사용자 이메일 변경
~~~
$git config --global user.email {사용자 이메일}
~~~

</details>

<details>
<summary>Git ignore</summary>

1. 특정 파일이나 디렉토리를 git 버전 관리에서 의도적으로 추적하지 않도록 설정하는 파일을 gitignore 파일이라 한다. 

2. gitignore 파일 생성
~~~
touch .gitignore
~~~



</details>


<details>
<summary>깃허브 Push</summary>

1. 로컬 저장소 초기화하기
+ 교재에는 구체적인 설명이 나와 있지 않으나 프로젝트 자체의 용량은 크지 않치만 node_modules 폴더에 파일이 많아 업로드,
복사, 삭제 시에 시간이 많이 소요된다.

+ 또한 필요한 것은 새로 작성된 source이기 때문에 node_modules폴더를 제외하도록.gitignore파일을 작성한다

+ VScode를 사용할 경우 좌측하단의 구름 아이콘을 클릭하면 바로 push가 가능하다.

+ 교재에서는 루트 폴더라고 하는데, 이는 프로젝트의 루트를 말하는 것이다. 교재 전체에서 그렇게 사
용하고 있으니 주의해야 한다.

2. 깃허브에 저장소 만들기

3. 깃허브 저장소에  로드하기

4. 깃허브 저장소 확인하기

</details>



