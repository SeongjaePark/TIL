# 2. 트리

[코드잇 자료구조 코스 ](https://www.codeit.kr/courses/data-structures)

<details>
  <summary>1) 트리란?</summary>
  <details>
    <summary>계층적 관계 & 트리란? & 트리 용어 & 트리의 활용</summary>

# 계층적 관계

## 트리

- 데이터의 상-하 관계(계층적 관계)를 저장하는 자료 구조

계층적 관계의 예시: 회사의 직급, 컴퓨터 폴더 구조, 클래스 상속 관계

## 계층적 데이터 저장

배열, 링크드 리스트 → 선형적 자료 구조

해시 테이블 → 데이터 관계 저장 X

따라서 위의 자료 구조들은 계층적 관계를 나타내기에는 적합하지 않음

# 트리란?

링크드 리스트가 노드들 간의 앞뒤 관계를 포함하고 있듯이,

트리는 노드들 간의 계층적 관계(상하 관계)를 포함하고 있다.

이때, 이 관계를 부모-자식 관계라고 한다.

여러 노드들이 부모-자식 관계를 통해서 연결되어 있고, 이 관계가 뻗어나가는 모양이 나무와 같다고 하여 트리라는 이름을 갖게 되었다.

트리에서 가장 상위에 있는 노드, 즉 트리의 시작점이 되는 노드를 나무의 뿌리와 같다 하여, 루트 노드 (root node)라 부른다.

# 트리 용어

- root 노드 (뿌리 노드): 트리의 시작 노드, 뿌리가 되는 노드를 말함. 보통 트리를 표현할 때 가장 위에 root 노드를 놓는 방식으로 나타냄
- 부모 노드: 특정 노드의 직속 상위 노드.
- 자식 노드: 특정 노드의 직속 하위 노드. 부모 노드와 반대되는 개념.
- 형제 노드: 같은 부모를 갖는 노드
- leaf 노드 (잎/말단 노드): 자식 노드를 갖고 있지 않은, 가장 말단에 있는 노드임. 트리의 끝에 있다고 해서 root(뿌리) 노드와 반대되는 표현으로 leaf(잎) 노드라고 부름.
- 깊이: 특정 노드가 root 노드에서 떨어져 있는 거리. 깊이는 해당 노드로 가기 위해서 root 노드에서 몇 번 아래로 내려와야 하는지를 나타냄.
- 레벨: 깊이 +1. 깊이랑 거의 같은 개념. 그냥 깊이에 1을 더한 값. 레벨 1에 있는 노드들, 레벨 2에 있는 노드들, 이런 식으로 특정 깊이인 노드들을 묶어서 표현할 때 사용하는 용어
- 높이: 트리에서 가장 깊이 있는 노드의 깊이.
- 부분 트리 (sub-tree): 현재 트리의 일부분을 이루고 있는 더 작은 트리를 말함. 오른쪽 부분 트리, 왼쪽 부분 트리 등. 전체 트리를 좀 더 작은 단위로 쪼개보면 더 작은 부분 트리들을 발견할 수 있음. 특정 노드를 root 노드라고 생각하고 바라보면 여러 가지 부분 트리들을 발견할 수 있음.

# 트리의 활용

## 트리의 장점

- 계층적 관계가 있는 데이터를 컴퓨터에서 사용!
- 컴퓨터 과학의 다양한 문제 기발하게 해결! (정렬, 압축)
- 흔히 사용하는 여러 추상 자료형 구현! (딕셔너리, 세트, 우선순위 큐)
  </details>
  <details>
    <summary>이진 트리 & 이진 트리 구현</summary>

# 이진 트리

## 이진 트리란?

각 노드가 최대 2개의 자식 노드를 가질 수 있는 트리

- 왼쪽 자식, 오른쪽 자식

# 이진 트리 구현

## 만들려는 이진 트리

<img src="img/binaryTree.png" width=400>

## 파이썬 코드

```python
class Node:
  """이진 트리 노드 클래스"""

  def __init__(self, data):
    """데이터와 두 자식 노드에 대한 레퍼런스를 갖는다"""
    self.data = data
    self.left_child = None
    self.right_child = None

"""노드 인스턴스 생성"""
root_node = Node(2)
node_B = Node(3)
node_C = Node(5)
node_D = Node(7)
node_E = Node(11)

"""B와 C를 root 노드의 자식으로 지정"""
root_node.left_child = node_B
root_node.right_child = node_C

"""D와 E를 B의 자식으로 지정"""
node_B.left_child = node_D
node_B.right_child = node_E

# root 노드에서 왼쪽 자식 노드 받아오기
test_node_1 = root_node.left_child
print(test_node_1.data) # 3

# 노드 B의 오른쪽 자식 노드 받아오기
test_node_2 = test_node_1.right_child
print(test_node_2.data) # 11
```

  </details>
  <details>
    <summary>이진 트리 종류 & 완전 이진 트리 배열로 구현하기</summary>

# 이진 트리 종류

## 정 이진 트리 (Full Binary Tree)

모든 노드가 2개 또는 0개의 자식을 가지는 이진 트리

## 완전 이진 트리 (Complete Binary Tree)

마지막 레벨 직전의 레벨 까지는 모든 노드들이 다 채워진 트리

마지막 레벨에서는 노드들이 다 채워질 필요는 없더라도, 왼쪽부터 오른쪽 방향으로는 노드들이 다 채워져야 함

<img src="img/completeBinaryTree.png" width=800>

### 완전 이진 트리의 중요한 성질

완전 이진 트리 안에 저장된 노드: n개

완전 이진 트리의 높이는 항상 *lg(n)*에 비례한다.

완전 이진 트리는 마지막 레벨 직전 레벨까지는 모두 노드로 가득 채워져 있음.

레벨1에 1개, 레벨2에 2개, 레벨3에 4개, 레벨4에 8개. 이런 식으로 레벨이 하나씩 증가할 때마다 이전 레벨에 있는 노드 개수의 2배를 더 담을 수 있음

이진 트리의 높이를 _h_, 그 노드 수를 *n*이라고 할 때,

