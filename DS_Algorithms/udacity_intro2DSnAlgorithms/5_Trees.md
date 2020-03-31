# a5. Trees

## 1) Basics and Terminology

- Linked-list 의 확장 버전으로, linked-list 는 하나의 node 가 다음 하나의 node 만을 가리키는 반면 tree 는 여러 개의 node 를 가리킬 수 있음
- 조건
  1. NO unconnected nodes
  2. NO cycles
- 용어
  - node : 각 요소들
  - root : 시작 노드
  - leaf : 가장 끝에 위치한 노드
  - edge : 노드간의 연결
  - path : 특정한 두 노드를 연결하는 엣지들의 그룹
  - level : root (level = 1) 을 기준으로 떨어져있는 정도
  - height : leaf (height = 0) 을 기준으로 특정 노드와 가장 멀리 있는 leaf 사이 존재하는 엣지의 개수
  - depth : root (depth = 0) 을 기준으로 특정 노드와 leaf 사이 존재하는 엣지의 개수
  - 부모노드-자식노드 : 자식노드는 단 하나의 부모노드를 가짐

## 2) Tree Traversal

![image-20200328205414074](/Users/eunjung/Documents/CS_learning/DS_Algorithms/udacity_intro2DSnAlgorithms/images//image-20200328205414074.png)

### (1) DFS (Depth First Search)

- 탐색할 자식 노드가 있다 해당 자식 노드를 우선으로 탐색

#### Pre-order traversal

- D - B - A -C - E - F

#### In-order traversal (왼쪽 자식 우선)

- A - B - C - D - E - F

#### Post-order traversal (자식 우선)

- A - C - B - F - E - D



### (2) BFS (Breadth First Search)

- 자식 노드를 탐색하기 전에 동일한 레벨의 모든 노드를 우선으로 탐색



## 3) Binary Trees

- 각각의 부모 노드들이 최대 2개의 자식 노드를 가질 수 있는 트리
- **Perfect Tree** : leaf 노드를 제외한 모든 노드들이 2개의 자식노드를 갖는 트리
- **순서가 없는** 트리에서 작업 내용에 따른 시간 복잡도
  - Search : `O(n)`
  - Delete : `O(n)`
  - Insert : `O(logN)`

### Binary Search Tree (BST)

- 노드 배치에 관한 규칙이 있는 정렬된 binary tree
- 특정 노드의 값보다 작은 값은 왼편의 자식 노드에, 큰 값은 오른편의 자식 노드에 배치
- 시간 복잡도
  - Search: `O(logN)`
  - Insert: `O(logN)`

## 4) Heap

- root 에서부터 각 노드의 데이터 값이 오름차순 또는 내림차순으로 정렬되어 있는 트리

  - Max heap : root 노드의 데이터 값이 가장 큼
  - Min heap : root 노드의 데이터 값이 가장 작음

- 시간 복잡도 **(Max Binary Heap 의 경우)**

  - Search
    - Worst: `O(n)`
    - Average: `O(N/2) == O(N)` (찾고자 하는 값이 노드의 값보다 큰 경우에는 탐색을 중단)
  - Insert:
    - 이에 대한 대안으로, 빈 자리의 첫 번째 위치에 우선 삽입한 후 부모 자식과의 비교 과정을 반복함
  - **heapify** : heap 의 특징에 따라 트리를 재정렬하는 작업
    - Insert: 빈 자리의 첫 번째 위치에 우선 삽입한 후 부모 자식과의 비교, swap 과정을 반복함
      - `O(logN)`
      - heapify 를 활용하지 않는 경우, 삽입하고자 하는 값이 트리의 처음~중간에 위치해야 하는 경우에 여러 번의 shuffle 이 필요해짐
    - delete: 가장 오른편의 leaf 노드로 비워진 노드를 채운  자식 노드와의 비교, swap 과정을 반복함
      - `O(logN)`

  ### Heap Implementation

  - Heap 은 트리로 분류되지만, 많은 경우에 있어서 **array 로 구현됨**
    - 메모리를 아낄 수 있음 (value, left-ch, right-ch, parent => value, index)
  - 다음과 같이 정렬되어있는 array 와 heap 은 서로 쉽게 호환됨

  ![image-20200331223727436](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200331223727436.png)

  ![image-20200331223818984](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200331223818984.png)

  `

## 5) Self-balancing Trees

- **Balanced tree** : 좌, 우 sub-tree 간의 균형이 맞는 트리로, level 이 최소화됨
  - Linked-list : extremely unbalanced tree
- **Self-balancing tree**: insert, deletion 과 같은 연산을 수행하는 과정에서 스스로 level 의 수를 최소화하려는 트리

## 6) Red-Black Trees

- **대표적인 self-balancing tree** 이자 **binary search tree**
- 규칙
  1. 노드는 red 또는 black 중 하나를 색상 속성으로 가짐
  2. 모든 노드는 null leaf node (black) 를 포함하여 2개의 자식 노드를 가짐
  3. red 노드의 자식 노드는 모두 black
  4. root 노드는 black
  5. 모든 특정 노드부터 해당 노드의 자손 중에 있는 null node 까지의 path는 동일한 개수의 black 노드를 포함함

![image-20200331224728200](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200331224728200.png)

### Insertion

- O(logN) : search, deletion 도 마찬가지
  - Binary search tree 의 경우, balance 조건이 없기 때문에 최악의 경우 시간복잡도가 더 높음

1. 우선 red 노드로서 삽입

2. 삽입한 노드가 root 노드일 경우 black으로 변경

3. 삽입한 노드의 부모 노드와 부모의 형제 노드가 모두 red 노드일 경우, 부모 노드, 부모 형제 노드, 부모의 부모 노드를 red 노드로 변경
   - 부모의 부모 노드가 root 노드인 경우, 2번에 따라 다시 black 으로 변경

**Rotation**: 삽입한 노드의 부모 노드가 red, 부모의 형제 노드가 black일 경우에 수행하며, 노드 순서의 변화 없이 트리 구조를 변화시킴

4. 삽입한 노드와 부모 노드가 각각 자신의 부모 노드기준 서로 다른 방향에 있으면서 Rotation이 필요한 경우, 다음과 같이 왼쪽 방향으로 회전
   - 그 결과: 5번의 경우가 됨

![image-20200331230333107](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200331230333107.png)

5. 삽입한 노드와 부모 노드가 각각 자신의 부모 노드기준 서로 같은 방향에 있으면서 Rotation이 필요한 경우, 다음과 같이 노드의 색상을 변경하면서 오른쪽 방향으로 회전

![image-20200331230403272](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200331230403272.png)

![image-20200331230509030](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200331230509030.png)

![image-20200331230537998](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200331230537998.png)

