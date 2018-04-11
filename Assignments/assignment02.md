# Assignment #2

## 과제 2-1: 중간고사 성적 정리

디지스트 2학년 학생들의 공통필수 교과들의 중간고사 점수를 정리하고자 한다. 아래와 같이, 공통필수 교과목들의 이름은 `course_titles`라는 리스트에, 그리고 중간고사 성적은 `midterm_scores`라는 리스트에 주어져 있다.

`midterm_scores`는 아래와 같이 구성되어 있다.
- 학생이름과 `course_titles`에 주어진 순서대로의 중간고사 성적이 저장된 리스트를 저장하는 리스트가 한 학생의 이름과 중간고사 성적을 나타냄
- 위와 같은 리스트를을 원소로 가지는 리스트가 `midterm_scores`이다.

아래와 같은 예에서, Alice와 Victor의 중간고사 성적은 아래와 같다.
- Alice의 선형대수, 세포와 생명현상, 프로그래밍 중간고사 점수는 각각 62, 60, 77
- Victor의 선형대수, 세포와 생명현상, 프로그래밍 중간고사 점수는 각각 82, 67, 94

```python
course_titles = ['Linear Algebra', 'Cell Biology', 'Programming']
midterm_scores = [
    ['Alice', [62, 60, 77]],
    ['Bob', [84, 88, 87]],
    ['Carol', [88, 88, 97]],
    ['Chuck', [92, 71, 93]],
    ['Craig', [81, 89, 72]],
    ['Dan', [79, 100, 97]],
    ['Erin', [76, 72, 65]],
    ['Eve', [69, 84, 67]],
    ['Faythe', [66, 60, 70]],
    ['Frank', [88, 76, 64]],
    ['Grace', [66, 77, 92]],
    ['Heidi', [93, 93, 82]],
    ['Mallory', [77, 89, 82]],
    ['Oscar', [67, 63, 67]],
    ['Peggy', [70, 81, 86]],
    ['Sybil', [96, 94, 62]],
    ['Trent', [67, 66, 61]],
    ['Trudy', [85, 74, 90]],
    ['Victor', [82, 67, 94]],
    ['Walter', [67, 84, 86]],
    ['Wendy', [97, 92, 66]]
]
```

중간고사 성적을 처리하기 위해서, 아래와 같은 함수를 작성하시오.

### `print_scores(test_scores, course_titles, student_name)`

* 인자
  - test_scores: 위의 midterm_score의 형태로 저장된 리스트
    - 이 함수를 잘 만들면 final_scores라는 리스트를 만들어서 재활용할 수도 있을지 모른다!
  - course_titles: 과목명(문자열)들이 저장된 리스트
  - student_name: 학생의 이름이 저장된 문자열
* 반환값
  - 없음
* 함수의 동작
  - 학생의 이름이 test_scores에 전달된 인자에 없는 경우: 학생이름이 없다고 출력을 한다, student_name이 'Emma'인 경우, 아래와 같은 출력을 한다.
    - There is no student name Emma.
  - 학생의 이름이 test_scores에 전달된 인자에 있는 경우: 학생들의 이름, 각 과목별 점수, 평균을 출력한다. 자세한 출력 형식은 아래 함수 사용 예시를 참고할 것

### `get_scores(test_scores, course_title, course_name)`
* 인자
  - test_scores: 위의 midterm_score의 형태로 저장된 리스트
    - 이 함수를 잘 만들면 final_scores라는 리스트를 만들어서 재활용할 수도 있을지 모른다!
  - course_titles: 과목명(문자열)들이 저장된 리스트
  - course_name: 과목 이름이 저장된 문자열
* 반환값
  - 과목의 이름이 없는 경우: None
  - 과목의 이름이 있는 경우: 리스트
    - course_name으로 지정된 과목의 점수들이 저장된 리스트

### `print_midterm_stat_by_course(course_name, subject_scores)`
* 인자
  - course_name: 과목 이름이 저장된 문자열
  - subject_scores: 과목의 점수를 저장한 리스트
* 반환값
  - 없음
* 함수의 동작
  - 교과 이름과 그 과목 점수의 평균, 최대, 최소값을 출력. 출력 형식은 함수 사용 예시를 참고할 것.

* 참고: 학생들의 이름은 암호/보안 연구에서 자주 사용되는 이름들을 차용했습니다.
  - 영어: https://en.wikipedia.org/wiki/Alice_and_Bob
  - 한국어: https://ko.wikipedia.org/wiki/%EC%95%A8%EB%A6%AC%EC%8A%A4%EC%99%80_%EB%B0%A5

### 함수 사용 예시