2^(h) ≤ n ≤ 2^(h+1) - 1 , 2^(h) ≤ n < 2^(h+1) 이고, 각 항에 *lg*를 씌우면

_h_ ≤ _lg(n)_ < _h_+1 이 됨

이걸 보면 완전 이진 트리의 높이는 노드 수에 *lg*를 취한 값보다 작은 정수 중에서 최대의 정수임을 알 수 있다.

즉, 노드 수가 n개인 완전 이진 트리의 **높이**는 **h ≤ lg(n)**를 **만족하는 정수 중 **최대의 정수\*\*임

따라서, 완전 이진 트리의 높이 h는 노드 수인 n에 lg를 취한 값인 lg(n)에 비례해서 증가한다는 것을 알 수 있음. 그럼 언제 확실히 높이가 하나 더 증가할까? 그건 바로 노드 수가 현재보다 최소 2배 이상이 되었을 때이다.

h ≤ lg(n) 인 상황에서 n이 2n이 되면, lg(2n) = lg(n) + 1이고,

h+1 ≤ lg(n) +1을 만족하므로, 최소한 현재 노드 수보다 노드 수가 2배 이상이 되었을 때 확실히 높이도 하나 더 올라간다는 것을 알 수 있다.

정리하자면, 완전 이진 트리의 높이는 결국 O(lg(n))이라고 할 수 있음

## 포화 이진 트리 (Perfect Binary Tree)

포화 이진 트리는 모든 레벨이 빠짐없이 다 노드로 채워져 있는 이진 트리임

포화 이진 트리는 기본적으로 정 이진 트리와 완전 이진 트리의 특성을 모두 갖는다.

높이가 0이면 노드 수가 1개, 높이가 1이면 노드 수가 (1+2)개, 높이가 2면 (1+2+4)개, 높이가 3이면 (1+2+4+8)개 이런 식으로 그 높이에 따라 노드의 수가 고정된다.

트리의 높이는 h, 노드 수를 n이라 하면, **n = 2^(h+1) - 1**

식의 양쪽에 1을 더해주면 결국 **n+1 = 2^(h+1)** 와 같은 공식이 성립함

포화 이진 트리는 그 높이나 노드 수, 둘 중에서 하나만 알아도 나머지 하나의 값을 바로 구할 수 있음

# 완전 이진 트리 배열로 구현하기

## 완전 이진 트리 배열 (파이썬 리스트)에 저장하기

트리를 파이썬의 리스트로 구현하는 방법은 모든 이진 트리에 쓸 수 있는 방법은 아니고, 완전 이진 트리인 경우에만 쓸 수 있는 방법이다

<img src="img/completeBinaryTree2.png" width=800>

이 완전 이진 트리는 아래처럼 리스트에 저장할 수 있다.

```python
complete_binary_tree = [None, 1, 5, 12, 11, 9, 10, 14, 2, 10]
```

위 그림에서 빨간색 작은 숫자는 각 노드의 리스트 내에서의 인덱스를 나타냄. 그러니까 리스트에서 5번째 노드는 노드 9임

## 자식 노드를 찾는 방법

이진 트리에서 각 노드는 기본적으로 자식 노드들을 가리키는 레퍼런스를 가져야 함. 그래야 부모 노드가 자식 노드에 접근할 수 있으니까.

그렇다면 리스트에 노드들이 저장된 경우에는 부모 노드가 자식 노드에 어떻게 접근할 수 있을까?

<img src="img/completeBinaryTree2.png" width=800>

지금 2번째 노드(노드 5)의 왼쪽 자식 노드를 찾고 싶다고 하자.

그럼 먼저 노드의 인덱스 2에 2를 곱한다. 4다. 그 다음 리스트의 4번째 인덱스에 있는 노드를 찾으면 된다. 노드 11이 있다. 제대로 찾았다.

이번에는 3번째 노드(노드 12)의 오른쪽 자식 노드를 찾아보자.

이번에도 노드의 인덱스 3에 2를 곱한다. 그리고 1을 더해주는데, 그럼 7이다. 이번에는 리스트의 7번째 인덱스를 보면 노드 14가 있다. 맞게 찾았다.

왼쪽 자식 인덱스 = 자신의 인덱스 \* 2

오른쪽 자식 인덱스 = (자신의 인덱스 \* 2) + 1

## 부모 노드를 찾는 방법

부모의 노드를 찾을 때에는, 자신의 인덱스를 2로 나눈 것에서 정수만 취하면 된다.

## 정리

완전 이진 트리는 그 특수한 2가지 성질

- 마지막 레벨 직전의 레벨까지는 노드들로 가득 차 있음
- 마지막 레벨은 왼쪽에서 오른쪽 방향으로 노드들로 가득 차 있어야 함

때문에 이렇게 각 노드를 리스트에 저장한 후에도 부모 노드와 자식 노드를 손쉽게 찾을 수 있다.

## 파이썬 구현

```python
def get_parent_index(complete_binary_tree, index):
    """배열로 구현한 완전 이진 트리에서 index번째 노드의 부모 노드의 인덱스를 리턴하는 함수"""
    parent = index // 2
    if parent != 0:
        return parent
    # root 노드만 부모 노드가 없는데, 이 경우 parent_index가 0. None을 리턴
    else:
        return None

def get_left_child_index(complete_binary_tree, index):
    """배열로 구현한 완전 이진 트리에서 index번째 노드의 왼쪽 자식 노드의 인덱스를 리턴하는 함수"""
    left_child = index * 2
    # 자식 노드가 없으면 - None을 포함한 배열의 길이가 계산된 인덱스+1 보다 작음
    if len(complete_binary_tree) < left_child + 1:
        return None
    else:
        return left_child


def get_right_child_index(complete_binary_tree, index):
    """배열로 구현한 완전 이진 트리에서 index번째 노드의 오른쪽 자식 노드의 인덱스를 리턴하는 함수"""
    right_child = index * 2 + 1
    # 자식 노드가 없으면 - None을 포함한 배열의 길이가 계산된 인덱스+1 보다 작음
    if len(complete_binary_tree) < right_child + 1:
        return None
    else:
        return right_child

# 실행 코드
root_node_index = 1 # root 노드

tree = [None, 1, 5, 12, 11, 9, 10, 14, 2, 10]  # 과제 이미지에 있는 완전 이진 트리

# root 노드의 왼쪽과 오른쪽 자식 노드의 인덱스를 받아온다
left_child_index = get_left_child_index(tree, root_node_index)
right_child_index = get_right_child_index(tree,root_node_index)

print(tree[left_child_index]) # 5
print(tree[right_child_index]) # 12

# 9번째 노드의 부모 노드의 인덱스를 받아온다
parent_index = get_parent_index(tree, 9)

print(tree[parent_index]) # 11

# 부모나 자식 노드들이 없는 경우들
parent_index = get_parent_index(tree, 1)  # root 노드의 부모 노드의 인덱스를 받아온다
print(parent_index) # None

left_child_index = get_left_child_index(tree, 6)  # 6번째 노드의 왼쪽 자식 노드의 인덱스를 받아온다
print(left_child_index) # None

right_child_index = get_right_child_index(tree, 8)  # 8번째 노드의 오른쪽 자식 노드의 인덱스를 받아온다
print(right_child_index) # None
```

  </details>
  <details>
    <summary>트리 순회</summary>

