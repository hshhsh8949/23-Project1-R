## 이름 :  함승현
---
## 강의날짜 : 2023-04-27
---
## 학습내용 :

* 막대그래프 작성의 기초
* 도수분포표 계산하기
~~~r
favorite <- c('WINTER,  SUMMER','FALL', 'SUMMER', 'SPRING', 'SPRING')
favorite
table(favorite)


ds <- table(favorite) # 도수 분포표 저장
ds  # 도수분포표 내용 확인
barplot(ds, main = 'Favorite season' col = 'red')    #막대그래프 나옴


barplot(ds, main = 'Favorite season', col = c('red', 'blue'  ), xlab='계절', ylab='빈도수' )  
  #막대그래프 나옴   색깔을 차례로 넣을수도 있다.

xlab='계절'  # x축 설명
 ylab='빈도수' # y축 설명

horiz = true   # 수평
names=c('FA','SP','SU','WI')  # 네임 변경
las = 2  # 그룹이름을 수직으로 변경  3까지 있음


#중첩 그래프 
age.A <- c(13709,10974,7979,5000,4250)
age.B <- c(17540,29701,36209,33947,24487)
age.C <- c(991,2195,5366,12980,19007)

ds <- rbind(age.A,age.B ,age.C)
colnames(ds) <- c('1970','1990','2010','2030','2050')
ds
barplot(ds, main='인구 추정', col=rainbow(3), beside=TRUE,legend.text=TRUE,args.legend = list(x='topright', bty='n', inset=c(-0.25,0)))


beside=TRUE #그래프가 옆으로 누움
legend.Text = TRUE #색인
args.legend = list(x='topright', bty='n', inset=c(-0.25,0))  # 위치를 바꿀수 있다.
par(mfrow=c(1,1), mar=c(5,5,5,7))


# 범례 내용 바꾸기   legend.text
barplot(ds, main='인구 추정', col=rainbow(3), beside=TRUE,
        legend.text = c('0~14세','14~64세','65세이상')  ,
        args.legend = list(x='topright', 
        bty='n', inset=c(-0.25,0))   
          )

#히스토그램
head(cars)
dist <- cars[,2]     #자동차 제동거리
dist
hist(dist,           #데이타
     main = 'Histogram for 제동거리',   #제목
     xlab ='제동거리',    #x축축
     ylab = '빈도수',#y축
     border='blue', 
     col='green',
     las=2,
     breaks=5)   #막대개수조절절

# 매개변수
border='blue' 

freq <- result$counts  #구간별 빈도수 저장
names(freq) <- result$breaks[-1]   #구간값을 이름으로 지정
freq    # 구간별 빈도수 출력

#그래프 4분면 표시
par(mfrow=c(2,2), mar=c(3,3,4,2))

hist(iris$Sepal.Length,
     main='sepal.length',
     col='orange')

barplot(table(mtcars$cyl),
        main='mtcars',
        col=c('red','green','blue'))

barplot(table(mtcars$gear),
        main='mtcars',
        col=rainbow(3),
        horiz=TRUE)

pie(table(mtcars$cyl),
        main='mtcars',
        col=topo.colors(3),
        radius=2)

par(mfrow=c(1,1), mar=c(5,4,4,2)+.1)
#4분면 초기화


# save할때는 확장자를 미리 정해주고 저장 할것

# barplot , hist , par
# 함수 3개 


# 원그래프 선그래프 그리기
# 원그래프 작성
favorite <- c('WINTER,  SUMMER','FALL', 'SUMMER', 'SPRING', 'SPRING')
ds <- table(favorite) # 도수 분포표 저장
ds  # 도수분포표 내용 확인

pie(ds, main='선호 계절', radius=1)
# 똑같이 컬러값 지정 가능

#3D로 변경
install.packages('plotrix')
library(plotrix)
pie3D(ds, main='선호 계절', radius=1)

explode = 1  # 원그래프 간의 간격

