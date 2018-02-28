# Lab #01

## Lecture #01 요약

### 기본자료형

* 부울 (bool): True, False
* 정수 (int): 1, 2, 3, 0, -1, -2, ...
* 실수 (float): 3.14, 1.0, 6.02e23
* 복소수 (complex): 1 + 2j, j, 1 + 4j
* 문자열 (str): '' 혹은 "" 안에 포함되어 있는 내용임. '' 혹은 ""은 문자열을 표시하는 내용이지, 문자열에 포함되지는 않는다.
  - 'Hello, World!'
  - "Hello, Wrold!'

### 수에 관한 연산 (일부)

* 덧셈: +
* 뺄셈: -
* 곱하기: \*
* 나누기: /
* (정수 나머지의) 몫: //
* (정수 나누기의) 나머지: %
* 지수: \*\*

### 변수: 자료를 저장하는 공간

* 변수이름 규칙
  - 첫글자: 문자 혹은 밑줄(\_)
  - 나머지 글자: 문자, 밑줄(\_), 숫자
* 변수에 값을 대입할 때는 =를 사용

### 입출력 함수
* `print()`
  - 인자의 값을 화면에 출력
  - 인자가 여러 개일 경우에는 빈칸(space)로 인자들을 구분

* `input()` **(추가 내용)**
  - 인자의 값을 화면에 출력
    - 인자를 문자열, 숫자 등이 가능함
    - 0개 혹은 1개의 인자만 전달할 수 있음
  - 사용자의 키보드입력을 반환값을 돌려줌

### 주석(comment) (추가 내용)
* python 프로그램에서 #부터 줄의 마지막까지는 무시되기 때문에, 코드에 대한 설명(즉, 주석) 등을 이것을 이용해서 적는다

## 자료형

### `type()` 함수를 이용한 자료형 확인

정수 42와 문자열 '42'는 `print()`함수로 그 값을 출력하면, 같은 결과가 출력된다. 그렇지만 컴퓨터에서는 다른 자료형으로 처리되고 있고, 이것을 `type()` 함수를 이용하여 확인할 수 있다.

```python
print(42)
print(42.0)
print('42')
print(type(42))
print(type(42.0))
print(type('42'))
```
    42
    42.0
    42
    <class 'int'>
    <class 'float'>
    <class 'str'>


### 자료형에 따른 연산


```python
print(1 + 2)
print(1.0 + 2.0)
print(1 + 2.0) # 정수와 실수의 연산은 정수 -> 실수로 자동으로 변환한다

print(4.7 // 2.3)
print(4.7 % 2.3)
# error: 문자열 '2'와 정수 2는 다른 자료형(data)이다
# 문자열과 수와 더하는 연산은 정의되어 있지 않다
print(1 + '2')
```

```
    3
    3.0
    3.0
    2.0
    0.10000000000000053
    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-2-f39e63963935> in <module>()
          7 # error: 문자열 '2'와 정수 2는 다른 자료형(data)이다
          8 # 문자열과 수와 더하는 연산은 정의되어 있지 않다
    ----> 9 print(1 + '2')


    TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

## 변수를 이용하기


```python
# 변수의 대입을 =을 사용: 오른쪽의 값을 왼쪽의 있는 변수에 대입
pi = 3.14159265359
print(pi)

r = 3 # r에 3을 대입
print(pi * r * r) # r을 반지름으로 하는 원의 넓이 계산

# (개념상으로) 위의 문장이 실행되는 순서
# print(pi * r * r)
# => print(3.14159265359 * 3 * 3) # 변수에 있는 값을 이용
# => print(9.424777960770001 * 3) # 연산자 우선 순위에 따라 계산
# => print(28.274333882310003) # 연산자 우선 순위에 따라 계산

r = 5 # r에 5를 대입
print(pi * r * r) # r을 반지름으로 하는 원의 넓이 계산

# 동일한 수식(expression)이지만, r에 어떤 값이 대입됐는지에 따라, 다른 값이 출력된다
```

    3.14159265359
    28.274333882310003
    78.53981633974999


## 키보드에서 입력받기: `input()`

`input()`은 사용자가 키보드에서 입력한 내용과 상관없이 문자열로 반환값을 돌려주기 때문에, 사칙연산 등을 위해서는 수(int, float 등)로 형변환이 필요하다.


```python
# 입력 내용과 상관없이 문자열로 저장됨
text = input('Enter any text: ')
print(text, type(text))
text = input('Enter any text: ')
print(text, type(text))
```

```
Enter any text: abc
abc <class 'str'>
Enter any text: 42
42 <class 'str'>
```  

## 형변환(type conversion)

python에서는 자료형에 따라 저장되는 방식, 또 그 자료에 대해서 할 수 있는 연산이 다르게 정의된다. 따라서 특정한 연산을 하기 위해, 하나의 자료형으로 저장된 데이터를 다른 자료형으로 바꾸는 것이 필요할 수 있다. 예를 들어, 문자열 '42'에 대해서 산술연산을 하기 위해서는, 문자열에 해당하는 정수로 자료형을 변환하는 작업, 즉 형변환(type conversion)이 필요하다.

python에서 자료형을 변경하고자 할 경우에는, 얻고자 하는 자료형의 이름을 함수 이름처럼 사용하고, 변경될 데이터를 함수의 인자로 사용하면, 형변환된 값이 반환된다.

```python
value = '42'
print(value, type(value))
converted_value = int(value)
print(converted_value, type(converted_value))
print(converted_value + 1)
print(value + 1)  # generate TypeError
```

```
42 <class 'str'>
42 <class 'int'>
43
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-9-89a1a75dcaf2> in <module>()
      4 print(converted_value, type(converted_value))
      5 print(converted_value + 1)
----> 6 print(value + 1)  # generate TypeError

TypeError: must be str, not int
```

`input()` 함수의 반환값은 문자열이기 때문에, 수에 관한 연산(예: 사칙연산)을 하기 위해서는 정수(int) 혹은 실수(float)로 형변환하는 것이 필요하다.

```python
value = input('Enter a number: ')
print(value, type(value))
int_value = int(value)
float_value = float(value)
print(int_value, type(int_value))
print(float_value, type(float_value))
```

```
42 <class 'str'>
42 <class 'int'>
42.0 <class 'float'>
```


## 연습 1: 이름 출력

사용자에게 성과 이름을 입력받아, 아래와 같은 형식으로 출력하는 프로그램을 작성할 것.
- 성, 이름
- 이름 성

**실행예시**
```
Enter your last name: Bond
Enter your first name: James
James Bond
Bond, James
```

## 연습 2: 온도 변환

사용자에게 섭씨온도를 입력받아, 이것을 화씨온도로 출력하는 프로그램을 작성할 것. 섭씨 온도(C)를 화씨온도(F)로 변경하는 수식은 아래와 같다.

$$ F = C \times \frac{9}{5} + 32 $$

**실행예시**
```
Enter a degree: 10
-12.222222222222221
```

## 연습 3: 만유인력 계산

사용자에게 두 물체의 질량과 거리를 입력받아, 만유인력에 의해 가해지는 힘을 계산하는 프로그램을 작성할 것. 만유인력의 공식과 중력상수 G의 값은 아래와 같다.

$$ F = G \frac{m_1 \cdot m_2}{r^2}, G = 6.67384 \times 10^{-11} $$

**실행예시**
```
Enter the mass of object 1 (kg): 5.972e24
Enter the mass of object 2 (kg): 1.989e30
Enter the distance between object 1 and object 2 (m): 1.496e11
The force between the object 1 and object 2 is 3.5421519355858047e+22 N
```
