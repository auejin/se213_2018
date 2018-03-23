## 과제 1-1: 윤년 확인

[윤년](https://ko.wikipedia.org/wiki/윤년)을 확인하는 함수 `leap_year(year)`를 작성하시오. 윤년은 아래와 같은 규칙으로 확인할 수 있다.

1. 서력 기원 연수가 4로 나누어떨어지는 해는 윤년으로 한다.(1988년, 1992년, 1996년, 2004년, 2008년, 2012년 …)
1. 이 중에서 100으로 나누어떨어지는 해는 평년으로 한다.(1900년, 2100년, 2200년, 2300년, 2500년 …)
1. 그중에 400으로 나누어떨어지는 해는 윤년으로 둔다.(1600년, 2000년, 2400년 …)

**인자**
- year: 윤년인지 확인하고자 하는 연도. 항상 양의 정수가 입력된다고 가정해도 됨

**반환값**
- True: year가 윤년인 경우
- False: year가 윤년이 아닌 경우

**함수 사용 예시**
```python
print(leap_year(1999))
print(leap_year(2000))
print(leap_year(2001))
print(leap_year(2002))
print(leap_year(2004))
print(leap_year(2100))
```
**실행결과**
```
False
True
False
False
True
False
```

## 과제 1-2: 과제 수행 여부

DGIST 2학년 프밍군은 기분에 따라 과제를 매우 일찍하는 경우와 전날 밤을 새서 하는 경우가 있다고 한다. 프밍군의 룸메 생태군의 세밀한 관찰에 따르면, 프밍군은 의욕상태와 과제 제출 기한이 며칠 남았냐에 따라 다음 행동을 보인다고 한다.

|  의욕  |   3일전 혹은 이전  |    2일전 | 1일전 |
|--------|---------|---------|------|
| 의욕충만 | Working | Working | Done |
| 의욕저하 | Nothing | Nothing | Overnight Working |

프밍군의 기분과 과제제출기한의 남을 날을 입력으로 받아, 프밍군의 과제 수행 상황을 문자열로 반환하는 함수 `status(mood, days)`를 작성하시오.

**인자**
- mood: 의욕충만 여부
  - `True`: 의욕충만
  - `False`: 의욕저하
- days: 과제 제출 남은 일수. 항상 양의 정수라 가정하면 됨.

**반환값**: 위의 표와 같은 상태가, **문자열** 로 반환됨

**함수 사용 예시**
```python
print(status(True, 3))
print(status(True, 1))
print(status(False, 5))
print(status(False, 1))
```

**실행결과**
```
Working
Done
Nothing
Overnight Working
```

## 과제 1-3: 세금과 팁의 계산

DGIST 2학년 빅데이터양은 이번 여름에 FGLP로 미국을 방문하게 된다. 빅데이터양이 미국에서의 생활에 대한 조사를 하다가, 미국의 식당에서는 메뉴에 표시된 음식 가격에 부가가치세가 별도로 붙고, 또 팁을 내야된다는 사실을 알게 됐다.

팁문화에 익숙하지 않기 때문에, 빅데이터양은 세금과 팁을 계산하는 프로그램을 짜기로 했다. 부가가치세, 팁을 계산하는 함수 `vat()`, `tip()`을 만들고 이 함수들을 이용하여, 전체 계산해야 될 가격을 계산하는 함수 `total()`을 만들기로 했다. 자, 빅데이터양과 함께 이 함수들을 구현하세요.

### `vat(price, vat_ratio)`
**인자**
- price: float. 음식가격
- vat_ratio: float. 부가가치세의 %.

**반환값**
- float: 부가가치세의 양
  - 소수점 3째자리에서 반올림해서 소수점 이하 2자리만 남은 수를 반환할 것

### `tip(price, vat_ratio, tip_ratio, after_tax)`
**인자**
- price: float. 음식가격
- vat_ratio: float. 부가가치세의 %
- tip_ratio: float. 팁의 %
- after_tax: bool
  - True: 부가가치세를 포함한 음식가격에 tip_ratio만큼 팁을 계산
  - False: 부가가치세를 포함하지 않은 음식가격에 tip_ratio만큼 팁을 계산

**반환값**
- float: 팁의 양
  - 소수점 3째자리에서 반올림해서 소수점 이하 2자리만 남은 수를 반환할 것

**참고**

미국에서도 팁을 세금 전에 주어야 할까 세금 후에 주어야 할까라는 논쟁이 있다.

### `tip(price, vat_ratio, tip_ratio, after_tax)`
**인자**
- price: float. 음식가격
- vat_ratio: float. 부가가치세의 %
- tip_ratio: float. 팁의 %
- after_tax: bool
  - True: 부가가치세를 포함한 음식가격에 tip_ratio만큼 팁을 계산
  - False: 부가가치세를 포함하지 않은 음식가격에 tip_ratio만큼 팁을 계산

**반환값**
- float: 음식 가격에 부가가치세, 팁을 포함한 전체 계산해야 될 값
  - 소수점 3째자리에서 반올림해서 소수점 이하 2자리만 남은 수를 반환할 것

**주의**
- 반드시 `vat()`과 `tip()` 함수를 이용할 것


**참고**

소수점 이하 반올림을 하기 위해서 파이썬의 내장함수 `round()`를 사용할 것.

[Python official documentation on `round()`](https://docs.python.org/3/library/functions.html#round)

**함수사용예시**
```python
print(vat(20, 6))
print(vat(20, 5))
print(tip(20, 6, 20, False))
print(total(20, 6, 20, False))
print(total(20, 6, 20, True))
```

```
1.2
1.0
4.0
25.2
25.44
```
