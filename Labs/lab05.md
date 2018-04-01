
# Lab #5

## Lecture #5 요약

### list 함수들

- `list.insert(i, x)`: Insert an item at a given position. The first argument is the index of the element before which to insert, so `a.insert(0, x)` inserts at the front of the list, and `a.insert(len(a), x)` is equivalent to `a.append(x)`.
- `list.remove(x)`: Remove the first item from the list whose value is x. It is an error if there is no such item.
- `list.clear()`: Remove all items from the list. Equivalent to `del a[:]`.
- `list.sort(key=None, reverse=False)`: Sort the items of the list in place (the arguments can be used for sort customization, see `sorted()` for their explanation).
- `list.reverse()`: Reverse the elements of the list in place.
- `list.copy()`: Return a shallow copy of the list. Equivalent to `a[:]`.

```python
t1 = [42, 1024, 23]
print(t1)
t1.reverse()
print(t1)
t1.sort()
print(t1)
t1.insert(1, 6)
print(t1)
t1.remove(42)
print(t1)
t1.sort(reverse=True)
print(t1)
t1.clear()
print(t1)
```
```
[42, 1024, 23]
[23, 1024, 42]
[23, 42, 1024]
[23, 6, 42, 1024]
[23, 6, 1024]
[1024, 23, 6]
[]
```

### sort() v.s. sorted() (**new: 이론 시간에 설명하지 않은 내용**)

`sort()` 함수는 `list.sort()`와 같은 형태로 사용되고, `list` 안에 있는 원소들을 정렬하며 반환값은 없다.
`sorted()` 함수는 `sorted(list)`와 같은 형태로 사용되고, `list`에 있는 원소들이 정렬된 상태로 저장된 새로운 리스트를 만든다. 이 때 `list`에 있는 원소의 순서는 변경되지 않는다.


```python
t1 = [42, 1024, 23, 6, 28, 496]
t1.sort()
print(t1)
t2 = [42, 1024, 23, 6, 28, 496]
t3 = sorted(t2)
print(t2) # 변경되지 않음
print(t3)
```
```
[6, 23, 28, 42, 496, 1024]
[42, 1024, 23, 6, 28, 496]
[6, 23, 28, 42, 496, 1024]
```

### 리스트의 복사

리스트를 변수에 대입할 때, 리스트의 원소들은 네임스페이스가 아닌 별도의 공간(heap이라고 불리는 공간)에 저장되고, 변수에는 그 리스트에 대한 정보가 저장된다.

**advanced**

python에서 모든 자료(data)는 객체로 구성되어 있고, 모든 객체(object)는 고유의 식별자(identifier)를 가진다. 리스트로 객체의 일종으로, 리스트를 변수에 대입하면 리스트의 식별자가 변수에 저장된다. 어떤 변수에 저장된 값의 식별자는 `id()`함수를 이용해서 확인할 수 있다.

아래 프로그램의 첫 번째 줄에 실행될 때 python이 하는 작업은 아래와 같다.
- 42, 1024, 23을 원소로 가지는 리스트를 만들고, 고유한 식별한(unique identifier)를 생성한다.
- 변수 `t1`에 식별자를 저장한다


```python
t1 = [42, 1024, 23]
t2 = t1 # t2 points the same list t1 points
t3 = t1.copy() # make a new list
t4 = t1[:] # make a new list
print('--Before assignment--', t1, t2, t3, t4, sep='\n')
t2[2] = 6
t3[2] = 28
t4[2] = 296
print('--After assignment---', t1, t2, t3, t4, sep='\n')
print('Identifires of t1 through t4:', id(t1), id(t2), id(t3), id(t4))
```
```
--Before assignment--
[42, 1024, 23]
[42, 1024, 23]
[42, 1024, 23]
[42, 1024, 23]
--After assignment---
[42, 1024, 6]
[42, 1024, 6]
[42, 1024, 28]
[42, 1024, 296]
Identifires of t1 through t4: 4469131912 4469131912 4474049672 4474051144
```

### 튜플언패킹

튜플(혹은 리스트, 문자열 등 다른 시퀀스)의 원소들을 하나씩 변수에 대입하는 것을 튜플 언패킹이라고 한다. 다음 경우에 많이 사용된다.
- 두 변수의 값 교환
- 함수에서 2개 이상의 반환값을 전달하는 경우
- for문에서 enumerate() 함수를 이용해서 인덱스와 값을 모두 loop variable로 사용하는 경우


```python
# 간단한 튜플 언패킹 예시
my_tuple = (42, 1024, 23) # ()는 생략 가능
(a, b, c) = my_tuple # ()는 생략 가능
print(a, b, c)

# 두 변수의 값 교환
var1 = 'apple'
var2 = 'pen'
var1, var2 = var2, var1
print(var1, var2)
```
```
42 1024 23
pen apple
```

## 연습 1: 리스트의 원소에 상수배를 하는 함수 작성

함수 `multiple_by_a_constant(t, a)`를 아래와 같이 정의할 것

* 인자
  - t (list): 임의의 값을 원소로 포함하는 리스트
  - a (int): 리스트의 원소를 곱하기 혹은 반복할 회수
* 반환값
  - list: 전달받은 리스트, 즉 함수 내부에서 값이 변경한 리스트를 반환
* 동작
  - t에 전달된 리스트에 있는 각 원소에 a를 곱해줌. 즉 t의 원소가 변화함.

**함수 사용 예시**
```python
t = [42, 1024, 23]
multiply_by_a_constant(t, 2)
print(t)
multiply_by_a_constant(t, 10)
print(t)
multiply_by_a_constant(t, 0.5)
print(t)
s = ['i', 'love', 'python']
multiply_by_a_constant(s, 2)
print(s)
```

**실행 결과**
```
[84, 2048, 46]
[840, 20480, 460]
[420.0, 10240.0, 230.0]
['ii', 'lovelove', 'pythonpython']
```

## 연습 2: 리스트 두 개의 각각의 원소의 합을 구하는 함수

함수 `add(t1, t2)`를 아래와 같이 작성하시오.

* 인자
  - t1: 리스트
  - t2: 리스트
* 반환값
  - t1와 t2의 원소의 개수가 같은 경우
    - 새로운 리스트를 만들고, 각각 원소의 합을 저장함
    - t1과 t2의 원소는 변화하지 않음
  - t1와 t2의 원소의 개수가 다른 경우: `None`을 반환

**함수 사용 예시**
```python
t1 = [42, 1024, 23]
t2 = [6, 28, 496]
t3 = add(t1, t2)
print(t1)
print(t2)
print(t3)
t4 = add(t2, t2)
print(t2)
print(t4)
```

**실행 결과**
```
[42, 1024, 23]
[6, 28, 496]
[48, 1052, 519]
[6, 28, 496]
[12, 56, 992]
```

## 연습 3: 숫자 맞추기 게임

프로그램 내부에서 0-99사이의 정수 중 하나를 random하게 정하고, 이것을 사용자가 맞추는 게임을 작성하시오.

참고: `random` 모듈을 사용할 것.

아래는 컴퓨터가 발생한 난수가 27인 경우의 실행 예시임. (숫자는 사용자가 입력한 값임)
```
Enter your guess: 50
Too big!
Enter your guess: 25
Too small!
Enter your guess: 37
Too big!
Enter your guess: 28
Too big!
Enter your guess: 24
Too small!
Enter your guess: 26
Too small!
Enter your guess: 27
You got it!
```

**주의:** 채점 코드 없음
