# Lab #03

## Lecture #03 요약

### 함수의 정의

```python
def function_name(parameters):
    statement_1
    statement_2
    ...
    statement_n
    return return_value # may be omitted
```

### 함수의 호출

```python
function_name(arguments)
```

### 함수의 인자 전달

인자가 계산(evaluate)된 후, 그 값이 매개변수로 **'전달'**됨


```python
def print_add(value1, value2):
    """Print the addition of two parameters"""
    print(value1 + value2)

print_add(42, 1024)
answer = 42
print_add(answer, 2 ** 10)
sum_value = print_add(42, 23)  # None is used since there is no return value
print(sum_value)
```
```
1066
1066
65
None
```

**주의**:

어떤 값을 계산하는 것, 어떤 값을 반환문으로 돌려주는 것, 그리고 어떤 값을 화면에 출력하는 것은 모두 다른 작업이다.

예를 들어, 위에 있는 함수의 예에서,
- `value1 + value2`의 표현식(expression)은 두 변수의 값을 더하는 계산하기 위한 것이고,
- 이 값이 화면에 출력되는 것은 `print()` 함수를 사용했기 때문이다. (어떠한 값을 계산해도 `print()`함수의 인자로 사용하지 않으면, 화면에 출력되지 않는다.)
- 또한 `return`문이 없기 때문에 어떠한 값도 반환되지 않는다. 즉 마지막에서 두 번째 줄에, `print_add()` 함수의 반환값이 없기 때문에 이것을 의미하는 `None`이 변수 `sum_value`에 대입된다

```python
def print_add(value1, value2):
    """Print the addition of two parameters"""
    print(value1 + value2)
    return value1 + value2

sum_value = print_add(42, 23)  # None is used since there is no return value
print(sum_value)
```
```
65
65
```

위의 예제에서는
- 밑에서 두 번째 줄에서
  - `print_add()` 함수가 호출되고
  - 이 때 함수 내부의 첫 번째 줄에서 `value1 + value2`를 계산하고, 이를 `print()` 함수를 이용하여 화면에 그 계산값이 65가 출력된다.
  - 두 번째 줄에서 `value1 + value2`를 계산하고, 이 값, 즉 65를 반환한다
  - 반환된 값 65가 변수 `sum_value`에 대입된다.
- 마지막 줄에서 `print()` 함수를 이용하여, `sum_value`의 값, 즉 65가 화면에 출력된다.

