# Lab #4

## Lecture #4 요약

## 리스트 (list)

여러 값을 한 꺼번에 저장할 수 있는 공간.


```python
# t의 정의
t = [42, 1024, 6]
print(t[1]) # 1번째 (0부터 순서를 세기 시작)
print(t[1:3]) # 1번째에서 3번째 전까지, 즉 1번째 & 2번째

# 연산
print(len(t))     # t에 있는 item의 개수(length)
print(min(t))     # t중에 가장 작은 item
print(max(t))     # t중에 가장 큰 itm

print(sum(t))      # t에 있는 원소들의 합
print(t.count(42)) # t에서 42가 포함된 개수
```
```
1024
[1024, 6]
3
6
1024
1072
1
```


## 문자열 (str)

문자열은 문자(unicode 문자)로 이루어진 immutable sequence이다. 다른 sequence(예: list)에 대해 쓸 수 있는 많은 함수 혹은 연산을 문자열에도 쓸 수 있다.

```python
hello = 'Hello, '
world = 'World!'
new_string = hello + world
print(new_string)
print(len(hello), len(world), len(new_string))

character = '^'
print(character * 1)
print(character * 2)
print(character * 4)
print(character * 8)
print(character * 16)
```
```
Hello, World!
7 6 13
^
^^
^^^^
^^^^^^^^
^^^^^^^^^^^^^^^^
```

## while


```python
# 가장 간단한 경우
counter = 0
while counter < 3:
    print(counter)
    counter += 1
```
```
0
1
2
```

## for

```python
# 가장 간단한 for문
my_list = [42, 1024, 23]
for value in my_list: # my_list의 원소를 하나씩 value에 대입하고, code block을 실행
    print(value)
```
```
42
1024
23
```

### 가장 자주 쓰이는 for 구문 중 하나: range(len())

리스트 my_list의 원소에 대해서 인덱스가 필요한 경우에 자주 사용된다. 리스트에 저장된 값을 변경하는 등의 경우에, 인덱스가 필요하다.


```python
my_list = [42, 1024, 23]
for i in range(len(my_list)):
    my_list[i] = my_list[i] * 2
print(my_list)
```
```
[84, 2048, 46]
```

위의 예에서  `range(len(my_list))` 라는 표현식은 아래와 같이 평가(evaluate)된다
- `len(my_list)`는 원소의 개수를 반환한다. 즉 이 경우에는 3을 반환한다.
- 따라서 `range(len(my_list))`는 `range(3)`과 같은 의미를 뜻하게 된다. 즉 `[0, 1, 2]`를 준 것과 같은 결과가 된다.

여기서 유의할 것은 `range(len(my_list))`가 my_list의 원소들의 index 값들을 가지게 된다는 것이다. 즉 변수 i에 my_list의 원소들의 인덱스가 순차적으로 대입되고, for문 안의 코드블럭이 실행되게 된다. for문 안에서 `my_list[i]`와 같은 표현을 쓰면 i번째 원소를 접근할 수 있게된다.

## Recap: print() 함수: sep, end

print() 함수의 동작을 조금 더 자세하게 설명하면 다음과 같다.
- 첫번째 인자를 출력한다
- 두번째 인자가 있다면, sep를 출력하고 두번째 인자를 출력한다
- 세번째 인자가 있다면, sep를 출력하고 세번째 인자를 출력한다
- ...
- end를 출력한다

여기서 sep과 end는 키워드 인자(keyword argument 혹은 named argument)라 불리는 인자이다.

키워드 인자를 print() 함수에 넘겨주기 위해서는, 아래 예시와 같이 인자의 이름 뒤에

sep의 기본값은 ' '이고, end의 기본값은 '\n'이다. 즉 인자들 사이에는 빈칸 한 칸, 그리고 인자들을 모두 출력한 후, 줄바꿈을 한다.

sep=''와 같이 빈 문자열(아무 글자를 포함하지 않는 문자열)으로 지정하면, 인자들 사이에 공백이 생략된다. 즉, 모든 인자들이 붙어서 출력된다.

end=''와 같이 빈 문자열(아무 글자를 포함하지 않는 문자열)으로 지정하면, print() 함수 출력 뒤의 줄바꿈을 하지 않는다.


```python
print(1, 2, 3)
print(1, 2, 3, sep='')  # 인자들 사이의 공백을 없앰
print()                 # 줄바꿈 (end의 기본값만을 출력)
print(1, 2, 3, sep='*') # 인자들 사이에 *를 출력
print('\n')             # 두 줄 바꿈 ('\n' 때문에 한 번 줄 바꾸고
                        # end의 기본값을 출력해 다시 한 번 줄 바꿈)
print('apple', end='')  # 인자들을 출력한 후, 줄바꾸지 않음
print('pen')
```
```
1 2 3
123

1*2*3


applepen
```

## 연습 1: 구구단

구구단의 한 단을 출력하는 함수 `print_multiples(n)`과 구구단을 출력하는 함수 `print_multiplication_table()`을 작성할 것

**주의**: 지난 시간에 실습했던 내용과 동일하나, 이번에는 반복문을 사용해서 프로그램을 작성하시오.

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

## 연습 2: 문자열 삼각형

문자열 삼각형을 출력하는 `print_pyramid(n)`을 만드시오.

**매개변수**
- n: 정수. 출력할 줄 수

**함수의 동작**
- 문자열 삼각형은 `n`줄만큼 출력하면서, 각 줄에 `'*'` 를  1, 2, ..., n개씩 출력할 것

**함수사용예시**
```
print('First pyramid')
print_pyramid(5)
print('Second pyramid')
print_pyramid(3)
```
**실행 결과**
```
First pyramid
*
**
***
****
*****
Second pyramid
*
**
***
```

## 연습 3: 간단한 통계

사용자로부터 양의 정수를 입력받아, 입력된 수의 개수, 총합, 평균, 최대값, 최소값과 지금까지 입력받은 수를 모두 출력하는 프로그램을 작성할 것.

사용자로부터 양의 정수를 입력받아 리스트에 넣고 반환하는 함수 `input_numbers()`와 리스트를 전달받아 간단한 통계 결과를 보여주는 함수 `describe(input)`을 작성하시오.

### `input_numbers()`

**함수의 동작**
- 화면에 `'Enter a positive nunmber: '`를 출력하고 정수를 입력받는다
  - 입력받은 값이 양의 정수이면, 위의 동작을 반복
  - 입력받은 값이 0이면, 중단

**반환값**
- 입력받은 양의 정수들은 담은 리스트 (0은 포함하지 않음)

**주의**
반복문을 어떻게 구성하면 좋은지 잘 고민해볼 것.

### `describe(input)`

**함수의 동작**
- 리스트의 원소, 합, 평균, 최대값, 최소값, 그리고 원소들을 출력할 것

**반환값**
- 없음

**함수 사용 예시**
```python
positive_numbers = input_numbers()
describe(positive_numbers)
```

**실행예시**
```
Enter a positive number: 42
Enter a positive number: 1024
Enter a positive number: 23
Enter a positive number: 6
Enter a positive number: 28
Enter a positive number: 496
Enter a positive number: 0

The count of input numbers: 6
The sum of input numbers: 1619
The average of input numbers: 269.8333333333333
The max of input numbers: 1024
The min of input numbers: 6
The elements: [42, 1024, 23, 6, 28, 496]
```