# 트리 순회

## 순회

- 자료 구조에 저장된 모든 데이터를 도는 것

## 재귀 함수

선형적 자료 구조를 순회할 때는 보통 반복분을 사용했는데,

트리 순회에는 재귀 함수 사용!

순회 말고도, 트리에서는 재귀 함수를 많이 사용

## 순회 기본 동작들

- 재귀적으로 왼쪽 부분 트리 순회
- 재귀적으로 오른쪽 부분 트리 순회
- 현재 노드 데이터 출력

# 트리 순회: pre-order

## pre-order 순회

부분 트리 순회 "전"에 현재 노드 출력

1. 현재 노드 데이터를 출력한다
2. 재귀적으로 왼쪽 부분 트리 순회
3. 재귀적으로 오른쪽 부분 트리 순회

# 트리 순회: post-order

## post-order 순회

부분 트리 순회 "후"에 현재 노드 출력

1. 재귀적으로 왼쪽 부분 트리 순회
2. 재귀적으로 오른쪽 부분 트리 순회
3. 현재 노드 데이터를 출력한다.

# 트리 순회: in-order

## in-order 순회

부분 트리 순회 "사이"에 현재 노드 출력

1. 재귀적으로 왼쪽 부분 트리 순회
2. 현재 노드 데이터를 출력한다.
3. 재귀적으로 오른쪽 부분 트리 순회

## 순회

트리를 순회하면 노드들 사이에 **선형적 순서**를 만들 수 있다!

# in-order 순회 구현

## 순회할 트리

<img src="img/inOrder.png" width=800>

## 파이썬 코드

```python
class Node:
    """이진 트리 노드를 나타내는 클래스"""

    def __init__(self, data):
        """이진 트리 노드는 데이터와 두 자식 노드에 대한 레퍼런스를 갖는다"""
        self.data = data
        self.left_child = None
        self.right_child = None

def traverse_inorder(node):
    """in-order 순회 함수"""

    if node.left_child is not None:
        traverse_inorder(node.left_child)

    print(node.data)

    if node.right_child is not None:
        traverse_inorder(node.right_child)


# 여러 노드 인스턴스 생성
node_A = Node("A")
node_B = Node("B")
node_C = Node("C")
node_D = Node("D")
node_E = Node("E")
node_F = Node("F")
node_G = Node("G")
node_H = Node("H")
node_I = Node("I")

# 생성한 노드 인스턴스들 연결
node_F.left_child = node_B
node_F.right_child = node_G

node_B.left_child = node_A
node_B.right_child = node_D

node_D.left_child = node_C
node_D.right_child = node_E

node_G.right_child = node_I

node_I.left_child = node_H

# 노드 F를 root 노드로 만든다
root_node = node_F

# 만들어 놓은 트리를 in-order로 순회한다
traverse_inorder(root_node)
# A
# B
# C
# D
# E
# F
# G
# H
# I
```

  </details>
</details>

<details>
  <summary>2) 힙</summary>
  <details>
    <summary>힙이란?</summary>

# 힙이란?

## 힙의 두 가지 속성

힙은 2가지 속성을 가진 트리임

- 형태 속성: 완전 이진 트리다 ( 높이 = O(lg(n)) )
- 힙 속성: 모든 노드의 데이터는 자식 노드들의 데이터보다 크거나 같다.

## 힙의 두 가지 활용

- 정렬 문제 해결
- 우선순위 큐 구현
  </details>
  <details>
    <summary>정렬 문제</summary>

# 정렬 문제

## 정렬

여러 개의 데이터 요소를 특정 순서로 배치하는 것

정렬 알고리즘: 데이터를 재배치하는 구체적인 방법

- 삽입 정렬, 합병 정렬, 선택 정렬, 힙 정렬

# 배열로 구현한 힙

## 힙 구현하기

- 힙도 완전 이진 트리이므로 동적 배열로 구현! (파이썬 리스트)

# 힙 만들기 1

## heapify

**heapify**: 힙 속성을 지키지 않는 노드가 있을 때마다, 그 노드가 맞는 위치를 찾을 때까지 재배치하는 알고리즘

부모 노드와 자식 노드들의 데이터의 크기를 비교하여, 부모 노드보다 자식 노드가 크면 두 노드의 위치를 바꿔준다.

### 시간 복잡도

모든 노드의 개수: n

최악의 경우: 루트 노드가 리프 노드까지 내려가는 경우

- 총 트리의 높이만큼 데이터를 비교하고 재배치 함

heapify 시간 복잡도: **O(lg(n))**

## 내가 짠 heapify 코드