# 선그래프 작성
month = 1:12
late = c(5,8,7,9,4,6,12,13,8,6,6,4)
plot(month,
     late,
     main='지각생 통계',
     type='l',   #그래프 종류 선택(알파벳)
     lty=1,    #선의 종류 선택
     lwd=1,    #선의 굵기 선택
     xlab='month',
     ylab='Late cnt')













~~~


  





---
## 강의날짜 : 2023-04-13
---
## 학습내용 :

~~~R
a <- 10; b<-20
sink('result.txt', append=T)
cat('a+b=', a+b, '\n')
sink()
* 출력할 파일이름에 값이 나옴

> airquality.txt
head(air)
View(air)

# if_else문 
job.type <- 'a'
if(job.type == 'b') {
  bonus <- 200
}else{
  bonus <- 100
}
print(bonus)


a <- 10
b <- 20
if(a > 5 & b >5) {
  print(a+b)
}
if(a > 5 | b >5) {
  print(a+b)
}

# ifelse문 조건에 따라 선택할 값이 각각 하나씩이면 이용하는 것이 편리

c <- ifelse(a>b, a,b)
print(c)
[1] 20

# for문 
# 반복 범위는 반복 변수에 할당할 값을 모아둔 벡터
> for(i in 1:5){
+   print('*')
+ }
[1] "*"
[1] "*"
[1] "*"
[1] "*"
[1] "*"

# 구구단
for( i in 1:3) {
  cat('2 *', i,'=', 2*i, '\n')
}

# while문
sum <- 0
i <- 1
while(i <-100) {
  sum <- sum  + i
  i <- i +1
}
print(sum)

# apply() 계열 함수
(데이터셋, 행/열 방향 지정, 적용함수)

apply(iris[,1:4], 1, mean)    
# 행 방향으로 함수 적용
apply(iris[,1:4], 2, mean)    
# 열 방향으로 함수 적용

# 사용자 정의 함수의 개념
#사용자가 스스로 만드는 함수
mymax <- function(x,y) {
  num.max <- x
  if (y >x){
    num.max <- y
  }
  return(num.max)
}

mymax (10, 15)
a <- mymax(20, 15)
b <- mymax(31, 45)
print(a+b)




mydiv <- function(x,y=2) {
  result <- x/y
  return(result)
}

getwd()
### source('mydiv.r')  디렉토리에 있어야~~
source('mydiv.r')

a <- mydiv(x=10, y=3)
b <- mydiv(10,3)
c <- mydiv(0)

print(a)
print(b)
print(c)

#which문  데이터 분석을 하다보면 어디에 위치하는디 알아야 할 떄가 있음
> score <- c(76,84,69,50,95)
> which(score==69)
[1] 3
> which(score>=85)
[1] 5
> max(score)
[1] 95
> which.max(score)
[1] 5
> min(score)
[1] 50
> which.min(score)
[1] 4

> idx <- which(score <=60)
> score[idx] <- 61
> score
[1] 76 84 69 61 95
> 
> idx <- which(score <=80)
> score.high <- score[idx] 
> score.high
[1] 76 69 61



~~~



---
## 강의날짜 : 2023-04-06
---
## 학습내용 :
* 행과 열에 이름 붙이기
~~~R
> score <- matrix(c(90,85,69,78,85,96,49,95,90,80,70,60),
+ nrow=4)
> score
     [,1] [,2] [,3]
[1,]   90   85   90
[2,]   85   96   80
[3,]   69   49   70
[4,]   78   95   60



> rownames(score) <- c('john','tom','mark','jane')
> colnames(score) <- c('english','math','science')
> score
     english math science
john      90   85      90
tom       85   96      80
mark      69   49      70
jane      78   95      60



> score['john','math']
[1] 85
> score['tom',c('math','science')]
   math science 
     96      80 
> score['mark']
[1] NA
> score['mark',]
english    math science 
     69      49      70 
> score[,'english']
john  tom mark jane 
  90   85   69   78 
> rownames(score)
[1] "john" "tom"  "mark" "jane"
> colnames(score)
[1] "english" "math"    "science"
> colnames(score)[2]
[1] "math"


> city <- c("seoul", "tokyo","washington")
> rank <- c(1,3,2)
> city.info <- data.frame(city, rank)
> city.info
        city rank
