<h1>전승현</h1>

<h2>[05월 25일] 학습내용</h2>

## 

<h3>방사형 차트</h3>

방사형 차트(Radar Chart)는 어떤 측정 목표에 대한 평가항목이 여러 개일 때 항목 수에 따라 원을 같은 간격으로 나누고, 중심으로부터 일정 간격으로 동심으로 척도를 재는 칸을 나누어 각 평가항목의 정량화된 점수에 따라 그 위치에 점을 찍고 평가항목간 점을 이어 선으로 만들어 항목 간 균형을 한눈에 볼 수 있도록 해주는 차트입니다. 여러 측정 목표를 함께 겹쳐 놓아 비교하기에 편리하고 각 항목 간 비율뿐만 아니라 균형과 경향을 직관적으로 알 수 있어 편리함을 제공해주는 차트입니다. 




```R
> set.seed(99)
> data <- as.data.frame(matrix( sample( 0:20 , 15 , replace=F) , ncol=5))
> colnames(data) <- c("math" , "english" , "biology" , "music" , "R-coding" )
> rownames(data) <- paste("mister" , letters[1:3] , sep="-")
> data
         math english biology music R-coding
mister-a   12      17      10    19        1
mister-b    2       9       4     6       16
mister-c   13      15      18     5       20
```


<h5>방사형 차트 그리기/h5>

 
```R
#색깔설정
> colors_border=c( rgb(0.2,0.5,0.5,0.9), rgb(0.8,0.2,0.5,0.9) , rgb(0.7,0.5,0.1,0.9) )
> colors_in=c( rgb(0.2,0.5,0.5,0.4), rgb(0.8,0.2,0.5,0.4) , rgb(0.7,0.5,0.1,0.4) )

# 방사형 차트
> radarchart( data  , axistype=1 , 
+   #custom polygon
+   pcol=colors_border , pfcol=colors_in , plwd=4 , plty=1,
+   #custom the grid
+   cglcol="grey", cglty=1, axislabcol="grey", caxislabels=seq(0,20,5), cglwd=0.8,
+   #custom labels
+   vlcex=0.8 
+ )

# 범례추가
> legend(x=0.7, y=1, legend = rownames(data[-c(1,2),]), bty = "n", pch=20 ,
+        col=colors_in , text.col = "grey", cex=1.2, pt.cex=3)

```

<h3>요약</h3>
```R
- 방사형 차트(Radar Chart)는  평가항목간 점을 이어 선으로 만들어 항목 간 균형을 한눈에 볼 수 있도록 해주는 차트임. 

-R에서 방사형 차트를 그릴 수 함수는  fmsb 패키지의 radarchart() 함수가 있음

- 방사형 차트를 그릴 때, 축의 최대값, 최소값 설정은 maxmin 인자와 데이터 삽입을 통해 가능

​
```





<h2>[05월 18일] 학습내용</h2>

## 

<h3>벡터 정렬</h3>



<h5>Sort함수</h5>

a에 랜덤한 숫자 벡터를 선언하고

sort함수를 이용해 아래와 같이 정렬할 수 있습니다. 

 

내림차순을 하기 위해서는 decreasing = T 옵션을 넣어주어야 하고

 

오름차순을 위해서는 옵션없이 사용하시면 됩니다.


```R
a<-c(3,5,6,1,8,9,11,13) 
sort(a,decreasing = T) 
sort(a) 
sort(a,decreasing = F)
```


<h5>order함수</h5>

order함수는 vector값들의 순서 index를 반환합니다.

a[order(a)] # 는 오름차순이고

a[order(-a)] # 는 내림차순을 의미합니다.

 
```R
a 
order(a)  
## 4 a의 네번째 값이 첫번째로 
## 1 a의 첫번째 값이 두번째로 
## 2 a의 두번째 값이 세번째로... 

order(-a) 
a[order(a)] ## 오름차순 
a[order(-a)] ## 내림차순

```

<h3>샘플링</h3>
많은 데이터 중 일부를 선택해야 할 때가 있습니다. 그 경우에 처리하는 기술을 샘플링이라고 합니다. 비복원 추출을 통해 중복되지 않은 랜덤한 값을 추출할 수 있습니다
```R
 x <- 1:100
 
 # x 에서 10개의 수를 임의로 추출 (비복원 추출) 
 y <- sample(x, size=10, replace = FALSE)
 
 y
 # [1] 37 43 18 95 29 51 52 28 88 67
```

