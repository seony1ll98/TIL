# 비시퀀스 데이터 구조

## 딕셔너리

- 딕셔너리 메서드
1. `.get(key[,default])` : 키 연결된 값을 반환하거나 키가 없으면 None 혹은 기본값을 반환

```python
# get
person = {'name': 'Alice', 'age': 25}
print(person.get('name'))
print(person.get('country'))
print(person.get('country','unknown'))
# print(person['country'])  # KeyError: 'country'
```
2. `.keys` : 딕셔너리 키를 모은 객체를 반환
    - 참고) `dict_keys(['name', 'age'])` = 실시간으로 동기화되는 확인 창(view)
```python
# keys
person = {'name': 'Alice', 'age': 25}
print(person.keys())  # dict_keys(['name', 'age'])

person_keys = person.keys()
person['country'] = 'KOREA'
print(person_keys)

for key in person.keys() :
    print(key)
```

3. `.values()` : 딕셔너리 값을 모은 객체를 반환
```python
# values
person = {'name': 'Alice', 'age': 25}
print(person.values())  # dict_values(['Alice', 25])
```

4. `.items()` : 딕셔너리 키/값 쌍을 모은 객체를 반환
```python
# items
person = {'name': 'Alice', 'age': 25}
print(person.items())  # dict_items([('name', 'Alice'), ('age', 25)])
```

5. `.pop(key[,default])` : 키를 제거하고 연결되어 있던 값을 반환(없으면 에러나 default를 반환)
```python
# pop
person = {'name': 'Alice', 'age': 25}
print(person.pop('age'))  # 25
print(person)  # {'name': 'Alice'}
print(person.pop('country', None))  # None
# print(person.pop('country'))  # KeyError: 'country'
```

6. `.clear()` : 딕셔너리의 모든 키/값 쌍을 제거

7. `.setdefault(key[,default])` : 키와 연결된 값을 반환함. 키가 없다면 default와 연결한 키를 딕셔너리에 추가하고 default를 반환
```python
# setdefault
person = {'name': 'Alice', 'age': 25}
print(person.setdefault('country','KOREA'))  # KOREA
print(person)  # {'name': 'Alice', 'age': 25, 'country': 'KOREA'}
```

8. `.update([other])` : other가 제공하는 키/값 쌍으로 딕셔너리를 갱신하고 기존 키는 덮어씀
```python
# update
person = {'name': 'Alice', 'age': 25}
other_person = {'name': 'Jane', 'country': 'KOREA'}

person.update(other_person)
print(person)  # {'name': 'Jane', 'age': 25, 'country': 'KOREA'}

person.update(age=100, address='SEOUL')
print(person) 
# {'name': 'Jane', 'age': 100, 'country': 'KOREA', 'address': 'SEOUL'}
```

## 세트
- 세트(set) : 고유한 항목들의 정렬되지 않은 컬렉션(중복 없음, 순서 없음)

- 세트 메서드
1. `.add(x)` : set에 x를 추가. 이미 x가 있다면 변화 없음
```python
# add
my_set = {'a', 'b', 'c', 1, 2, 3}

my_set.add(4)
print(my_set) # {1, 2, 3, 4, 'b', 'a', 'c'}
my_set.add(4)
print(my_set) # {1, 2, 3, 4, 'b', 'a', 'c'}
```
2. `.update(iterable)` : set에 다른 iterable 요소를 추가
```python
my_set = {'a', 'b', 'c', 1, 2, 3}
my_set.update([1, 4, 5])
print(my_set)  # {'c', 2, 3, 1, 'b', 4, 5, 'a'}
```
3. `.clear()` : set의 모든 항목을 제거

4. `.remove(x)` : set에서 항목 x를 제거. 항목 x가 없을 경우 Keyerror
```python
# remove
my_set = {'a', 'b', 'c', 1, 2, 3}
my_set.remove(2)
print(my_set)
# my_set.remove(10)  # KeyError: 10
```
5. `.pop()` : set에서 임의의(**evenly random이 아니라 arbitrary**) 항목을 제거하고 반환
```python
my_set = {'a', 'b', 'c', 1, 2, 3}
element = my_set.pop()
print(element)
```
6. `.discard(x)` : set에서 항목 x를 제거. `.remove(x)`와 달리 에러 없음
```python
my_set = {'a', 'b', 'c', 1, 2, 3}
my_set.discard(2)
print(my_set)
my_set.discard(10) # 에러 메시지 없음(아무런 출력도 없음)
```
7. 세트의 집합 연산 메서드   
    - 합집합 연산 : `set1.union(set2)` 또는 `set1 | set2` 
    - 교집합 연산 : `set1.intersection(set2)` 또는 `set1 & set2` 
    - 차집합 연산 : `set1.difference(set2)` 또는 `set1 - set2`
    - 포함 관계(포함된다) : `set1.issubset(set2)` 또는 `set1 <= set2`
    - 포함 관계(포함한다) : `set1.issuperset(set2)` 또는 `set1 >= set2`

# 참고

## 해시 테이블
- 해시 테이블은 key-value을 짝지어 저장하는 자료구조이다.

- 해시 테이블의 원리 :
1. 키를 해시 함수를 통해 해시 값으로 변환

2. 변환된 해시 값을 인덱스로 삼아 데이터를 저장하거나 찾음

3. 이로 인해 검색, 삽입 삭제를 매우 빠르게 수행

- 해시(Hash) : 임의의 크기를 가진 데이터를 고정된 크기의 고유한 값으로 변환하는 것   
- 데이터 -> 해시 함수 -> 해시값(고정된 정수) : 버킷 위치로 사용
- 해시 함수의 결과는 실행 때마다 다르다
- **set는 버킷 위치가 요소의 위치를 결정하므로, 순서를 보장하지 않는다!**
---

- `pop` 순서는 버킷 위치에 따라 결정됨. 그런데 자꾸 int형 자료들은 같은 버킷 위치를 가지는 듯하다?
1. 문자열은 해시 계산 시 파이썬의 해시 난수화가 적용되므로, 실행마다 순서가 달라질 수 있음(해시 난수화)   
because 파이썬 프로세스가 새로 시작될 때마다 해시 계산 시 사용하는 난수 seed가 달라짐
2. **같은 정수는 항상 같은 해시 값을 가짐**

---
- 참고) hashable : hash() 함수에 넣어 해시값을 구할 수 있는 객체를 의미   
1. 대부분의 **불변 타입**은 해시 가능하며 항상 같은 해시 값을 유지함   
ex) `int`, `float`, `str`, `tuple`(단, 내부에 불변만 있는 경우)

2. 가변형 객체는 기본적으로 해시 불가능

3. hashable 객체가 필요한 이유 : 해시 테이블 기반 자료구조 사용, 불변성을 통한 일관된 패치값,
안정성과 예측 가능성 유지

## 파이썬 문법 규격

### BNF(Backus-Naur Form)

- BNF : 프로그래밍 언어의 문법을 표현하기 위한 표기법
- EBNF : BNF를 확장한 표기법. 메타 기호를 추가하여 더 간결하고 표현력이 강해진 형태   

    ex) 대표적인 EBNF 메타기호 
    `[]` : 선택적 요소   
    `{}` : 0번 이상 반복   
    `()` : 그룹화   

    ex) EBNF 메타기호 사용 예시   
    `.pop(key[,default])`