```python
print_scores(midterm_scores, course_titles, 'Alice')
print_scores(midterm_scores, course_titles, 'Oscar')
print_scores(midterm_scores, course_titles, 'Emma')

for course_name in course_titles:
    subject_scores = get_scores(midterm_scores, course_titles, course_name)
    print_midterm_stat_by_course(course_name, subject_scores)

```

```
Alice:
    Linear Algebra: 62
    Cell Biology: 60
    Programming: 77
    Average: 66.33333333333333
Oscar:
    Linear Algebra: 67
    Cell Biology: 63
    Programming: 67
    Average: 65.66666666666667
There is no student named Emma.
Linear Algebra: 78.7 97 62
Cell Biology: 79.4 100 60
Programming: 78.9 97 61
```

## 과제 2-2: 회문(回文, palindrome)

단어, 구문, 수 등이 앞에서 읽으나 뒤에서 읽으나 동일할 때, 회문([https://en.wikipedia.org/wiki/Palindrome](https://en.wikipedia.org/wiki/Palindrome))이라 한다. 회문의 예는 아래와 같은 것이 있다.
- madam
- noon
- I did, did I?
- Step on no pets
- No lemon, no melon
- 11
- 121
- 1001

또한 유전자의 정보에서도 회문과 비슷한 형태를 가지는 것을 palindromic sequence 혹은 간단히 palindrome이라 한다. (참고: [https://en.wikipedia.org/wiki/Palindromic_sequence](https://en.wikipedia.org/wiki/Palindromic_sequence))

유전자는 4가지 종류의 염기서열(A, T, C, G)로 이루어져있다. 염기서열은 결합이 될 수 있는 염기 서열이 정해져있다. A와 T, 그리고 C와 G만 결합이 가능하고, 다른 결합은 불가능하다.

어떠한 염기서열이 정해졌을 때, 그 염기서열과 결합할 수 있는 염기서열을 상보서열(complementary sequence 혹은 complement)라 한다. 예를 들어, ATCG의 complement는 TAGC로 주어진다.

palindromic sequence는 주어진 염기서열이 그것의 complement의 역순과 동일한 경우를 의미한다. 예를 들어, ACCTAGGT의 complement는 TGGATCCA이고, 이것의 역순은 원래의 염기서열과 동일하다. 따라서 이 서열은 palindromic sequence라고 정의된다. (아래 그림 참고: A 부분이 palindrome 혹은 palindromic sequence라 한다.) 염기서열에서 palindrome이 존재하면 염기서열에 loop, stem 등이 만들어질 수 있기 때문에, 염기서열을 분석할 때 palindrome을 찾는 것이 의미가 있다.

![palindromic sequence](https://upload.wikimedia.org/wikipedia/commons/7/75/DNA_palindrome.svg)
Source: wikipedia

아래 조건을 만족하는 함수들을 작성하시오.

### 문자열의 회문

#### `get_reverse_string(string)`

**인자**
- string: 문자열

**반환값**: 문자열
- string으로 주어진 문자열의 역순으로 된 문자열을 반환

**제한 조건** (아래의 입력은 항상 만족된다. 즉 아래 조건을 어기는 함수 입력값은 신경쓰지 않아도 된다)
- string에는 문자열만 입력된다고 가정한다.

**참고**
이 함수를 구현할 때, 인자로 문자열만 전달된다고 가정하셔도 됩니다. 그렇지만, 구현하는 방법에 따라, 임의의 시퀀스 자료형이 입력으로 오는 경우에 작동을 하도록 함수를 구현할 수도 있습니다. (입력된 인자가 어떤 자료형인지 하나하나 비교해서 별도로 만드는 것이 아니라, 같은 방법으로 여러 자료형에 대해서 처리가 되도록 만들 수 있습니다.)

예를 들어, `[2, 3, 5, 7]`이라는 리스트가 인자로 넘겨지면 `[7, 5, 3, 2]`라는 리스트가 반환되도록 만들 수 있습니다.

#### `is_palindrome(string)`

**인자**
- string: 문자열

**반환값**: 부울
- string이 회문일 경우는 True, 그렇지 않으면 False를 반환

**추가 조건**
- 반드시 `get_reverse_string()` 함수를 사용할 것

**제한 조건** (아래의 입력은 항상 만족된다. 즉 아래 조건을 어기는 함수 입력값은 신경쓰지 않아도 된다)
- string에는 문자열만 입력된다고 가정한다.

### 유전자 회문 (palindromic sequence)

#### `complement_sequence(dna_sequence)`

**인자**
- dna_sequence: 문자열. A, T, C, G의 염기서열을 저장한 문자열

**반환값**: 문자열
- dna_sequence의 complement를 문자열로 반환

**제한 조건** (아래의 입력은 항상 만족된다. 즉 아래 조건을 어기는 함수 입력값은 신경쓰지 않아도 된다)
- dna_sequence는 A, T, C, G 4가지 대문자만을 포함한다. 즉, 이 4가지 이외의 문자가 포함된 문자열은 인자로 전달되지 않는다고 가정한다


#### `is_palindromic_sequence(dna_sequence)`

**인자**
- dna_sequence: 문자열. A, T, C, G의 염기서열을 저장한 문자열

**반환값**: 부울
- dna_sequence가 palindromic sequence일 경우는 True, 그렇지 않으면 False를 반환

**제한 조건** (아래의 입력은 항상 만족된다. 즉 아래 조건을 어기는 함수 입력값은 신경쓰지 않아도 된다)
- dna_sequence는 A, T, C, G 4가지 대문자만을 포함한다. 즉, 이 4가지 이외의 문자가 포함된 문자열은 인자로 전달되지 않는다고 가정한다

**추가 조건**
- 반드시 `complement_sequence()` 함수를 사용할 것

### 함수 사용 예시와 실행 결과


```python
print('* Testing reverse_string()')
print(get_reverse_string('Hello'))
print(get_reverse_string('madam'))
print(get_reverse_string('I need more homework'))

print('* Testing is_palindrome()')
print(is_palindrome('madam'))
print(is_palindrome('Madam')) # 대소문자 구분
print(is_palindrome('hello'))
#print(is_palindrome([1, 2, 1]))

print('* Testing complement_sequence()')
print(complement_sequence('CGAT'))
print(complement_sequence('ATTCG'))

print('* Testing is_palindromic_sequence()')
print(is_palindromic_sequence('ATTCG'))
print(is_palindromic_sequence('GAATTC'))
print(is_palindromic_sequence('TCGA'))
```

```
* Testing reverse_string()
olleH
madam
krowemoh erom deen I
* Testing is_palindrome()
True
False
False
* Testing complement_sequence()
GCTA
TAAGC
* Testing is_palindromic_sequence()
False
True
True
```

## 과제 2-3: 순환하는 소수

어떤 수가 있을 때, 그 숫자와 그 순자를 회전시켜 나오는 모든 수가 소수인 경우, 그 수를 순환하는 소수라 한다.  예를 들어, 1193의 경우, 이 숫자를 (왼쪽 혹은 오른쪽으로) 순환하여 얻을 수 있는 숫자 1931, 9311, 3119 모두 소수이다. 따라서 이 수를 순환하는 소수라고 한다.

어떤 수가 순환하는 소수인지를 확인하기 위하여, 다음과 같은 함수를 작성하시오.

### `circular(n)`

자연수 n를 회전하여 만들 수 있는 모든 수를 원소로 포함하는 리스트를 반환할 것

**인자**
- n: 자연수

**반환값**: 리스트
- n과 n를 순환하여 얻을 수 있는 모든 수를 포함하는 리스트
  - n을 먼저포함하고, 왼쪽으로 회전시킨 순서대로 숫자를 포함할 것 (아래 함수 사용 예시와 실행 결과를 참고할 것)

**제한 조건** (아래의 입력은 항상 만족된다. 즉 아래 조건을 어기는 함수 입력값은 신경쓰지 않아도 된다)
- n는 항상 자연수가 전달된다고 가정한다.

### `prime(n)`

자연수 n이 소수인지를 확인하는 함수이다.

**인자**
- n: 자연수

**반환값**: 부울
- `True`: n이 소수일 때
- `False`: n이 소수가 아닐 때

**제한 조건** (아래의 입력은 항상 만족된다. 즉 아래 조건을 어기는 함수 입력값은 신경쓰지 않아도 된다)
- n는 항상 자연수가 전달된다고 가정한다.

### `circular_prime(n)`

자연수 n이 순환하는 소수인지를 확인하는 함수

**인자**
- n: 자연수

**반환값**: 부울
- `True`: n이 순환하는 소수일 때
- `False`: n이 순환하는 소수가 아닐 때

**제한 조건** (아래의 입력은 항상 만족된다. 즉 아래 조건을 어기는 함수 입력값은 신경쓰지 않아도 된다)
- n는 항상 자연수가 전달된다고 가정한다.

**추가 조건**
- 반드시 `prime()`과 `circular()`를 사용할 것

**함수 사용 예시**

```python
print(circular(123))
print(circular(1123))
print(prime(2))
print(prime(3))
print(prime(4))
print(circular_prime(197))
print(circular_prime(13))
print(circular_prime(19))
```

**실행 결과**
```
[123, 231, 312]
[1123, 1231, 2311, 3112]
True
True
False
True
True
False
```
