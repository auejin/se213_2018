# lab #02

## Lecture #2 요약

### 네임스페이스(namespace)

변수가 저장되는 공간을 네임스페이스라고 한다. 네임스페이스를 아주 간단히 설명하면 변수의 이름과 값을 저장하는 공간이다. 이를 사람의 이름(변수명)과 전화번호(변수값)이 저장되는 것에 비유할 수 있다.

### 조건문 (if statement)

조건에 따라 다른 명령을 수행하기 위한 명령어.


```python
# 들여쓰기(indentation)의 의미
print('1st example')
a = 1
if a % 2 == 0:
    print('even')
    print('짝수')
print('---')

print('2nd example')
if a % 2 == 0:
    print('even')
print('짝수')
print('---')

# 조건을 만족하는 것이 여러개가 있어도 최초에 만족하는 조건만
print('3rd example')
a = 12
if a % 2 == 0:
    print('even')
elif a % 3 == 0:
    print('multiple of 3')
elif a % 4 == 0:
    print('multiple of 4')
```
```
1st example
---
2nd example
짝수
---
3rd example
even
```

## 수학 함수 사용하기

python에서 패키지란 자주 사용될만한 프로그램들을 미리 만들어놓고 프로그래머들이 사용하기 편하게 만들어놓은 것을 뜻한다. python용으로 10만개 이상의 패키지가 만들어져있다.

수학 패키지는 아래와 같이 math 패키지를 불러들이면 (import) 사용을 할 수 있다. math 패키지에 정의된 변수 혹은 함수는 `math.`를 접두어 불여서 사용할 수 있다.


```python
# using math
import math
# constants
print(math.pi)
print(math.e)

print(math.exp(2))       # return e ** 2
print(math.log(math.e))  # natural log
print(math.log10(100))   # log with base 10
print(math.sqrt(2))      # square root
# triangular functions
print(math.cos(math.pi / 2))
print(math.sin(math.pi / 2))
```
```
3.141592653589793
2.718281828459045
7.38905609893065
1.0
2.0
1.4142135623730951
6.123233995736766e-17
1.0
```

## 난수 만들기

난수를 만들기 위해서는 random 패키지를 이용한다.


```python
import random  # using random module
print(random.random())          # float, 0.0 <= x < 1.0
print(random.uniform(1, 10))    # float, 1.0 <= x < 10.0
print(random.randrange(10))     # int, 0 <= x < 10
print(random.randrange(1, 10))  # int, 1 <= x < 10
print(random.randint(1, 10))    # int, 1 <= x <= 10
# choice(): select one element in a given sequence
print(random.choice('abc'))
```
```
0.5936628610967284
9.30857147918338
4
6
3
c
```

### (추가 내용) random seed

컴퓨터에서 난수(random numbers)를 발생시키기 위해서는 (Pseudo) Random Number Generator, 즉 RNG를 이용합니다. RNG는 난수의 수열을 발생시키는데, 같은 RNG를 이용하면 동일한 순서의 난수의 수열을 만들게 됩니다.

난수의 수열을 시작하는 값을 random seed라고 합니다. python의 random 패키지는 운영체제(OS)에 따라 제공하는 방법으로 이 값을 임의의 값으로 지정하여, 프로그램을 실행할 때마다 다른 난수들을 발생시키도록 합니다.

그렇지만 프로그램을 테스트하거나 프로그램의 오류를 고칠 때(즉, 디버깅할 때)는 같은 순서의 난수가 발생되는 것이 편리한 경우가 있습니다. `random.seed()` 함수를 이용하면, 임의의 random seed를 지정할 수 있습니다. 이 함수에 대한 자세한 설명은 python 공식문서를 참조하기 바랍니다: https://docs.python.org/3/library/random.html#random.seed