```python
def swap(tree, index_1, index_2):
    """완전 이진 트리의 노드 index_1과 노드 index_2의 위치를 바꿔준다"""
    temp = tree[index_1]
    tree[index_1] = tree[index_2]
    tree[index_2] = temp

def heapify(tree, index, tree_size):
    """heapify 함수"""

    # 왼쪽 자식 노드의 인덱스와 오른쪽 자식 노드의 인덱스를 계산
    left_child_index = 2 * index
    right_child_index = 2 * index + 1

		parent_data = tree[index]

    # 자식 노드가 없을 때 종료
    if tree_size < left_child_index + 1:
        return
    # 왼쪽 자식 노드만 있을 때
    elif tree_size < right_child_index + 1:
        left_child_data = tree[left_child_index]
        most = max(parent_data, left_child_data)
        # 부모 노드의 데이터가 가장 클 떄
        if parent_data == most:
            return
        # 왼쪽 자식 노드의 데이터가 가장 클 떄
        else:
            swap(tree, index, left_child_index)
            heapify(tree, left_child_index, tree_size)
        return

    # 모든 자식 노드가 있을 때
    left_child_data = tree[left_child_index]
    right_child_data = tree[right_child_index]

    most = max(parent_data, left_child_data, right_child_data)

    # 부모 노드의 데이터가 가장 클 떄
    if parent_data == most:
        return
    # 왼쪽 자식 노드의 데이터가 가장 클 떄
    elif left_child_data == most:
        swap(tree, index, left_child_index)
        heapify(tree, left_child_index, tree_size)
    # 오른쪽 자식 노드의 데이터가 가장 클 떄
    else:
        swap(tree, index, right_child_index)
        heapify(tree, right_child_index, tree_size)



# 실행 코드
tree = [None, 15, 5, 12, 14, 9, 10, 6, 2, 11, 1]  # heapify하려고 하는 완전 이진 트리
heapify(tree, 2, len(tree))  # 노드 2에 heapify 호출
print(tree)
```

## 코드잇 해답: 더 나은 heapify 코드

```python
def swap(tree, index_1, index_2):
    """완전 이진 트리의 노드 index_1과 노드 index_2의 위치를 바꿔준다"""
    temp = tree[index_1]
    tree[index_1] = tree[index_2]
    tree[index_2] = temp

def heapify(tree, index, tree_size):
    """heapify 함수"""

    # 왼쪽 자식 노드의 인덱스와 오른쪽 자식 노드의 인덱스를 계산
    left_child_index = 2 * index
    right_child_index = 2 * index + 1

    largest = index # 일단 부모 노드의 값이 가장 크다고 설정

    # 왼쪽 자식 노드의 값과 비교
    #(동시에 인덱스의 유효 범위 확인을 통해서 자식 노드가 있는지도 확인)
    if 0 < left_child_index < tree_size and tree[largest] < tree[left_child_index]:
        largest = left_child_index

    # 오른쪽 자식 노드의 값과 비교
    if 0 < right_child_index < tree_size and tree[largest] < tree[right_child_index]:
        largest = right_child_index

    if largest != index: # 부모 노드의 값이 자식 노드의 값보다 작으면
        swap(tree, index, largest) # 부모 노드와 최댓값을 가진 자식 노드의 위치를 바꿔준다
	      # 자리가 바뀌어 자식 노드가 된 기존의 부모 노드를 대상으로 또 heapify 함수를 호출한다
				heapify(tree, largest, tree_size)


# 실행 코드
tree = [None, 15, 5, 12, 14, 9, 10, 6, 2, 11, 1]  # heapify하려고 하는 완전 이진 트리
heapify(tree, 2, len(tree))  # 노드 2에 heapify 호출
print(tree)
```

# 힙 만들기 2

## heapify

파라미터로 넘기는 노드가 힙에서 위치를 찾아간다.

파이썬 리스트로 구현한 완전 이진 트리에서, 마지막 인덱스부터 차례로 hipify를 호출해 추면 힙으로 만들 수 있음

- 이미 자식 노드들에 heapify 함수가 호출된 이후에는 부모 노드를 뿌리로 하고 있는 부분들은 모두 힙 속성을 지키고 있는 것으로 가정할 수 있기 때문

## 시간 복잡도

heapify: O(lg(n))

이 heapify를 맨 뒤 노드부터 모든 노드에 호출해야 하기 때문에

시간복잡도는 **O(nlg(n))** 이다!

  </details>
  <details>
  <summary>힙 정렬</summary>

# 힙 정렬

## 힙 정렬

힙을 이용한 정렬 알고리즘!

1. 힙을 만든다
2. root와 마지막 노드를 바꿔준다
3. (바꾼 노드는 없는 노드 취급한다)
4. 새로운 노드가 힙 속성을 지킬 수 있게 heapify 호출

모든 인덱스를 돌 때까지 2~4 반복

### 만약 내림 차순으로 정렬하고 싶으면?

힙 속성을 반대로 (부모 노드의 데이터가 자식 노드의 데이터보다 작아야 한다) 바꾸고, 똑같은 알고리즘을 적용하면 된다.

# 힙 정렬 구현하기

## 순서

1. 먼저 리스트를 힙으로 만든다
2. root 노드와 마지막 노드의 위치를 바꾼다. 마지막 위치로 간 기존의 root 노드는 이제 힙에서 없다고 가정한다.
3. 새로운 root 노드가 힙 속성을 지킬 수 있게 heapify 한다.
4. 힙에 남아있는 노드가 없도록 단계 2~3을 반복한다.

## 내가 짠 코드