1      seoul    1
2      tokyo    3
3 washington    2


> iris[1:5,c(1,3)]
  Sepal.Length Petal.Length
1          5.1          1.4
2          4.9          1.4
3          4.7          1.3
4          4.6          1.5
5          5.0          1.4



> colSums(iris[,-5])
Sepal.Length  Sepal.Width Petal.Length  Petal.Width 
       876.5        458.6        563.7        179.9 

#행열을 변화하는 t() 함수
> z <- matrix(1:20, nrow=4,ncol=5)
> z
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20
> t(z)
     [,1] [,2] [,3] [,4]
[1,]    1    2    3    4
[2,]    5    6    7    8
[3,]    9   10   11   12
[4,]   13   14   15   16
[5,]   17   18   19   20

> IR.1 <- subset(iris, Species == 'setosa')
> IR.1

# 매트릭스와 데이터프레임에 함수 적용
> a <- matrix(1:20,4,5)
> b <- matrix(21:40,4,5)
> a
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20
> b
     [,1] [,2] [,3] [,4] [,5]
[1,]   21   25   29   33   37
[2,]   22   26   30   34   38
[3,]   23   27   31   35   39
[4,]   24   28   32   36   40
> a*b
     [,1] [,2] [,3] [,4] [,5]
[1,]   21  125  261  429  629
[2,]   44  156  300  476  684
[3,]   69  189  341  525  741
[4,]   96  224  384  576  800

# 매트릭스와 데이터프레임의 자료구조 확인하기
> class(iris)
[1] "data.frame"
> class(state.x77)
[1] "matrix" "array" 
> is.matrix(iris)
[1] FALSE
> is.data.frame(iris)
[1] TRUE
> is.matrix(state.x77)
[1] TRUE
> is.data.frame(state.x77)
[1] FALSE

> st <- data.frame(state.x77)
> is.matrix(st)
[1] FALSE

# 데이터 프레임을 매트릭스로 변환
> is.data.frame(iris[,1:4])
[1] TRUE
> iris.m <- as.matrix(iris[,1:4])
> head(iris.m)
     Sepal.Length Sepal.Width Petal.Length Petal.Width
[1,]          5.1         3.5          1.4         0.2
[2,]          4.9         3.0          1.4         0.2
[3,]          4.7         3.2          1.3         0.2
[4,]          4.6         3.1          1.5         0.2
[5,]          5.0         3.6          1.4         0.2
[6,]          5.4         3.9          1.7         0.4
> class(iris.m)
[1] "matrix" "array" 


> age <- c(28,17,35,46,23,67,30,50)
> age
[1] 28 17 35 46 23 67 30 50
> young <-min(age)
> old <-max(age)
> cat(young,old)
17 67

##########
#install.packages('svDialogs')
library(svDialogs)
user.input <- dlgInput('Input income')$res
user.input
income <- as.numeric(user.input)
income
tax <- income * 0.05
cat('세금:', tax)

~~~

* print()함수와 cat()함수
~~~R
> result
[1] 14.14214

> x <- 26
> y <- '입니다'
> z <- c(10,20,30,40)
> print(x)
[1] 26
> print(y)
[1] "입니다"
> print(iris[1:5,])
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
> print(x,y)
Error in print.default(x, y) : invalid printing digits -2147483648
In addition: Warning message:
In print.default(x, y) : NAs introduced by coercion

> cat(x,y)
26 입니다

~~~
* 작업폴더 : 자신이 읽거나 쓰고자 하는 파일이 위치하는 폴더

* csv 파일 읽기와 쓰기

~~~R
> getwd()
[1] "C:/Users/seung/Documents"
> air <- read.csv('airquality.csv', header=T)
> head(air)
  Ozone Solar.R Wind Temp Month Day
1    41     190  7.4   67     5   1
2    36     118  8.0   72     5   2
3    12     149 12.6   74     5   3
4    18     313 11.5   62     5   4
5    NA      NA 14.3   56     5   5
6    28      NA 14.9   66     5   6
> class(air)
[1] "data.frame"