<h3>조합</h3>
combn 함수를 통해 조합을 만들 수 있습니다. 아래 예제를 참고해보세요. 경우의 수를 만들어주어 원하는 데이터를 만들어낼 수 있습니다.


```R

combn(5,3) # 5개중 3개를 뽑는 조합
 #      [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]
 # [1,]    1    1    1    1    1    1    2    2    2     3
 # [2,]    2    2    2    3    3    4    3    3    4     4
 # [3,]    3    4    5    4    5    5    4    5    5     5
 
 x = c("red","green","blue","black","white")
 
 com <- combn(x,2) # x 의 원소를 2개씩 뽑는 조합
 
 com
 #      [,1]    [,2]   [,3]    [,4]    [,5]    [,6]    [,7]    [,8]    [,9]   
 # [1,] "red"   "red"  "red"   "red"   "green" "green" "green" "blue"  "blue" 
 # [2,] "green" "blue" "black" "white" "blue"  "black" "white" "black" "white"
 #      [,10]  
 # [1,] "black"
 # [2,] "white"
 
 for(i in 1:ncol(com)) {   
   cat(com[,i], "\n")   
 }
 # red green 
 # red blue 
 # red black 
 # red white 
 # green blue 
 # green black 
 # green white 
 # blue black 
 # blue white 
 # black white

```




<h2>[05월 04일] 학습내용</h2>

## 

<h3>원 그래프</h3>

원을 그리고 이 원을 상대도수에 비례하여 중심각을 나누어 마치 파이의 조각을 나눈 것 같은 형태를 갖는 그림.


```R
data= c(21.6,22.3,16.4,15.7,9.9,14.2)

pie(data
```

<h3>원 그래프(점유율)</h3>

```R
data= c(21.6,22.3,16.4,15.7,9.9,14.2)

labels=c('LGD 21.6%', 'BOE 22.3%', 'AOU 16.4%', 'Innolux 15.7%', 'Samsung 9.9%', 'Others 14.2%')



mycolor=c(colors()[1],colors()[13],colors()[53],colors()[45],colors()[23],colors()[18])

title=c("Global large-area display market share 2017.1")



pie(data,labels,col=mycolor,main=title)

```

<h3>상자 그림</h3>
R을 이용하여 상자그림을 그리는 방법을 알아봅시다. 아래와 같은 그림이 상자그림인데요. 점선부분이 수염처럼 생겼기 때문에 상자수염그림이라고도 부릅니다

```R
> x=c(1,2,3,4,5)

> boxplot(x)

> x=c(1,2,3,4,5,10)

 > boxplot(x)
```

<h3>산점도</h3>
x축과 y축으로 이루어진 그래프에 두 변수의 값을 점으로 나타낸 그래프이다.

삼점도를 이용하면 두 변수의 관계를 파악하는데 용이하다.


```R

> #자료생성
> group<-c(1,1,1,2,2,2,2,2,1,1,2,1)
> age<-c(12,15,29,22,40,33,31,38,12,30,25,19)
> weight<-c(30,45,58,50,61,65,50,51,28,62,50,40)
> dat<-cbind(group,age,weight)
> dat
      group age weight
 [1,]     1  12     30
 [2,]     1  15     45
 [3,]     1  29     58
 [4,]     2  22     50
 [5,]     2  40     61
 [6,]     2  33     65
 [7,]     2  31     50
 [8,]     2  38     51
 [9,]     1  12     28
[10,]     1  30     62
[11,]     2  25     50
[12,]     1  19     40

 
> #plot( )함수를 적는 방법은 두 가지가 있다. 
> plot(x=age,y=weight)          
> plot(formula=weight~age, data=dat)

```




<h2>[04월 27일] 학습내용</h2>

## 

<h3>막대 그래프</h3>

R에서 막대그리프를 그려주는 함수는 barplot() 입니다.


```R
mydata=c(5,8,3)

barplot(mydata,names=c("A","B","C"))
```

<h3>중첩 그래프</h3>
중첩 그래프는 하나의 막대가 여러 데이터를 포함하고 있는 그래프

