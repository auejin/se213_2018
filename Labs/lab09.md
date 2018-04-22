# Lab #9: 텍스트 파일 입출력

## 파일 접근 방법

1. 파일 열기: `open(file, mode='r')`
  - mode
    - 'r': open for reading
    - 'w': open for writing, truncating the the file first
    - 'x': open for exclusive creation, failing if the file already exists
    - 'a': open for writing, appending to the end of the file if it exists
    - 'b': binary mode
    - 't': text mode (default)
    - '+': open a disk file for updating (reading and writing)
  - See also: https://docs.python.org/3/library/functions.html#open
1. 파일 읽기/쓰기
  - 읽기: `read()`
  - 쓰기: `print()`
1. 파일 닫기: `close()`

## pycharm 사용법

- [Pycharm tutorial](https://www.jetbrains.com/help/pycharm/creating-and-running-your-first-python-project.html)
  - Step 1 and Step 2

### 익힐 내용
1. pycharm 설치/실행 방법
1. python 프로젝트 만들기
1. python 파일 실행하기
1. debugger 사용하기
  - break point 설정하기
  - 한 줄씩 실행하기
  - 함수 끝까지 실행하기
  - 변수 내용 보기

**오늘 연습은 pycharm에서 실행할 것**

## 연습 1: 텍스트 파일 출력

아래 파일을 실행해보면서, 어떤 것이 화면에 출력되고, 어떤 것이 파일에 출력되는지 확인해보시기 바랍니다.

아래 내용을 바꾸면서 한 번 실행해보세요.
- filename 변수의 내용
- 3번째 줄에서 'wt'를 'at'로 바꿔볼 것
- print() 함수, 특히 file=f로 키워드 매개변수를 지정한 print() 함수를 추가해보고, 파일에 어떻게 출력이 되는지 확인해볼 것

```python
filename = 'test.txt'

with open(filename, 'wt') as f:
    print(filename, 'is opened for writing.')
    print(filename, file=f)
    for i in range(1, 10):
        for j in range(1, 10):
            print('%3d' % (i * j), sep='', file=f)
        print(file=f)
    print('Multiplication is written into the file', filename)

print(filename, 'is now closed.')    

```
```
test.txt is opened for writing.
Multiplication is written into the file test.txt
test.txt is now closed.
```

## 연습 2: 구구단 파일

multiplication_table.txt라는 파일에 구구단을 출력할 것
