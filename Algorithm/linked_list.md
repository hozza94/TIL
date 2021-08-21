# Linked List

- 떨어진 곳에 위치한 데이터를 화살표로 연결한 것
- 노드 구조
  - 데이터 + 링크 로 구성
  - `head` -> `list` -> `Null(tail)`
- 선형리스트와 달리 데이터를 삭제하고 삽입할때 유동적이다.



## Implement

- `head` : linked_list 시작점
- `current` : node를 순회할때 현재 지점
- `pre` : `current`의 이전 지점

### Create

```python
# data save, link the other node
class Node():
    def __init__(self):
        self.data = None
        self.link = None
        
node = Node() # or head
```



### Insert

```python
# find_data == index
# inserted before find_data
def insertNode(find_data, insert_data):
    global head, current, pre
    
    # case 1. 맨 처음에 삽입되는 경우
    if head.data == find_data: 
        node = Node()
        node.data = insert_data
        node.link = head
        head = node
        memory.append(node)
        return

    # case 2. 중간에 삽입되는 경우
    current = head
    while (current.link != None):
        pre = current
        current = current.link
        if current.data == find_data:
            node = Node()
            node.data = insert_data
            node.link = current
            pre.link = node
            memory.append(node)
            return

    # case 3. 맨 마지막에 삽입되는 경우
    node = Node()
    node.data = insert_data
    current.link = node
    memory.append(node)
    return
```



### Delete

```python
# delete target data
def deleteNode(delete_data):
    global head, current, pre

    # case 1. 맨 처음 데이터가 삭제되는 경우
    if head.data == delete_data:
        current = head
        head = head.link
        del(current)
        return

    # case 2. case 1을 제외한 모든 경우
    current = head
    while current.link != None:
        pre = current
        current = current.link
        if current.data == delete_data:
            pre.link = current.link
            del(current)
```



### Print

```python
def printNode(start):
    current = start
    print(current.data, end=' ')
    while (current.link != None):
        current = current.link
        print(current.data, end=' ')
    print()
```