```python
def swap(tree, index_1, index_2):
    """완전 이진 트리의 노드 index_1과 노드 index_2의 위치를 바꿔준다"""
    temp = tree[index_1]
    tree[index_1] = tree[index_2]
    tree[index_2] = temp

def heapify(tree, index, tree_size):
    """heapify 함수"""

    # 왼쪽 자식 노드의 인덱스와 오른쪽 자식 노드의 인덱스를 계산
    left_child_index = 2 * index
    right_child_index = 2 * index + 1

    largest = index  # 일단 부모 노드의 값이 가장 크다고 설정

    # 왼쪽 자식 노드의 값과 비교
    if 0 < left_child_index < tree_size and tree[largest] < tree[left_child_index]:
        largest = left_child_index

    # 오른쪽 자식 노드의 값과 비교
    if 0 < right_child_index < tree_size and tree[largest] < tree[right_child_index]:
        largest = right_child_index

    if largest != index: # 부모 노드의 값이 자식 노드의 값보다 작으면
        swap(tree, index, largest)  # 부모 노드와 최댓값을 가진 자식 노드의 위치를 바꿔준다
        heapify(tree, largest, tree_size)  # 자리가 바뀌어 자식 노드가 된 기존의 부모 노드를대상으로 또 heapify 함수를 호출한다

def heapsort(tree):
    """힙 정렬 함수"""
    tree_size = len(tree)

    # 1. 리스트를 힙으로 만든다
    # 마지막 노드부터  root 노드까지 반복
    for i in range(len(tree) - 1, 0, -1):
        # heapify 호출
        heapify(tree, i, tree_size)

    root_index = 1

    # 마지막 노드부터 root 노드까지 반복
    for i in range(len(tree) - 1, 0, -1):
        # 2-1. root 노드와 마지막 노드의 위치를 바꾼다.
        temp = tree[root_index]
        tree[root_index] = tree[i]
        tree[i] = temp

        # 2-2 마지막 위치로 간 기존의 root 노드는 이제 힙에서 없다고 가정한다.
        sub_tree = tree[:i]


        # 3. 새로운 root 노드가 힙 속성을 지킬 수 있게 heapify 한다.
        heapify(sub_tree, root_index, len(sub_tree))


        # 4. 기존의 tree에 반영
        tree[:i] = sub_tree[:]

# 실행 코드
data_to_sort = [None, 6, 1, 4, 7, 10, 3, 8, 5, 1, 5, 7, 4, 2, 1]
heapsort(data_to_sort)
print(data_to_sort)
```

## 코드잇 해답: 더 나은 코드

```python
def swap(tree, index_1, index_2):
    """완전 이진 트리의 노드 index_1과 노드 index_2의 위치를 바꿔준다"""
    temp = tree[index_1]
    tree[index_1] = tree[index_2]
    tree[index_2] = temp

def heapify(tree, index, tree_size):
    """heapify 함수"""

    # 왼쪽 자식 노드의 인덱스와 오른쪽 자식 노드의 인덱스를 계산
    left_child_index = 2 * index
    right_child_index = 2 * index + 1

    largest = index  # 일단 부모 노드의 값이 가장 크다고 설정

    # 왼쪽 자식 노드의 값과 비교
    if 0 < left_child_index < tree_size and tree[largest] < tree[left_child_index]:
        largest = left_child_index

    # 오른쪽 자식 노드의 값과 비교
    if 0 < right_child_index < tree_size and tree[largest] < tree[right_child_index]:
        largest = right_child_index

    if largest != index: # 부모 노드의 값이 자식 노드의 값보다 작으면
        swap(tree, index, largest)  # 부모 노드와 최댓값을 가진 자식 노드의 위치를 바꿔준다
        heapify(tree, largest, tree_size)  # 자리가 바뀌어 자식 노드가 된 기존의 부모 노드를대상으로 또 heapify 함수를 호출한다

def heapsort(tree):
    """힙 정렬 함수"""
    tree_size = len(tree)

    # 마지막 인덱스부터 처음 인덱스까지 heapify를 호출한다
    for index in range(tree_size - 1, 0, -1):
        heapify(tree, index, tree_size)

    # 마지막 인덱스부터 처음 인덱스까지
    for i in range(tree_size - 1, 0, -1):
        swap(tree, 1, i) # root 노드와 마지막 인덱스를 바꿔준 후
        heapify(tree, 1, i) # root 노드에 heapify를 호출한다

# 실행 코드
data_to_sort = [None, 6, 1, 4, 7, 10, 3, 8, 5, 1, 5, 7, 4, 2, 1]
heapsort(data_to_sort)
print(data_to_sort)
```

# 힙 정렬 시간 복잡도 & 평가

## 힙 정렬 시간 복잡도

모든 노드의 수 = n

### 힙 정렬의 각 단계

1. 먼저 리스트를 힙으로 만든다.
2. root 노드와 마지막 노드의 위치를 바꾼다. 마지막 위치로 간 기존의 root 노드는 이제 힙에서 없다고 가정한다.
3. 새로운 root 노드가 힙 속성을 지킬 수 있게 heapify 한다.
4. 힙에 남아있는 노드가 없도록 단계 2 ~ 3을 반복한다.

1번째 단계인 리스트를 힙으로 만드는 데 걸리는 시간은 O(nlg(n))이다.

2번째 단계는 그냥 두 노드의 위치를 바꿔 주는 작업이기 때문에 노드의 개수 n과는 상관없이 항상 O(1)이다.

3번째 단계는 새로운 root 노드에 heapify 하는 것이다. 이때의 시간 복잡도는 O(lg(n)). 그럼 2번째 단계와 3번째 단계를 합치면 O(lg(n) + 1), 즉, O(lg(n))이다.

4번째 단계는 2~3 단계를, 힙에 남아있는 노드가 없을 때까지 반복한다. 힙에는 총 n개의 노드가 있으므로 2, 3, 4단계의 시간 복잡도를 종합하면 O(nlg(n)) 이라고 할 수 있다.

### 정리

- 힙을 만드는 데 O(nlg(n))
- 만든 힙에서 매번 root 노드를 뽑고 남은 것들을 다시 힙을 만들어주는 작업을 반복하는 데 O(nlg(n))이 걸린다.

그럼 힙 정렬의 총 시간 복잡도는 O(nlg(n) + nlg(n))으로 O(2nlg(n))이고,

시간 복잡도에서 상수는 무시되니까 결국 O(nlg(n))이라고 할 수 있다.

힙 정렬은 **O(nlg(n))**의 시간 본잡도를 가지는 정렬 알고리즘이다.

## 다른 정렬 알고리즘들과의 비교

- 선택 정렬: O(n^(2))
- 삽입 정렬: O(n^(2))
- 합병 정렬: O(nlg(n))
- 퀵 정렬: 평균 O(nlg(n)), 최악 O(n^(2))
- 힙 정렬: O(nlg(n))

힙 정렬은 선택 정렬과 삽입 정렬보다는 좋고, 합병 정렬과 퀵 정렬과는 비슷한 성능을 내는 정렬 방법이라는 것을 알 수 있다.

  </details>
  <details>
    <summary>우선순위 큐</summary>

