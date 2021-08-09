# List Comprehension

- 리스트 내부에서 for문과 if문을 사용해서 표현하는것.

![img](https://dojang.io/pluginfile.php/13698/mod_page/content/2/022016.png)

![img](https://dojang.io/pluginfile.php/13698/mod_page/content/2/022018.png)

## 연습문제

- 다음 소스 코드를 완성하여 리스트 a에 들어있는 문자열 중에서 길이가 5인 것들만 리스트 형태로 출력되게 만드세요(리스트 표현식 사용).

```python
a = ['alpha', 'bravo', 'charlie', 'delta', 'echo', 'foxtrot', 'golf', 'hotel', 'india']
b = [                           ]
 
print(b)
```

- 출력결과

```python
['alpha', 'bravo', 'delta', 'hotel', 'india']
```

### 정답

```python
[i for i in a if len(i) == 5]
```

### 해설

리스트 a의 각 원소에 대해 길이가 5인지 확인하여 b에 저장하면 된다.

` i for i in a if len(i) == 5 ` 중 먼저 `for i in a` a 에 있는 i를 순서대로 꺼낸 후

`len(i) == 5` 길이가 5인지 판별 한 후 길이가 5인 i에 대해서만 b에 저장한다.



## 심화문제

- 표준 입력으로 정수 두 개가 입력됩니다(첫 번째 입력 값의 범위는 1~20, 두 번째 입력 값의 범위는 10~30이며 첫 번째 입력 값은 두 번째 입력 값보다 항상 작습니다). 첫 번째 정수부터 두 번째 정수까지를 지수로 하는 2의 거듭제곱 리스트를 출력하는 프로그램을 만드세요(input에서 안내 문자열은 출력하지 않아야 합니다). 단, 리스트의 두 번째 요소와 뒤에서 두 번째 요소는 삭제한 뒤 출력하세요. 출력 결과는 리스트 형태라야 합니다.

- 예시

  > 입력 : 1, 10
  >
  > 출력 : [2, 8, 16, 32, 64, 128, 256, 1024]

### 풀이

```python
start, end = map(int, input().split())
answer = [2 ** x for x in range(start, end+1)]

del answer[1] # 두번째 요소 삭제
del answer[-2] # 뒤에서 두번째 요소 삭제

print(answer)
```

### 실행 결과

>입력 : 10 20
>
>출력 : [1024, 4096, 8192, 16384, 32768, 65536, 131072, 262144, 1048576]

### 해설

start, end 변수를 통해 두개의 정수를 입력 받습니다.

리스트 표현식을 활용해 start, end까지 범위의 x 값을 받아와 2의 거듭제곱으로 저장해줍니다.

이후 `del` 을 이용해 특정 위치의 요소를 삭제합니다.

## :bookmark: References

- [파이썬 코딩도장](https://dojang.io/mod/quiz/view.php?id=2288)