위의 함수의 실행을 python tutor에서 확인할 수 있다.
- [첫 번째 예제](http://pythontutor.com/visualize.html#code=def%20print_add%28value1,%20value2%29%3A%0A%20%20%20%20%22%22%22Print%20the%20addition%20of%20two%20parameters%22%22%22%0A%20%20%20%20print%28value1%20%2B%20value2%29%0A%0A%20%0Asum_value%20%3D%20print_add%2842,%2023%29%20%20%23%20None%20is%20used%20since%20there%20is%20no%20return%20value%20%0Aprint%28sum_value%29&cumulative=false&curInstr=5&heapPrimitives=false&mode=display&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false)
- [두 번째 예제](http://pythontutor.com/visualize.html#code=def%20print_add%28value1,%20value2%29%3A%0A%20%20%20%20%22%22%22Print%20the%20addition%20of%20two%20parameters%22%22%22%0A%20%20%20%20print%28value1%20%2B%20value2%29%0A%20%20%20%20return%20value1%20%2B%20value2%0A%0A%20%0Asum_value%20%3D%20print_add%2842,%2023%29%20%20%23%20None%20is%20used%20since%20there%20is%20no%20return%20value%20%0Aprint%28sum_value%29&cumulative=false&curInstr=7&heapPrimitives=false&mode=display&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false)


### 지역 변수

함수가 호출되면 네임스페이스가 만들어지고, 함수의 실행이 끝나면 이 네임스페이스는 소멸된다. 함수의 매개변수와 지역변수는 이 공간에 독립적으로 저장되기 때문에, 변수의 생성/변경이 함수 외부에 영향을 끼치지 않는다.


```python
def func(answer):
    print('The answer is', answer)
    answer = 23
    print('Now the answer is', answer)
    perfect = 28
    birthday = 23

answer = 42
perfect = 6
func(answer)
print('The answer is still', answer)
print('Perfect number is still', perfect)
print(birthday) # NameError: name 'birthday' is not defined
```

```
The answer is 42
Now the answer is 23
The answer is still 42
Perfect number is still 6


---------------------------------------------------------------------------

NameError                                 Traceback (most recent call last)

<ipython-input-2-a50055e16e94> in <module>()
     11 print('The answer is still', answer)
     12 print('Perfect number is still', perfect)
---> 13 print(birthday) # NameError: name 'birthday' is not defined


NameError: name 'birthday' is not defined
```


### 인자의 디폴트 값와 키워드 인자

python에서는 함수를 정의할 때, 기본값(default value)를 사용할 수 있다. 또한 함수를 호출할 때, 인자의 이름을 사용하여 임의의 순서로 인자를 전달할 수 있다.


```python
def func(a, b=5, c=10):
    print('a is ', a, 'and b is', b, 'and c is', c)

func(3, 7)
func(25, c=24)
func(c=50, a=100)
```
```
a is  3 and b is 7 and c is 10
a is  25 and b is 5 and c is 24
a is  100 and b is 5 and c is 50
```


## 연습 1: 화씨, 섭씨 변환 함수 작성

함수 `convert_temperature(degree, degree_type)` 함수를 작성할 것

* 매개변수
  - degree: 온도를 입력받는다. int 혹은 float 값을 사용자가 전달할 수 있도록 한다
  - degree_type: 온도가 섭씨인지, 화씨인지를 구분한다
    - 'c' or 'C': degree가 섭씨를 뜻함
    - 'f' or 'F': degree가 화씨를 뜻함
* 반환값: 온도를 변환된 값을 float으로 반환한다
  - degree_type이 'c' or 'C'인 경우: degree를 섭씨로 가정하고, 이것을 화씨로 변환하여 출력
  - degree_type이 'f' or 'F'인 경우: degree를 화씨로 가정하고, 이것을 섭씨로 변환하여 출력
  - degree_type이 위의 값들 중 하나가 아니면 None을 반환
    - 참고: 아무 것도 return하지 않거나 `return None`이라고 하면 `None`이 반환값으로 사용된다.

**함수 사용예시**
```python
print(convert_temperature(10, 'c'))
print(convert_temperature(50, 'F'))
print(convert_temperature(50, 't'))
```

**실행결과**
```
50.0
10.0
None
```


## 연습 2: 구구단 함수 작성

구구단의 한 단을 출력하는 함수 `print_multiples(n)`과 구구단을 출력하는 함수 `print_multiplication_table()`을 작성할 것

**주의**: 아직 반복문을 배우지 않았기 때문에, 직접 copy&paste(복붙...)을 이용해서 코드를 작성해야 함. 다음 주에 반복문을 배우고, 이 함수들을 다시 작성하면서 어떻게 간단히 줄일 수 있는지를 확인할 것임.

### `print_multiples(n)` 함수

* 매개변수
  - n: n단을 출력, n은 1과 9 사이의 정수
* 반환값: 없음(None)
* 함수의 동작
  - 1 <= n <= 9: 구구단의 n단을 출력하고, 줄을 바꿈
  - otherwise: 'Don't torture me!!!'를 출력

### `print_multiplication_table()` 함수

* 매개변수: 없음
* 반환값: 없음(None)
* 함수의 동작
  - 구구단을 출력한다
  - 반드시 `print_multiples()` 함수를 사용할 것
  - `while`문을 사용하지 말 것!!!


**함수 사용예시**
```python
print_multiples(3)
print_multiples(5)
print_multiples(-1)
print_multiplication_table()
```

**실행결과**
```
3 6 9 12 15 18 21 24 27
5 10 15 20 25 30 35 40 45
Don't torture me!!!
1 2 3 4 5 6 7 8 9
2 4 6 8 10 12 14 16 18
3 6 9 12 15 18 21 24 27
4 8 12 16 20 24 28 32 36
5 10 15 20 25 30 35 40 45
6 12 18 24 30 36 42 48 54
7 14 21 28 35 42 49 56 63
8 16 24 32 40 48 56 64 72
9 18 27 36 45 54 63 72 81
```


## 연습 3: 원의 둘레와 넓이를 구하는 함수

원의 둘레와 넓이를 구하는 함수 `circumference(radius)`와 `area(radius)`를 각각 구현하시오.

**주의**: 원주율의 값으로 `math.pi` 값을 사용할 것. 즉 `math` 패키지를 `import`하여 사용할 것

그리고 반지름 1-3개를 입력받아, 그 반지름을 가지는 원의 넓이의 합을 반환하는 함수 `sum_of_areas(radius1, radius2, radius3)`를 구현할 것. `radius2`와 `radius3`는 생략가능함. 인자가 생략된 경우, 그 인자에 대한 원의 넓이를 구할 필요는 없음.

**주의**
- 원의 넓이를 구하기 위한 표현식을 따로 만들지 말고 `area()` 함수를 이용할 것.
- 힌트: 기본값을 사용할 것. 그리고 기본값을 어떻게 지정하면 함수의 구현이 가장 간단한지 생각해볼 것.

**함수 사용 예시**
```python
r = 1.0
print(circumference(r), area(r))
r = 3.0
print(circumference(r), area(r))
print(sum_of_areas(1, 2, 3))
print(sum_of_areas(1))
```
**실행결과**
```
6.283185307179586 3.141592653589793
18.84955592153876 28.274333882308138
43.982297150257104
3.141592653589793
```