# 우선순위 큐

## 우선순위 큐란?

우선순위 큐는 추상 자료형 중 하나다.

- 데이터를 저장할 수 있다.
- 저장한 데이터가 우선순위 순서대로 나온다.

## 우선순위 큐와 힙의 관계

- 힙을 사용하면 우선순위 큐를 효율적으로 구현할 수 있다.

# 힙에 데이터 삽입하기

## 힙 속성을 유지하면서 힙에 데이터 삽입하는 법

1. 힙의 마지막 인덱스에 데이터를 삽입한다
2. 삽입한 데이터와 부모 노드의 데이터를 비교한다
3. 부모 노드의 데이터가 더 작으면 둘의 위치를 바꿔준다
4. 새로 삽입한 노드가 제 위치를 찾을 때까지 2~3을 반복한다.

# 힙 데이터 삽입 구현하기

## 과정

우선순위 큐는 `PriorityQueue`라는 클래스로 정의되어 있고, 그 안에 힙이 있다. `PriorityQueue` 클래스에는 `heap`이라는 인스턴스 변수가 있고, 이것은 파이썬의 리스트를 가리킨다. 가장 처음 `heap`에는 `None`이라는 원소 하나만 있다.

힙에 데이터를 삽입하는 메소드의 이름은 `insert`이다. `insert` 메소드는 데이터를 삽입할 때 리스트가 계속 힙의 속성을 유지하도록 하는 기능도 포함해야 한다.

`insert` 메소드로 데이터를 삽입할 때 이루어져야 하는 일은 3단계로 나눌 수 있다.

1. 힙의 마지막 인덱스에 노드를 삽입한다.
2. (1) 삽입한 노드와 그 부모 노드를 비교해서 부모 노드가 더 작으면 둘의 위치를 바꾸고, (2)부모 노드가 더 크거나 같으면 그대로 둔다.
3. 2-1의 경우에는 삽입한 노드가 올바른 위치를 찾을 때까지 단계 2를 반복한다.

이때 단계 2와 단계 3의 작업을 하는 별도의 함수 `reverse_heapify`를 정의해 놓고 사용한다.

이 함수는

- 리스트로 구현한 완전 이진 트리, `tree`
- 삽입된 노드의 인덱스, `index`

를 파라미터로 받는다. 그리고 삽입된 노드를 힙 속성을 유지할 수 있는 위치로 이동시킨다.

이전에 배운 `heapify` 함수가 위에 있는 노드를 아래로 이동시켜서 힙 속성을 유지했다면 `reverse_heapify` 함수는 아래에 있는 노드를 위로 이동시켜서 힙 속성을 유지시킨다.

`reverse_heapify` 함수만 완성되면 `insert` 메소드를 완성하는 것은 간단하다

`insert` 함수는

- `self`
- 삽입하는 데이터, `data`

를 파라미터로 받는데, `insert` 메소드는

1. 리스트, `heap`의 마지막에 새로운 데이터를 삽입하고
2. 그 마지막 인덱스를 `reverse_heapify` 함수에 파라미터로 넘겨서 호출하면 된다.

## 힙에 데이터 삽입하기

```python
def swap(tree, index_1, index_2):
    """완전 이진 트리의 노드 index_1과 노드 index_2의 위치를 바꿔준다"""
    temp = tree[index_1]
    tree[index_1] = tree[index_2]
    tree[index_2] = temp

def reverse_heapify(tree, index):
    """삽입된 노드를 힙 속성을 지키는 위치로 이동시키는 함수"""
    parent_index = index // 2  # 삽입된 노드의 부모 노드의 인덱스 계산
    # 해당 자식 노드가 부모 노드보다 크면 두 노드의 위치를 바꾼다
    if 0 < parent_index and tree[parent_index] < tree[index]:
        swap(tree, parent_index, index)
        reverse_heapify(tree, parent_index)





class PriorityQueue:
    """힙으로 구현한 우선순위 큐"""
    def __init__(self):
        self.heap = [None]  # 파이썬 리스트로 구현한 힙

    def insert(self, data):
        """삽입 메소드"""
        # 1 힙의 마지막 인덱스에 노드를 삽입한다
        self.heap.append(data)

        # 2 삽입한 노드와 그 부모 노드를 비교해서 부모 노드가 더 작으면 둘의 위치를 바꾼다
        reverse_heapify(self.heap, len(self.heap)-1)

    def __str__(self):
        return str(self.heap)

# 실행 코드
priority_queue = PriorityQueue()

priority_queue.insert(6)
priority_queue.insert(9)
priority_queue.insert(1)
priority_queue.insert(3)
priority_queue.insert(10)
priority_queue.insert(11)
priority_queue.insert(13)

print(priority_queue)
# [None, 13, 9, 11, 3, 6, 1, 10]
```

# 힙에서 최고 우선순위 데이터 추출하기

## 힙에서 root 노드 데이터 추출하기

- root 노드와 마지막 노드를 서로 바꿔 준다.
- 마지막 노드의 데이터를 변수에 저장해 준다.
- 마지막 노드를 삭제한다.
- root 노드에 heapify를 호출해서 망가진 힙 속성을 고친다.
- 변수에 저장한 데이터를 리턴한다 (최고 우선순위 데이터)

# 힙 우선순위 데이터 추출 구현

## 단계

1. root 노드와 마지막 노드의 위치를 바꾼다
2. 마지막 위치로 간 원래 root 노드의 데이터를 별도 변수에 저장하고, 노드는 힙에서 지운다
3. 새로운 root 노드를 대상으로 heapify해서 망가진 힙 속성을 복원한다
4. 2단계에서 따로 저장해 둔 최우선순위 데이터를 리턴한다

### heapify_code.py