```R
A=c(1,3,5)

B=c(2,4,6)

C=c(3,4,6)

mat=matrix(c(A,B,C),nrow=3,dimnames=list(c("1","2","3"),c("A","B","C")))

```

cbind 함수를 를 사용하여 행렬을 만듬

```R
> mat2=cbind(A,B,C)

> mat2

     A B C

[1,] 1 2 3

[2,] 3 4 4

[3,] 5 6 6
```

위 행렬의 '열'이 막대가 됩니다. 세로 방향이 층이 쌓이는 순서입니다. 예를들어 A데이터는 1,3,5라는 값으로 층이 쌓이는 결과가 나옴

```R
barplot(mat)
```

<h3>반복문</h3>

```bash
> for문

for(i in 1:10){ 
  print(i) 
}

```

```bash
> while문
i<-1 
while(i < 11){ 
  cat("\n",i) 
  i<-i+1 
}

```



<h2>[04월 13일] 학습내용</h2>

## 

<h3>파일 입출력</h3>

TXT 파일은 read.table ( ) 함수를 사용하여 데이터 프레임으로 가져올 수 있습니다. read.table ( ) 함수 사용 형식은 다음과 같습니다.

```bash
read.table(“원시 데이터“, header = FALSE, skip = 0, nrows = -1, sep = “”, … )

함수에 원시 데이터 파일 경로를 넣어주고, 필요하다면 옵션을 지정합니다. 옵션을 지정하면 원시 데이터를 원하는 데이터 프레임 형태로 가져올 수 있습니다. 아래는 read.table ( ) 함수에서 자주 사용 하는 옵션입니다.
```

*데이터 구분자 지정하여 가져오기

```bash
ex_data4 <- read.table("C:/Rstudy/data_ex1.txt", encoding = "EUC-KR", fileEncoding = "UTF-8", header = TRUE, sep = ",")
View(ex_data4)
```

```bash
*CSV 파일 가져오기

ex_data <-read.csv(“C:/Rstudy/data_ex.csv”)
View(ex_data)
```

```bash
*엑셀 파일 가져오기
excel_data_ex <- read_excel("C:/Rstudy/data_ex.xlsx")
View(excel_data_ex)

```

<h3>반복문</h3>

```bash
> for문

for(i in 1:10){ 
  print(i) 
}

```

```bash
> while문
i<-1 
while(i < 11){ 
  cat("\n",i) 
  i<-i+1 
}

```


<h2>[04월 06일] 학습내용</h2>

## 

<h3>데이터프레임 개념</h3>

```bash
행과 열을 갖는 2차원 표의 형태로 데이터를 저장하는 것을 R에서는 '데이터프레임(Data Frame)'이라고 합니다. 데이터프레임은 변수 역할을 하는 컬럼(column)과 관측값(observation, record)을 나열하는 행(row)를 가지고 있습니다.  다른 프로그램에서 표, 테이블(table)이라고 일컫는 것이 R에서는 데이터프레임입니다. 
```

<h3>iris</h3>


```bash
nrow(iris)
[1] 150

ncol(iris)
[1] 5

```

```bash
> head(iris,5)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa

```




<h3>데이터프레임 매트릭스로 변환</h3>

```bash
데이터프레임 정의
> md=data.frame(C1=c(1,2,3),C2=c(10,20,30))
> md
  C1 C2
1  1 10
2  2 20
3  3 30

```

```bash
매트릭스
> md_m=as.matrix(md)
> md_m
     C1 C2
[1,]  1 10
[2,]  2 20
[3,]  3 30

```

```bash
변환
> class(md_m)
[1] "matrix" "array"

```

```bash
데이터 입력
> myData = c("dog", "pig", "cat", "horse")
> myData
[1] "dog"   "pig"   "cat"   "horse"

```




<h2>[03월 30일] 학습내용</h2>

## 벡터

<h3>벡터 만들기</h3>

```bash
 x <- c(1,2,3) # 숫자형 벡터
 y <- c("a","b","c") # 문자형 벡터
 Z <- c(TRUE,TRUE, FALSE, TRUE) # 논리형 벡터
 x # x 에 저장된 값을 출력하라는 의미
```

<h3>벡터 연산</h3>

