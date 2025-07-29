# 프로그래밍

- **프로그램 : 문제를 해결하기 위한 명령어들의 집합**

- 프로그래밍의 핵심 : 새 연산을 정의하고 조합해 유용한 작업을 수행하는 것(명령어 묶음을 만드는 과정)

- 프로그래밍 언어 : 컴퓨터에게 작업을 지시하고 문제를 해결하는 도구

# Python

## Python 실행

- Python 인터프리터(Interpretor)가 사용자의 명령어를 운영체제가 이해하는 언어로 바꿈   
  - 파이썬 인터프리터 사용 방법 : `python -i`

## 표현식과 값

- 표현식(Expression) : 하나의 '값'으로 평가될 수 있는 모든 코드   
cf. 평가 : 표현식을 계산하여 그 결과인 '값'을 만들어내는 과정

- 값(value) : 표현식이 평가된 결과. 더 이상 계산되거나 평가될 수 없는. 프로그램의 가장 기본적인 데이터 조각

## 변수와 메모리

- 변수 : 값을 나중에 다시 사용하기 위해, 그 값에 붙여주는 고유한 이름(객체를 가리키는 이름)

- 변수 할당 : 표현식이 만들어 낸 값에 이름을 붙이는 과정(연결)

```python
degrees = 36.5 # 값 36.5를 변수 degrees에 할당
```
- 변수명 규칙 :
1. 영문 알파벳, 숫자, 언더스코어(_)로 구성
2. <span style="color:red"> 숫자로 시작할 수 없음 </span>
3. 대소문자를 구분
4. 내부 예약어 사용 불가능

- 메모리 : 컴퓨터가 특정 데이터 값을 정확히 찾아가기 위해 사용하는 기계적인 숫자 주소

- 객체 : 값 + 타입 + 주소 정보를 묶은 것

## 표현식과 문장

- 문장 : 특정 '동작(action)'을 지시하는, 실행 가능한 코드의 최소 단위 (ex. 할당)

# Data types

## Type

- type : 변수나 값이 가질 수 있는 데이터의 종류를 의미 

1. **Numeric Types** :   
    <span style="color:green"> ex) int, double, float, complex </span>
2. **Text Sequence Types** :   
    <span style="color:green"> ex) str </span>   
  * 시퀀스 타입의 특징 : 순서 / 인덱싱/ 슬라이싱/ 길이 / 반복
  * 코드에서 따옴표는 작은따옴표('')로 통일하는 게 좋다. 따옴표 안에 따옴표를 넣고 싶다면 이스케이프 시퀀스(\\) 활용하기
  *  f-string : 문자열 안에 값 삽입하기 // 심화 사용법 익히기(숙제)
  ```python
  # String Interpolation "f-string"
  name = '홍길동'
  age = 25
  greeting = f'안녕하세요, 제 이름은 {name}이고 나이는 {age}살입니다.'
  # 안녕하세요, 제 이름은 홍길동이고 나이는 25살입니다.
  print(greeting)
  ```

  *  python은 음수 인덱스도 지원한다
  *  슬라이싱 사용법
  ```python
  my_sequence[start : stop : step]
  # start : 포함 / stop : 포함 안됨 / step :  건너뛰는 크기
  ```

  * 문자열은 불변성을 가진다
   ```python
   my_str = 'Hello'
   my_str[1] = 'a'

   # TypeError: 'str' object does not support item assignment

   # 그렇다면 문자열을 바꾸는 방법은?
   # 기존 문자열의 일부와 새로운 값을 조합하여 새로운 문자열을 만들어야 함

   new_str = my_str[0] + 'a' + my_str[2:]
   print(new_str)
   ```

 3. **Sequence Types**   
    <span style="color:green"> ex) list, tuple, range </span>
 4. **Non-sequence Types**  
    <span style="color:green"> ex) set, dict </span>
 5. **기타**   
    <span style="color:green"> ex) Boolean, None, Functions </span>


### 참고
* 정수형의 진법 표현
1. 2진법 : `0b`
2. 8진법 : `0o`
3. 16진법 : `0x`

* 실수의 함정, 부동소수점 오차
  ```python
  # 부동소수점 에러
  result = 0.1 + 0.2
  print(result == 0.3)  # False
  print(result)  # 0.30000000000000004


  # 해결 전
  a = 3.2 - 3.1
  b = 1.2 - 1.1

  print(a)  # 0.10000000000000009
  print(b)  # 0.09999999999999987
  print(a == b)  # False

  # 해결 후
  from decimal import Decimal

  a = Decimal('3.2') - Decimal('3.1')
  b = Decimal('1.2') - Decimal('1.1')

  print(a)  # 0.1
  print(b)  # 0.1
  print(a == b)  # True
  ```

* Style Guide : PEP 8(파이썬 코드의 공식 스타일 가이드)   
  ![alt text](image-8.png)

* 주석 :   
  ctrl + /


  ### 헷갈리는 예제
- 재할당 점검
```python
# x의 값은?
number = 10
x = 2 * number
print(x) # x = 20

number = 5
print(x) # x = ?
```
답은 20. x는 재할당된 number의 영향을 받지 않는다!

- 연산자 우선순위 점검
```python
# 결과는?
-2 ** 4
```
답은 -16. -보다 거듭제곱 **이 우선순위가 더 높기 때문!

- 슬라이싱 점검
```python
my_str = "hello"
my_str[::-1] # 결과는?
```
답은 "olleh". 이 표현은 유용하니 암기해 두자