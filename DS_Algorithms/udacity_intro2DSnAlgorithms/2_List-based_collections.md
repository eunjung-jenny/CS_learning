# 2. List-based Collections



## 1) Collection 이란?

- just a group of things
- 기본적으로는 특정한 순서를 가지고 있지도 않고, 서로 다른 유형끼리 구성될 수도 있음.

### (1) List

- Collection 에서 **순서**가 있는 경우.
- **python 의 list 는 array 로 구현되어 있으며 stack, queue 등 collection 으로 분류되는 대부분의 데이터 구조의 역할을 함**

### (2) Array

- Collection에서 **순서**가 있고, **Index** 로 접근할 수 있는 경우.
  - 장점: 특정 위치에 접근하기 편리함
  - 단점: 삽입과 삭제가 어려움 <= 해당 index 뒤쪽의 모든 원소들을 하나씩 이동시켜야 함.
- 프로그래밍 언어에 따라 같은 자료형으로만 구성되야 하는 경우도 있고 그렇지 않은 경우도 있음.
- 프로그래밍 언어에 따라 고정된 크기를 갖는 경우도 있고, 그렇지 않은 경우도 있음.

### (3) Linked List

- Collection에서 **순서**가 있고, **Index** 는 없으나, 각 원소는 다음 원소를 가리키고 있음.
  - 장점: 삽입과 삭제가 array에 비해 편리함. <= 그러나 index 가 없으므로 삽입하고 삭제할 위치에까지 도달하기 위해서는 head부터 차례로 탐색하는 과정이 필요함.

### (*) Array vs. Linked List

- Array : node 에 대한 정보는 해당 node의 index 와 데이터.
- Linked List : node 에 대한 정보는 해당 node 의 데이터와 다음 node 의 주소. => array 와 달리 각 node 가 메모리 상에서 서로 인접해있지 않아도 됨.

### (4) Stack

- ~~프링글스~~
- **LIFO** (Last In, First Out) : 제일 위(앞)에 새로운 요소를 넣을 수 있고 제일 위(앞)에서부터 요소를 꺼낼 수 있음.
- `push()`, `pop()` : 모두 O(1)

### (5) Queue

- ~~한 줄 서기~~
- **FIFO** (First In, First Out) : 제일 뒤에 새로운 요소가 들어갈 수 있고, 제일 앞에서부터 요소를 꺼낼 수 있음.
- `enqueue()`, `dequeue()`, `peek()`

#### (5-1) Deque

- Double-ended Queue: 양 쪽 끝에서 enqueue, dequeue 가능
- (python) `from collections import deque`

#### (5-2) Priority Queue

- 각 node에 우선순위를 함께 저장함.
- dequeue: 가장 우선순위가 높고, 먼저 enqueue 된 node 부터 제거.