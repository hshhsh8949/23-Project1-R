## 이름 :  함승현
---
## 강의날짜 : 2023-03-23
---
## 학습내용 :
 패키지 설치   
 R 스튜디오에서 패키지를 설치하기 전에 인터넷이 연결되어 있는지 확인...

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