```python
def swap(tree, index_1, index_2):
    """완전 이진 트리의 노드 index_1과 노드 index_2의 위치를 바꿔준다"""
    temp = tree[index_1]
    tree[index_1] = tree[index_2]
    tree[index_2] = temp

def heapify(tree, index, tree_size):
    """heapify 함수"""

    # 왼쪽 자식 노드의 인덱스와 오른쪽 자식 노드의 인덱스를 계산
    left_child_index = 2 * index
    right_child_index = 2 * index + 1

    largest = index  # 일단 부모 노드의 값이 가장 크다고 설정

    # 왼쪽 자식 노드의 값과 비교
    if 0 < left_child_index < tree_size and tree[largest] < tree[left_child_index]:
        largest = left_child_index

    # 오른쪽 자식 노드의 값과 비교
    if 0 < right_child_index < tree_size and tree[largest] < tree[right_child_index]:
        largest = right_child_index

    if largest != index: # 부모 노드의 값이 자식 노드의 값보다 작으면
        swap(tree, index, largest)  # 부모 노드와 최댓값을 가진 자식 노드의 위치를 바꿔준다
        heapify(tree, largest, tree_size)  # 자리가 바뀌어 자식 노드가 된 기존의 부모 노드를대상으로 또 heapify 함수를 호출한다

def reverse_heapify(tree, index):
    """삽입된 노드를 힙 속성을 지키는 위치로 이동시키는 함수"""
    parent_index = index // 2  # 삽입된 노드의 부모 노드의 인덱스 계산

    # 부모 노드가 존재하고, 부모 노드의 값이 삽입된 노드의 값보다 작을 때
    if 0 < parent_index < len(tree) and tree[index] > tree[parent_index]:
        swap(tree, index, parent_index)  # 부모 노드와 삽입된 노드의 위치 교환
        reverse_heapify(tree, parent_index)  # 삽입된 노드를 대상으로 다시 reverse_heapify 호출
```

### main.py

```python
from heapify_code import *

class PriorityQueue:
    """힙으로 구현한 우선순위 큐"""
    def __init__(self):
        self.heap = [None]  # 파이썬 리스트로 구현한 힙

    def insert(self, data):
        """삽입 메소드"""
        self.heap.append(data)  # 힙의 마지막에 데이터 추가
        reverse_heapify(self.heap, len(self.heap)-1) # 삽입된 노드(추가된 데이터)의 위치를 재배치

    def extract_max(self):
        """최우선순위 데이터 추출 메소드"""
        tree = self.heap
        # 1. root 노드와 마지막 노드의 위치를 바꾼다
        swap(tree, 1, len(tree)-1)

        # 2. 마지막 위치로 간 데이터를 별도 변수에 저장, 노드를 힙에서 삭제
        return_value = self.heap.pop()

        # 3. 새로운 root 노드를 대상으로 heapify
        heapify(tree, 1, len(tree))

        # 4. 2단계에서 따로 저장해 둔 최우선순위 데이터를 리턴한다
        return return_value


    def __str__(self):
        return str(self.heap)

# 출력 코드
priority_queue = PriorityQueue()

priority_queue.insert(6)
priority_queue.insert(9)
priority_queue.insert(1)
priority_queue.insert(3)
priority_queue.insert(10)
priority_queue.insert(11)
priority_queue.insert(13)

print(priority_queue.extract_max()) # 13
print(priority_queue.extract_max()) # 11
print(priority_queue.extract_max()) # 10
print(priority_queue.extract_max()) # 9
print(priority_queue.extract_max()) # 6
print(priority_queue.extract_max()) # 3
print(priority_queue.extract_max()) # 1
```

  </details>
  <details>
    <summary>힙 삽입, 추출 시간 복잡도 & 힙으로 구현한 우선순위 큐 평가</summary>

# 힙 삽입, 추출 시간 복잡도

## 힙의 삽입 연산 시간 복잡도

힙에 있는 노드의 개수를 n개라고 가정한다.

### 힙의 삽입 연산 단계

1. 힙의 마지막 인덱스에 노드를 삽입한다.
2. (1) 삽입한 노드와 그 부모 노드를 비교해서 부모 노드가 더 작으면 둘의 위치를 바꾸고, (2) 부모 노드가 더 크거나 같으면 그대로 둔다.
3. 2-(1)의 경우에는 삽입한 노드가 올바른 위치를 찾을 때까지 단계 2를 반복한다.

### 1단계

먼저 힙의 마지막에 노드를 삽입해야 한다. 힙을 동적 배열로 구현했으니, 동적 배열에 원소를 추가하는 것의 시간 복잡도를 분할 상환 분석하면 O(1)이다.

### 2단계

1. 삽입된 노드의 값과 부모 노드의 값을 비교하는 건 O(1)이 걸린다.
2. 삽입된 데이터가 더 큰 경우 부모 노드와의 위치를 바꿔주는 것과 마찬가지로 O(1)이 걸린다.

즉, 2단계에서는 O(2)이 걸리는데, 이건 O(1)과 동일하다.

### 3단계

최악의 경우 2단계를 몇 번이나 반복해야할까? 최악의 경우는 삽입한 데이터가 leaf 노드부터 시작해서 root 노드까지 올라가는 경우인데, 그럼 힙의 높이만큼 2단계를 반복해야 한다.

힙의 높이는 lg(n)에 비례하니까 시간은 O(lg(n))이다. 이 말은, 2단계의 시간인 O(1)를 최대 O(lg(n))번 반복할 수 있다는 말이니까 결국 시간 복잡도는 O(lg(n))이 걸린다.

### 정리

1. 1단계의 O(1)
2. 2단계, 3단계의 O(lg(n))

를 더하면 O(1+lg(n))이 되고, 이건 곧 O(lg(n))과 같다.

결론적으로, 힙에 데이터를 삽입하는 연산의 시간 복잡도는 **O(lg(n))**이다.

## 힙의 추출 연산 시간 복잡도

이제 힙에서 가자 우선 순위가 높은 데이터를 추출하는 데에 시간이 얼마 걸리는지 알아보자. 이번에도 힙에 있는 노드의 개수를 n이라고 한다.

### 힙의 추출 연산 단계

1. root 노드와 마지막 노드의 위치를 바꾼다.
2. 마지막 위치로 간 원래 root 노드의 데이터를 별도 변수에 저장하고, 노드는 힙에서 지운다.
3. 새로운 root 노드를 대상으로 `heapify`해서 망가진 힙 속성을 복원한다.
4. 2단계에서 따로 저장해 둔 최우선순위 데이터를 리턴한다.