```bash
벡터 연결

 x <- c(1,2,3)
 y <- c(4,5)
 c(x,y) # 단순히 x,y 를 연결하여 출력
 # 1 2 3 4 5
 z <- c(x,y) # x,y 를 연결하여 z에 저장


```

```bash
벡터의 합

 x <- c(1,2,3) # x에 벡터 입력
 y <- c(4,5,6) # y에 벡터 입력
 x+y # 대응하는 원소끼리 + 하여 출력
 # 5 7 9
 z <- x + y # x,y 를 더하여 z에 저장
 
 벡터끼리 연산을 하려면 벡터의 길이가 같아야 한다

```




<h3>팩터</h3>

```bash
팩터란, 범주형 데이터를 표현할 때 사용하는 데이터 타입입니다. 예를 들어, 대중소와 같은 순서형(ordinal)팩터나, 남여와 같은 명목형(nominal)팩터를 만들 수 있답니다


```










<h2>[03월 16일] 학습내용</h2>

## R 언어의 특징
<h3>데이터 분석에 특화된 언어</h3>

```bash
R은 통계를 포함한 데이터 분석 작업에 활용할 목적으로 개발한 언어
R은 컴파일 과정 없이도 바로 실행하여 결과를 확인할 수 있음
R로 작성한 것을 '프로그램'이 아니라 스크립트(script)라고 부름
```

<h3>탄탄한 사용자 커뮤니티</h3>

```bash
R은 사용자층이 두텁기 때문에 다양한 커뮤니티가 존재함
초보자를 위한 학습 자료도 풍부하게 넘침
국내 검색 사이트를 통해서 찾을 수 있는 한글 자료들이 증가하는 추세
```


## R언어에 대해 알아봅니다

### R을 배우는 이유

```bash
- 4차 산업혁명
- 4차 산업혁명의 중심은 '데이터'
- 시대적 흐름은 데이터를 잘 다룰 줄 아는 기업과 개인이 경쟁에서 우위를 점할 수 있음을 의미임
- 컴퓨팅 사고와 데이터 활용 능력은 전공을 불문하고 어떤 분야로 진출하든 점점 더 중요한 스펙임
```

### R설치하는법

```bash
 1.R 공식 홈페이지에 접속한 후 왼쪽 메뉴 목록 중 Download 항목에 있는 [CRAN]을 클릭하여 CRAN Mirrors 페이지로 이동합니다.

*R 공식 홈페이지: https://www.r-project.org.

2.선택한 국가의 미러 사이트가 열리면 Download and Install R 영역에서 사용자의 운영체 제에 맞게 해당 링크를 클릭합니다. 여기서는 윈도우 운영체제를 기본으로 설명하므로 [Download R for Windows]를 클릭합니다.

3.R for Windows 페이지가 열리면 [install R for the first time]을 클릭합니다.

4.다운로드 마지막 단계입니다. R 버전과 함께 다운로드 링크가 표시됩니다. [Download R 4.1.x for Windows]를 클릭하여 설치 파일 다운로드를 시작합니다.
```

### R 스튜디오 설치

```bash
1.R 스튜디오 웹 사이트 상단 메뉴에서 [Products]에 위치한 [RStudio]를 클릭합니다.

2. 페이지가 바뀌면 스크롤을 내려 [RStudio Desktop]을 클릭합니다.

3. Open Source Edition과 RStudio Desktop Pro 선택 페이지로 이동하면 Open Source Edition의 [DOWNLOAD RSTUDIO DESKTOP] 버튼을 클릭합니다.

4.Download the RStudio IDE 페이지에서 화면을 내려 다시 한번 무료 버전을 선택합니다. RStudio Desktop의 [DOWNLOAD] 버튼을 클릭합니다.

5. 운영체제별 설치 파일 다운로드 목록이 표시됩니다. 사용자 환경에 맞는 링크를 클릭하여 설치 파일을 다운로드합니다.
```

### R스튜디오 화면 구성

```bash
파일 영역
- 플롯창
- 패키지창
- 도움말창
- 뷰어창

```




<h2>[03월 23일] 학습내용</h2>

## R스튜디오(패키지)
<h3>패키지 설치</h3>

```bash
install.packages("cowsay") 설치 코드
library(cowsay)
say(by="cow")

```
결과물

