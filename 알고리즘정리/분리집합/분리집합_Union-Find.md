# 분리집합 Union-Find


**Union-Find**는 **트리구조**를 활용해 노드를 합치고 부모를 찾아서 이를 통해 서로소 집합을 찾아내는 알고리즘입니다.

**find** 함수를 통해 부모 노드를 찾을 때 까지 재귀를 활용하여 호출합니다.

이때, 재귀적으로 호출 하면 파이썬의 경우 문제가 생기는 경우가 있는데 이에 대한 내용은 하단에 새로운 코드를 추가하겠습니다.

**union** 함수는 두 노드의 부모노드를 찾고 이를 합치는데 이때 노드의 번호에 따라 합칠 수 있습니다.

두 함수를 수행하기 위해선 해당 노드의 **부모노드를 저장하는 리스트**를 가지고 있어야합니다.

아래는 위 함수들과 알고리즘을 구현한 예제 코드입니다.

```python
n, m = map(int, input().split())
parent = [i for i in range(n)]

def find(x):
    if parent[x] != x:
        parent[x] = find(parent[x])
    return parent[x]

def union(x, y):
    if x < y:
        parent[y] = x
    else:
        parent[x] = y

for _ in range(m):
    k, a, b = map(int, sys.stdin.readline().split())
    if k == 0:
        x = find(a)
        y = find(b)
        union(x, y)

    else:
        if find(a) == find(b):
            print('YES')
        else:
            print('NO')

```

아래는 find 함수를 while문을 통해 수정한 코드입니다.

```python
def find(x):
    while x != parent[x]:
        x = parent[x]
    return x

```