> my.iris <- subset(iris, Species == 'setosa')
> head(my.iris)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
# 파일만들기 csv
> write.csv(my.iris, 'my_iris.csv', row.names=F) #행 이름 없는 상태



install.packages('xlsx')
library('xlsx')
air <- read.xlsx('C:/Users/seung/Documents/airquality.xlsx'), header=T,
sheetIndex=1)
head(air)

~~~












---
## 강의날짜 : 2023-03-30
---
## 학습내용 :

* ls()   지금 변수가 뭐뭐있는 보여준다.
* rm()   변수 넣으면 제거
* rm(list = ls() )   리스트에 있는 변수를 다지움 
~~~
 자료 분석의 목적과 사례

입욕제 사용자 분석  아이들 뿐만이 아닌 어른들도 구매를 한다는 데이터를 알수있다.
~~~

*   1차원 자료  -> 벡터  , 리스트 , 팩터
*   2차원 자료 -> 매트릭스 형태   ,데이터프레임
~~~
범주형 자료   -  분류의 의미를 갖는 값  보통 문자로 표현 산술연산을 적용
수치형 자료  -  값들이 크기를 가지며 산술연산이 가능
~~~

~~~R
벡터에 대한 산술연산
> d <- c(1,2,4,6,8)
> 2*d
[1]  2  4  8 12 16
> 3*d +4
[1]  7 10 16 22 28
> x <- c(1,2,3,4)
> y <- c(5,6,7,8)
> x + y 
[1]  6  8 10 12
> y <- c("a","b","c","d")
> x + y
Error in x + y : non-numeric argument to binary operator
> m <- c(y,x)
> m
[1] "a" "b" "c" "d" "1" "2" "3" "4"
~~~
* 평균값 -> mean(x)  

~~~r
> d <- 1:9
> d
[1] 1 2 3 4 5 6 7 8 9
> d >= 5
[1] FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE
> d [d>5]
[1] 6 7 8 9

sum(d>5) #5보다 큰 값의 개수를 출력 4가 나온다 6789가 있으니까

> sum(d [d>5])
[1] 30
~~~

~~~r
> e <- c(4,5,3)
> a <- c(63,68,64)
> c <- c(61,70,59)
> sale.e <- 2 * e
> sale.a <- 2.5 * a
> sale.c <- 3.0 * c
> sale.day <- sale.e + sale.a + sale.c 
> names(sale.day) <- c('mon','tue','wed')
> 
> sale.e <- 2 * e
> sale.e
[1]  8 10  6
> sale.day
  mon   tue   wed 
348.5 390.0 343.0 
~~~

* 팩터(factor)
문자형 데이터가 저장되는 벡터의 일종으로 저장되는 문자값들이 어떠한 종류를 나타내는 값일 때 사용
~~~r
> bt <- c('A','B','B','O','AB','A')
> bt.new <- factor(bt)
> bt.new
[1] A  B  B  O  AB A 
Levels: A AB B O
> bt
[1] "A"  "B"  "B"  "O"  "AB" "A" 
> bt[5]
[1] "AB"
> bt.new[5]
[1] AB
Levels: A AB B O
> levels(bt.new)
[1] "A"  "AB" "B"  "O" 
> as.integer(bt.new)
[1] 1 3 3 4 2 1
~~~

* as.integer() ==> 함수를 이용하여 팩터의 문자값을 숫자로 바꿀 수 있음 알파벳 순서에 따라 숫자값 부여

* 리스트 - 자료형이 다른 값들을 한곳에 저장하고 다룰수 있도록 해주는 수단

~~~r
> h.list <- c('balling', 'tennis','ski')
> person <- list(name='tom', age=25, student=TRUE, hobby=h.list)
> person
$name
[1] "tom"

$age
[1] 25

$student
[1] TRUE

$hobby
[1] "balling" "tennis"  "ski"    

> person[[1]]
[1] "tom"
> person[[4]]
[1] "balling" "tennis"  "ski"    
> person[[2]]
[1] 25
> person$name
[1] "tom"
~~~