```bash
##
##  -----
## Hello world!
##  ------
##     \   ^__^
##      \  (oo)\ ________
##         (__)\         )\ /\
##              ||------w|
##              ||      ||

```


<h3>변수</h3>

```bash
변수란? 어떤 값을 보관하는 공간을 변수라고 합니다.
우리가 프로그래밍을 유연하게 하기 위해서 변수를 선언해서 사용하는 것이 중요합니다.

a <- 1
b = 2
c <- a*2

```


## 벡터


```bash
a <- c("a","b","c")
b <- c(1,2,3)
c <- c(TRUE,FALSE,TRUE)

```

동일한 자료 타입을 가지는 리스트라고 생각하시면 됩니다.

자료 타입이 다른 경우에는 벡터가 될 수가 없습니다.


만약 자료 타입을 다르게 선언하면 하나의 자료 타입으로 통일되게 됩니다


### R 함수

```bash
R 함수 정의


f <- function(x1, x2) {
  y <-  x1^2 + x2^2
  return(y)
}
```





<h2>[03월 16일] 학습내용</h2>

## R 언어의 특징
<h3>데이터 분석에 특화된 언어</h3>

```bash
R은 통계를 포함한 데이터 분석 작업에 활용할 목적으로 개발한 언어
R은 컴파일 과정 없이도 바로 실행하여 결과를 확인할 수 있음
R로 작성한 것을 '프로그램'이 아니라 스크립트(script)라고 부름
```

<h3>탄탄한 사용자 커뮤니티</h3>

```bash
R은 사용자층이 두텁기 때문에 다양한 커뮤니티가 존재함
초보자를 위한 학습 자료도 풍부하게 넘침
국내 검색 사이트를 통해서 찾을 수 있는 한글 자료들이 증가하는 추세
```


## R언어에 대해 알아봅니다

### R을 배우는 이유

```bash
- 4차 산업혁명
- 4차 산업혁명의 중심은 '데이터'
- 시대적 흐름은 데이터를 잘 다룰 줄 아는 기업과 개인이 경쟁에서 우위를 점할 수 있음을 의미임
- 컴퓨팅 사고와 데이터 활용 능력은 전공을 불문하고 어떤 분야로 진출하든 점점 더 중요한 스펙임
```

### R설치하는법

```bash
 1.R 공식 홈페이지에 접속한 후 왼쪽 메뉴 목록 중 Download 항목에 있는 [CRAN]을 클릭하여 CRAN Mirrors 페이지로 이동합니다.

*R 공식 홈페이지: https://www.r-project.org.

2.선택한 국가의 미러 사이트가 열리면 Download and Install R 영역에서 사용자의 운영체 제에 맞게 해당 링크를 클릭합니다. 여기서는 윈도우 운영체제를 기본으로 설명하므로 [Download R for Windows]를 클릭합니다.

3.R for Windows 페이지가 열리면 [install R for the first time]을 클릭합니다.

4.다운로드 마지막 단계입니다. R 버전과 함께 다운로드 링크가 표시됩니다. [Download R 4.1.x for Windows]를 클릭하여 설치 파일 다운로드를 시작합니다.
```

### R 스튜디오 설치

```bash
1.R 스튜디오 웹 사이트 상단 메뉴에서 [Products]에 위치한 [RStudio]를 클릭합니다.

2. 페이지가 바뀌면 스크롤을 내려 [RStudio Desktop]을 클릭합니다.

3. Open Source Edition과 RStudio Desktop Pro 선택 페이지로 이동하면 Open Source Edition의 [DOWNLOAD RSTUDIO DESKTOP] 버튼을 클릭합니다.

4.Download the RStudio IDE 페이지에서 화면을 내려 다시 한번 무료 버전을 선택합니다. RStudio Desktop의 [DOWNLOAD] 버튼을 클릭합니다.

5. 운영체제별 설치 파일 다운로드 목록이 표시됩니다. 사용자 환경에 맞는 링크를 클릭하여 설치 파일을 다운로드합니다.
```

### R스튜디오 화면 구성

```bash
파일 영역
- 플롯창
- 패키지창
- 도움말창
- 뷰어창

```





  <h2>[03월 09일] 학습내용</h2>
  
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