예를 들어, 아래와 같이 `random.seed()` 함수를 사용하면 프로그램 실행을 할 때마다 같은 결과를 얻을 수 있습니다. (python 버전에 따라 사용되는 RNG가 다를 수 있고, 그것에 따라 결과값이 다를 수 있습니다. 그렇지만, 한 시스템에서 같은 버전의 python을 사용하는 경우에 실행할 경우, 계속 같은 결과를 얻을 수 있습니다.)
```python
import random
random.seed(0)
print(random.random())
print(random.random())
print(random.random())
```
```
0.8444218515250481
0.7579544029403025
0.420571580830845
```

`seed()` 함수의 인자로 다른 값을 주면, 다른 출력값을 얻게 됩니다. 그렇지만 그 경우에도 프로그램을 실행할 때마다 같은 결과를 얻을 수 있습니다.

## 연습 1: 2 혹은 3으로 나누어지는지 확인

사용자에게 정수를 입력받은 후, 그 수가 2 혹은 3으로 나눠지는지 혹은 2, 3으로 모두 나눠지는지 출력하는 프로그래을 작성하시오.

_연습 1과 연습 2는 어떻게 if문을 구성하면 가장 간단하게 구현할 수 있는지 생각해볼 것_

**실행예시 1**
```
Enter an integer number: 42
42 is divisible by 2.
42 is divisible by 3.
```

**실행예시 2**
```
Enter an integer number: 8
8 is divisible by 2.
```

**실행예시 3**
```
Enter an integer number: 9
9 is divisible by 3.
```

**실행예시 4**
```
Enter an integer number: 23
```
별도의 출력이 없음


## 연습 2: 2 혹은 3으로 나누어지는지 확인 (조금 다른 출력)

사용자에게 정수를 입력받은 후, 그 수가 2 혹은 3으로 나눠지는지 혹은 2, 3으로 모두 나눠지는지 출력하는 프로그래을 작성하시오.

_연습 1과 연습 2는 어떻게 if문을 구성하면 가장 간단하게 구현할 수 있는지 생각해볼 것_

**실행예시 1**
```
Enter an integer number: 42
42 is divisible by 2 and 3.
```

**실행예시 2**
```
Enter an integer number: 8
8 is divisible by 2.
```

**실행예시 3**
```
Enter an integer number: 9
9 is divisible by 3.
```

**실행예시 4**
```
Enter an integer number: 23
23 is not divisible by 2 or 3.
```

## 연습 3: 온도 변환 2

섭씨에서 화씨, 혹은 그 반대로 온도 변환을 하는 프로그램을 작성하시오.

먼저 온도(실수의 값을 처리할 수 있어야 함), 그리고 그 온도의 종류를 입력받고('c' 혹은 'C'를 입력하면 섭씨, 'f' 또는 'F'를 입력하면 화씨), 섭씨이면 화씨로 아니면 반대로 변경하는 프로그램을 작성하시오.

온도의 종류에 대한 입력값이 정확하지 않은 경우, 문자열 'Error in the kind of temperature scale!'을 출력하시오.

**주의: 대소문자 모두 처리되도록 할 것. 그리고 입력받는 온도의 종류는 입력받은 온도가 섭씨 혹은 화씨임을 의미함.**

**실행예시 1**
```
Enter a degree: 10
Enter the kind of temperature scale: c
50.0
```

**실행예시 2**
```
Enter a degree: 50
Enter the kind of temperature scale: F
10.0
```

**실행예시 3**
```
Enter a degree: 10
Enter the kind of temperature scale: cc
Error in the kind of temperature scale!
```

## 연습 4: 난수 3개의 합 구하기

_리스트와 반복문을 사용하지 않았을 때와 사용했을 때의 차이를 확인해볼 것_

먼저 사용자에게 정수 하나를 입력받은 후, 그 정수를 random seed로 사용한다. 그리고 정수 하나를 더 입력받고, 0이상 두 번째 입력받은 정수 미만의 정수 3개 난수로 발생시켜(`randrange()` 함수를 사용할 것), 그 3개의 숫자와 합을 출력하는 프로그램을 작성하시오.

_**앞의 부분은 main.py에 이미 포함되어 있으니, 참고하기 바랍니다.**_

**실행예시**
```
Enter a random seed: 1
Enter n: 10
9 4 7 20
```
