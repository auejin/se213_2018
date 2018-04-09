# Lab #6

## 복합자료구조: 다중리스트(리스트의 원소에 리스트가 저장된 경우)의 예시

[Link to the pythontutor](https://goo.gl/39QsFJ)

```python
# 다중리스트의 정의
students = [['Alice', 95], ['Bob', 80], ['Carol', 100]]

# 리스트 각각의 원소를 반복적으로 사용하기
print(students)
print(students[1])
print(students[1][0])

# 반복문 이용
for student in students:
    print('Name: ', student[0], ', Score: ', student[1], sep='')

# 반복문에서 튜플 언패킹 (이 경우에는 정확히 이야기하면 리스트 언패킹) 이용
for name, score in students:
    print('Name: ', name, ', Score: ', score, sep='')
```

```
[['Alice', 95], ['Bob', 80], ['Carol', 100]]
['Bob', 80]
Bob
Name: Alice, Score: 95
Name: Bob, Score: 80
Name: Carol, Score: 100
Name: Alice, Score: 95
Name: Bob, Score: 80
Name: Carol, Score: 100
```

## 문자열 서식화

```python
n = 42
f = 42.195
s = 'string cheese'
pi = 3.1415926535897932384626433832795028841971693

# 기본 사용. fieldname을 생략하면 순서대로 인자 사용
print('{} {} {}'.format(n, f, s))
# {} 이외의 부분은 문자열 그대로
print('The first argument is {}'.format(n))
print('{2} {0} {1}'.format(n, f, s)) # 인자 순서를 숫자로 지정
print('{0} is {0}'.format(n))        # 같은 인자를 여러 번 사용
# 이름을 이용해 인자지정
print('{integer} {realnumber} {string}'.format(integer=n,
                                               realnumber=f,
                                               string=s))
# 인자의 자료형 지정
# d: 정수, f: 실수, s: 문자열
# g: general format. 아주 크거나 작으면 지수로 표현
#    아니면 실수로 표현, 단 소수점 이하의 0은 생략
print('{:d} {:f} {:s}'.format(n, f, s))
print('{0:d} {0:f} {0:g}'.format(n))  # 정수를 실수로는 변환 가능
print('{0:f} {0:g}'.format(f))        # g를 사용하면 조금 더 보기편한 숫자를 표시함
#print('{0:d}'.format(f))              # 실수를 정수로 바꾸려고 하면 에러 발생

print('-' * 10)
print('{:10d}'.format(n))    # 10칸에 맞추어 출력
print('{:>10d}'.format(n))   # 오른쪽 정렬
print('{:<10d}'.format(n))   # 왼쪽 정렬
print('{:^10d}'.format(n))   # 가운데 정렬
print('{:.>10d}'.format(n))  # 빈 칸 대신 . 사용
print('{:_<10d}'.format(n))  # 빈 칸 대신 _ 사용
print('{:*>10d}'.format(n))  # 빈 칸 대신 * 사용
print('{:10.3f}'.format(pi)) # 소수점 이하 정밀값
print('{:10.5s}'.format(s))  # 문자열 중 몇 글자만 출력
```
```
42 42.195 string cheese
The first argument is 42
string cheese 42 42.195
42 is 42
42 42.195 string cheese
42 42.195000 string cheese
42 42.000000 42
42.195000 42.195
----------
    42
    42
42        
42    
........42
42________
********42
 3.142
strin     
```


## 연습 1: 문자열 서식화

위에서 설명한 문자열 서식화를 printf-style과 f-string으로 각각 구현해 볼 것.

**참고**
- 빈 칸 대신 `.`, `_`, `*`를 사용하는 것은 printf-style로는 구현가능하지 않다.

**참고**: 채점 코드가 없음

## 연습 2: min-max

이중 리스트가 주어졌을 때, 이중 리스트 내부에 있는 리스트들의 최대값들의 최소값을 구하는 함수 `minmax()`를 구현하시오.

**인자**
- nested_list: list를 원소로 포함하는 list
  - 한 가지 자료형만을 가진 list(안 쪽에 포함된 리스트)들을 포함하는 리스트. 즉, 자료형이 다른 것을 처리해줄 필요는 없음

**반환값**
- 안 쪽에 포함된 리스트의 자료형: 안 쪽에 포함된 리스트들의 최대값 중 최소값을 반환

**함수 사용 예시**
```python
example1 = [[1, 2], [3, 4], [5, 6]]
example2 = [[42, 1024, 23], [6, 28, 496], [2, 3, 5, 7, 11]]
example3 = [['programming', 'linear algebra'],
            ['operating systems', 'computer architecture']]
print(minmax(example1))
print(minmax(example2))
print(minmax(example3))
```
```
2
11
operating systems
```

## 연습 3: 문자열 피라미드

문자열 피라미드를 만드는 `pyramid(char, n, alignment=-1)` 함수를 구현하시오.

**Optional**
같은 동작을 하는 프로그램을 문자열 서식화를 이용하지 않고 만들어보고, 문자열 서식화를 이용해서 만들어 보면 도움이 됨.

**인자**
- char: 한 글자를 포함한 문자열
  - 한 글자가 아닌 경우에는 반환값에 나타난대로 `None`을 반환해야 함
- n: 0 이상의 정수
  - 문자열 피라미드를 몇 칸에 맞추어서, 그리고 몇 줄에 걸쳐 만들 것을 지정
- alignment: -1, 0, 1 중 하나의 값
  - -1: 왼쪽에 char를 맞추어 문자열 피라미드를 만듦 (기본값)
  - 0: 가운데에 char를 맞추어 문자열 피라미드를 만듦
  - 1: 오른쪽에 char를 맞추어 문자열 피라미드를 만듦

**반환값**
- 문자열: 아래 조건에 맞춘 문자열 피라미드를 포함하는 문자열
  - 문자열 char에 포함된 문자의 수가 1이 아닐 때: `None` (문자열 'None'이 아닌 `None`값)
  - 문자열 cahr에 포함된 문자의 수가 1일 때: n개의 줄을 가지는 문자열을 반환함
    - 1번째 줄에 char 1개, 2번째 줄에 char 2개, ..., n번째 줄에 char를 n개 포함
    - 각 줄은 (공백을 포함한) n개의 문자열로 만드는데, 이 때 char들을 alignment의 값에 따라 포함함. alignment의 의미는 **인자**에 있는 내용을 참고할 것.

**함수 사용 예시**

```python
print("Output of pyramid('**', 3)")
print(pyramid('**', 3))
print("Output of pyramid('+', 3)")
print(pyramid('+', 3))
print("Output of pyramid('*', 5)")
print(pyramid('*', 5))
print("Output of pyramid('*', 5, 0)")
print(pyramid('*', 5, 0))
print("Output of pyramid('*', 5, 1)")
print(pyramid('*', 5, 1))
```
```
Output of pyramid('**', 3)
None
Output of pyramid('+', 3)
+  
++ 
+++

Output of pyramid('*', 5)
*    
**   
***  
**** 
*****

Output of pyramid('*', 5, 0)
  *  
 **  
 *** 
**** 
*****

Output of pyramid('*', 5, 1)
    *
   **
  ***
 ****
*****
```

