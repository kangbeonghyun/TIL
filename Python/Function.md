# Python

## function(def)

* 입력값이 몇 개가 될지 모를 때

```python
def sum_many(*args):
  sum=0
  for i in args:
    sum+=sum+i
```

위와 같이 입력변수 명 앞에 *를 붙이면 입력값들을 전부 모아서 튜플로 만듬.

* 함수의 리턴은 한개이다 단,

```python
def sum_and_mul(a,b):
  return a+b,a*b
```

이러한 경우 가능하다, 하나의 튜플 값인 (a+b,a*b)로 반환하기 때문.

함수를 받는 부분에서 result1,result2=sum_and_mul(3,7)과 같이 사용해서 분리 할 수 있다.

* 초기값은 미리 설정 할 수 있으나 항상 뒤쪽에 위치 시키자

```pyhon
def func1(name,man=True,old):
 ###error
def func2(name,old,man=True):
 ###right!
 
```