~~~
2차원 자료의 저장
매트릭스 와 데이터 프레임은 2차원 자료를 저장하기 위한 대표적인 자료구조
(여러 주제로 데이터를 수집한 형태)

이 둘의 차이점은 모든 자료의 종류가 동일하나 프레임은 다른 종류의 자료가 들어갈수 있다.


~~~
* 매트릭스  - 2차원 테이블 구조 만들기
~~~r
> z <- matrix(1:20, nrow=4, ncol=5)
> z
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20

byrow=T  해주면  세로로 해준다.
> z <- matrix(1:20, nrow=4, ncol=5, byrow=T)
> z
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    2    3    4    5
[2,]    6    7    8    9   10
[3,]   11   12   13   14   15
[4,]   16   17   18   19   20


bind하는 방법에 따라 다르게 출력 
> x <- 1:4
> y <- 5:8
> z <- matrix(1:20, nrow=4, ncol=5)
> m1 <- cbind(x,y)
> m1
     x y
[1,] 1 5
[2,] 2 6
[3,] 3 7
[4,] 4 8
> m2 <- rbind(x,y)
> m2
  [,1] [,2] [,3] [,4]
x    1    2    3    4
y    5    6    7    8
> m3 <- rbind(m2, x)
> m3
  [,1] [,2] [,3] [,4]
x    1    2    3    4
y    5    6    7    8
x    1    2    3    4
> m4 <- cbind(z,x)
> m4
                  x
[1,] 1 5  9 13 17 1
[2,] 2 6 10 14 18 2
[3,] 3 7 11 15 19 3
[4,] 4 8 12 16 20 4



++ 매트릭스에서 값을 추출 할떄 
> z <- matrix(1:20, nrow=4, ncol=5)
> z
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20
> z[2,3]
[1] 10
> z[1,4]
[1] 13
> z[2,]
[1]  2  6 10 14 18
> z[,4]
[1] 13 14 15 16
> z[2,1:3]
[1]  2  6 10
> z[1,c(1,2,4)]
[1]  1  5 13
> z[1:2,]
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
> z[,c(1,4)]
     [,1] [,2]
[1,]    1   13
[2,]    2   14
[3,]    3   15
[4,]    4   16
~~~

---
## 강의날짜 : 2023-03-23
---
## 학습내용 :
 패키지 설치   
 R 스튜디오에서 패키지를 설치하기 전에 인터넷이 연결되어 있는지 확인함
+ R에서 install.packages() 함수를 이용하면 알아서 설치

+ library(ggplot2)
~~~R
ggplot(data = iris, aes(x = Petal.Length,  y=Petal.Width)) + geom_point()
~~~

+ library(cowsay)
~~~R
say("hello world", by="cat")
~~~

도움말 ->    ?sort 
현재 시간 날짜 -> Sys.time()
+ 변수  - 어떤값을 저장해 놓을 수 있는 보관 역할

~~~R
> total <- 5050
> total
[1] 5050
> print(total)
[1] 5050
> cat('합계', total)
합계 5050
~~~

~~~
변수명의 작명 규칙
* 첫 글자는 영문자나 마침표지만 점은 하지말고 일반적으로 시작하는  영문자로 시작
* 두번쨰 글자부터는 영문자 숫자 마침포 밑줄을 사용가능
* 특수문자를 사용하면 변수명으로 사용불가
* 변수명에서 대문자와 소문자는 별개의 문자 취급
* 변수명 중간에 빈 칸을 넣을 수 없습니다.
~~~

+ 자료형 - 변수에 저장할 수 있는 값의 종류

~~~r
벡터의 평균
score <- c(61,62,63,64,65,66,76,87,98)
mean(score)
~~~

* 벡터 - 
R에서 제공하는 여러 개의 값을 한꺼번에 저장하는 기능으로 일반적인 프로그래밍 용어로는 1차원 배열이라고도 함

목적은 여러개의 값들을 하나의 묶음으로 처리하기 위한 것
~~~R
연속적인 숫자로 이루어진 벡터
V1 <- 50:90
~~~

