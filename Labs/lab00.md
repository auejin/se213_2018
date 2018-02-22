# Lab #0

## 오늘 다룰 내용

1. elice 가입
1. anaconda 설치
1. pycharm 설치
1. python을 계산기처럼 사용해보기

## 1. elice 가입

elice는 웹기반의 python 실행환경이다. 프로그래밍 강의 초중반에는 elice를 사용하여 python 코드를 실행하게 될 것이다. 또한 과제의 제출도 elice를 통해서 제출하게 될 것이다.

1. https://dgist.elice.io/ 에 접속한다.
1. 오른쪽 상단의 '회원가입'을 클릭한 후, '이메일 가입'을 선택한다.
1. 이메일, 비밀번호, 이름을 넣고 가입한다.
  - 이메일: dgist 이멜을 사용
  - 이름: *한글*로 성과 이름을 입력
1. 가입한 이메일과 비밀번호를 이용하여 elice에 접속한 후, Programming 과목에 등록한다.
  - 강좌등록 비밀번호는 ```se213_2018```이다.
  - 비밀번호 오류가 계속 발생할 때는, 로그아웃 후 다시 로그인하면 해결되는 경우가 있다.

## 2. anaconda 설치 (Optional: 노트북에 설치시 필요)

anaconda는 python의 설치와 업그레이드를 편하게 해주는 도구이다.

1. https://www.continuum.io/downloads 에 접속하여, 본인이 사용하는 OS에 맞는 python 3.6 버전을 다운로드하여 설치한다.

참고: https://sites.google.com/site/se2132016/lab-notes/lab01

## 3. pycharm 설치 (Optional: 노트북에 설치시 필요)

pycharm은 python 개발을 위한 통합개발환경(IDE, integrated development environment)이다.

1. https://www.jetbrains.com/pycharm/download/ 에 접속하여, community 혹은 professional 버전을 다운로드 받는다.
  - community 버전은 무료
  - professional 버전은 유료인데, dgist email로 인증을 받으면 사용 가능함. web 개발을 위해서는 professional 버전이 필요함
    - https://www.jetbrains.com/shop/eform/students 에서 apply 하면 된다.

## 4. python을 계산기처럼 사용하기

python에서는 어떠한 값을 출력하기 위해서 `print()` 함수를 이용한다. ()안에 출력하고자 하는 내용을 적으면 출력이 된다. 사칙연산, 문자열 등을 출력할 수 있다.

```python
# print() 함수를 이용하여, 계산기처럼 사용할 수 있다

# #부터 줄의 끝까지는 python이 주석으로 인식한다. 즉, 이 부분은
# 어떤 명령어로 인식하지 않고, 무시하게 된다.

print(3)   # 정수
print(3.0) # 실수

print(2 + 3)
print(2 - 3)
print(2 * 3)
print(2 / 3)
print(2 // 3) # 정수형으로 나눗셈을 할 때는 //를 사용
print(2 ** 3) # 2 * 2 * 2

print('Hello, World!') # ''를 이용하여, 문자열을 나타낼 수 있다
print("Hello, World!") # ""도 ''와 마찬가지로 문자열을 나타낸다

print(1, 2, 3) # , 를 적으면 여러 값을 출력할 수 있다. 빈칸으로 구분된다.
print(2 * 2 * 2, 2 ** 3)
print('1+2+...+10 =', 1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10)
```

**실행결과**
```
3
3.0
5
-1
6
0.6666666666666666
0
8
Hello, World!
Hello, World!
1 2 3
8 8
1+2+...+10 = 55
```



