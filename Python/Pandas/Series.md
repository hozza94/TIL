# Series class

`Series`(시리즈) 클래스는 넘파이에서 제공하는 1차원 배열과 비슷하지만, 각 데이터의 의미를 표시하는 `index`(인덱스)를 붙일 수 있다.

> Series = Value + Index

## series create

``` python
s = pd.Series([10, 20, 30, 40],
             index=['A', 'B', 'C', 'D'])
print(s)
'''
A	10
B	20
C	30
D	40
dtype: int64
'''

s.values # array([10, 20, 30, 40], dtype=int64)
s.index # Index(['A', 'B', 'C', 'D'], dtype='object')
```

## series calculation

```python
s = s / 10
print(s)
'''
A	1.0
B	2.0
C	3.0
D	4.0
dtype: float64
'''
```

## series indexing

```python
s[1], s['B'], s.B # (2.0, 2.0, 2.0)
```

```python
# fancy indexing
s[[0, 3, 1]] # == s[['A', 'D', 'B']]
'''
A    1.0
D    4.0
B    2.0
dtype: float64
'''
```

```python
# slicing
s[1:3]
'''
#B    2.0
#C    3.0
#dtype: float64
'''

s['B':'D']
'''
B    2.0
C    3.0
D    4.0
dtype: float64
'''
```

:red_circle: 문자열로 슬라이싱 하는경우에는 마지막 값까지 포함한다.

```python
# filtering
s[(2.1 < s) & (s < 3.1)]
'''
C    3.0
dtype: float64
'''
```

## indexing calculate

```python
s2 = pd.Series([7, 8, 9, 10],
             index=['A', 'B', 'E', 'F'])

print(s2 - s)
'''
A    6.0
B    6.0
C    NaN
D    NaN
E    NaN
F    NaN
dtype: float64
'''
```

같은 `index`를 가진 값 끼리는 사칙연산이 적용되고, 중복되지 않는 `index`는 `NaN`값으로 표현된다.

## data update, add, delete

```python
# update
s['D'] = 7
print(s)
'''
A    1.0
B    2.0
C    3.0
D    7.0
dtype: float64
'''
```

```python
# add
s['X'] = 5
print(s)
'''
A    1.0
B    2.0
C    3.0
D    7.0
X    5.0
dtype: float64
'''
```

```python
# delete
del s['X']
print(s)
'''
A    1.0
B    2.0
C    3.0
D    7.0
dtype: float64
'''
```