~~~r
> absent <- c(8,2,0,4,1)
> absent
[1] 8 2 0 4 1
> names(absent)
NULL
> names(absent) <- c('mon','tue','wed', 'thu','fri')
> absent
mon tue wed thu fri 
  8   2   0   4   1 
~~~

+ 인덱스 = R에서 벡터에 저장된 각각의 값들을 구별하기 위하여 앞쪽의 값부터 순서를 부여하는 것 
    d <- c(1,2,3,4,5)

+ 함수 =>  y = f(x)
 ~~~
* 함수의 매개변수
프로그래밍에서 함수의 입력값을 받는 변수를 매개변수라 함

함수의 정의에 맞추어 매개변수를 입력하면 정의된 결과값을 얻을 수 있음
 ~~~

~~~r
> pay <- paste(1:12,"월", sep="")
> pay
 [1] "1월"  "2월"  "3월"  "4월"  "5월"  "6월"  "7월"  "8월"  "9월" 
[10] "10월" "11월" "12월"
~~~











---
## 이름 :  함승현
---
## 강의날짜 : 2023-03-16
---
## 학습 내용 : 

~~~ r
R언어의 특징 
- 데이터 분석에 특화된 언어
        파이썬도 생각이 나야한다.
- 탄탄한 사용자 커뮤니티 
        오래된 언어라 풍부한 자료가 있다.  
        필요한 자료나 커뮤니티 등 있다.

- 다양한 패키지 제공   EX 코로나 통계 그래프

  미적이고 기능적인 통계 그래프 제공 
  데이터 분석에 있어서 분석결과를 시각적으로 제공

  편리한 프로그램 환경
  작업환경을 통합 개발환경 : IDE
~~~
+ R Studio 설치 2개를 같이 넣고 불러오면서 실행

~~~ r
- R을 배우는 이유 
    4차 산업혁명
    인공지능 빅데이터 로봇 사물인터넷 등 새로운 과학 기술이
    정치 경제 문화 전반에 미치면서 이를 수용하고 발전 가능성을 최대화 시키는 시대로  인공지능 ,빅데이터가 핵심기술 인식   
~~~
~~~ r
    4차 산업혁명의 중심은 '데이터'

    데이터 활용 능력은은 어떤 분야로 진출하든 점점 더 중요한 스펙
~~~
+ 무료 사용
    * 오픈소스 소프트웨어 1년에 2차례 지속적인 업데이트

~~~R
    5*10
    plot(1:10)  
    A <- 51:80
    print(A)
~~~
+ 화면 구성 
    * 소스영역 | 환경영역

    * 콘솔영역 | 파일영역
     
    파일이 4등분 되면서 확인
---
~~~R
    소스영역
    소스창 r명령문을 작성하고 실행하는 영역으로 메모장과 같은 문서 편집기와 유사함 
    run버튼클릭해야 명령문 실행

temp <- iris[,5]
 
    콘솔영역
        콘솔창 : 소스창에서 작성한 명령문을 실행시켰을때 실행과정 결과가 표시되는 영역
        키보드에서 엔터를 치면 바로 실행됨

        터미널 창 : 윈도우의  cmd와 동일한 기능을 제공


    환경영역
        환경창   주로 많이씀

        히스토리창   오류가 났을땐 볼수있을 것

        커넥션창

        튜토리얼창


    파일 영역
        파일창 - 윈도우의 파일탐색기와 동일한 기능 
        플롯창 - 그래프가 표시되는 영역
        패키지창 - 수많은 함수들을 제공
        도움말창  
        뷰어창
~~~
+ tetminal  =>  pwd하면 해당 경로를 보여줌
+ 주석 => #기호로 시작하여 뒤에 적는다  
~~~r
패키지 - 어떤 작업을 하느냐에 따라 필요한 패키지도 달라짐
스스로 만드는 것도 좋고 중요하지만 다른 사람들이 만들어 놓은 도구를 쓰는것이 효율적임
~~~


---
---
---





---
## 2023-03-09

1.   
***

-
~~~ html
HAM SEUNG HYEON
~~~