### 1단계

root 노드와 마지막 노드위 위치를 바꾸는 건 노드의 개수랑은 전혀 상관 없이 O(1)이 걸린다.

### 2단계

데이터를 변수에 지정하는 것은 O(1)이 걸린다. 힙을 동적 배열로 구현했으니, 동적 배열에서 마지막 인덱스의 원소를 삭제하는 건 분할 상환 분석을 하면 O(1)이 걸린다. 이 단계는 총 O(1+1)이 걸리니까 O(1)이 걸리는 것이다.

### 3단계

새로운 root 노드를 대상으로 `heapify`를 호출해서 망가진 힙 속성을 복원하는 단계이다. `heapify`는 O(lg(n))이 걸린다.

### 4단계

변수를 리턴하는 건 O(1)이 걸린다.

### 정리

총 걸리는 시간을 더하면 O(1+1+lg(n)+1)이다. 여기서 1은 다 무시해도 되니까, 힙에서 가장 우선 순위가 높은 데이터를 추출하는 연산의 시간 복잡도는 **O(lg(n))**이다.

# 힙으로 구현한 우선순위 큐 평가

우선순위 큐를 구현할 때는 힙 말고도 다른 자료 구조들을 활용할 수도 있다.

- 정렬된 동적 배열
- 정렬된 더블리 링크드 리스트

## 정렬된 동적 배열

### 삽입 연산

동적 배열에 데이터가 정렬된 채(오름차순 또는 내림차순)로 있다고 가정하고 새로운 데이터를 삽입할 때는 생각해보자. 새로운 데이터를 정렬된 동적 배열에 삽입하려면 크게 두 가지 작업을 해야한다.

1. 먼저 새로운 데이터가 어느 위치에 들어가야 하는지를 찾고
2. 그위치에 데이터를 넣어야 한다.

### 삽입 연산 시간 복잡도

1. 삽입할 위치를 찾는 것은 이진 탐색을 사용하면 O(lg(n))이 걸린다.
2. 그리고 그 위치에 데이터를 삽입하는 건 최악의 경우 O(n)이 걸린다.

그럼 삽입 연산은 총 O(lg(n) + n)이 걸리고, 이는 곧 O(n)과 같다.

결국, 정렬된 동적 배열에 데이터를 삽입하는 연산은 **O(n)**이 걸린다.

### 추출 연산

동적 배열이 항상 정렬된 상태라면 가장 우선순위가 높은 데이터는 항상 배열의 끝에 있을 것이다. 그래서 추출할 때는 그냥 마지막 데이터를 삭제함과 동시에 리턴하면 된다.

동적 배열 맨 뒤에 있는 데이터를 추출하는 연산은 O(1)이 걸린다.

결국, 정렬된 동적 배열에서 가장 우선순위가 높은 데이터를 추출하는 연산은 **O(1)**이 걸린다.

## 정렬된 더블리 링크드 리스트

### 삽입 연산

일단 데이터를 삽입해야 하는 위치를 찾아야 한다. 링크드 리스트에서는 이럴 때 선형 탐색을 해야 한다. 그러니까 head 노드부터 순서대로 하나씩 노드를 확인하면서 삽입할 위치를 찾아야 하는데, 총 노드 수가 n이라고 했을 때, 최악의 경우 n개의 노드를 다 봐야 한다.

예를 들어, `| 3 | 5 | 6 | 8 | 9 |` 이렇게 정렬된 더블리 링크드 리스트에서 10을 삽입하고 싶으면 선형 탐색으로 3부터 9까지를 다 확인해야 한다.

- 9 뒤에 삽입해야 한다는 걸 알기 위해 n개의 노드를 다 봐야 하는 것이다. 그러니까 삽입할 위치를 찾는 단계는 O(n)이 걸린다.

그럼 삽입은 얼마나 걸릴까? 위치만 정해지고 나면 링크드 리스트에서 데이터를 삽입하는 건 O(1)에 할 수 있다. 위치만 정해지고 나면 링크드 리스트에서 데이터를 삽입하는 건 O(1)에 할 수 있다.

결국, 정렬된 더블리 링크드 리스트에 데이터를 삽입하는 것은 O(1+n)이 걸리고, 이건 **O(n)**과 같다.

### 추출 연산

더블리 링크드 리스트에서 마지막 데이터를 추출하는 데에는 O(1)이 걸린다.

결국, 정렬된 더블리 링크드 리스트에서 가장 우선순위가 높은 데이터를 추출하는 데 **O(1)**이 걸리는 것이다.

## 힙

힙으로 우선순위 큐를 구현할 때에는, 힙에 데이터를 삽입하는 연산과 추출하는 연산의 시간 복잡도는 모두 O(lg(n))이었다.

## 우선순위 큐 시간 복잡도 정리

- 정렬된 동적 배열: 삽입=O(n), 추출=O(1)
- 정렬된 더블리 링크드 리스트: 삽입=O(n), 추출=O(1)
- 힙: 삽입=O(lg(n)), 추출=O(lg(n))

우선순위를 사용할 때

- 정렬된 동적 배열이나 정렬된 더블리 링크드 리스트를 사용하면 데이터를 추출할 때 더 효율적
- 힙을 사용하면 데이터를 삽입할 때 더 효율적

## 우선순위 큐는 뭐로 구현하는 게 가장 좋을까?

만약 새로운 데이터를 삽입할 일이 많으면 힙으로,

기존 데이터를 추출할 일이 더 많으면 정렬된 동적 배열이나 정렬된 더블리 링크드 리스트로 구현하는 게 좋을 것이다.

이렇게 우선순위 큐와 같은 어떤 추상 자료형을 구현할 때는 특정 방식이 항상 더 낫다고 단정하기 힘들다. 단지, 개발자가 처한 상황에 따라 정답이 달라질 뿐이고, 개발자는 이러한 것을 잘 판단해야겠다.

  </details>
</details>

<details>
  <summary>3) 이진 탐색 트리</summary>
</details>
