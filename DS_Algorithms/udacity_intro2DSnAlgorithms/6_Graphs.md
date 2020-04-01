# 6. Graphs

## 1) What is a graph?

![image-20200401234808264](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200401234641427.png)

- 그래프(=네트워크) 의 목적: 서로 어떻게 연결되어 있는가를 나타내기 위함
- **트리 또한 그래프의 특수한 경우로 볼 수 있음**
- 특징
  - node 와 edge (주로 strength) **모두** 데이터를 포현할 수 있음
  - edge는 **direction**이라는 속성을 가질 수 있음
    - from -> to
    - cycle 형성 가능 > **infinite loop 이슈 발생 가능성**
  - **connectivity**
    - connected graph: edge 로 모든 노드가 연결
      - weakly connected graph: directed graph에서 edge들을 undirected edge로 변경했을 때 connected graph가 되는 경우
      - strongly connected graph: 모든 노드가 양 방향으로 서로 연결
    - disconnected graph
      - edge 로 연결되어 있지 않으나 그룹 내에서는 서로 연결되어 있는 노드 그룹들이 존재
      - edge 로 연결되어 있지 않은 단일 노드가 존재
    - connectivity 는 **주어진 그래프가 disconnected graph가 되기 위해 제거해야 하는 최소한의 노드 수**를 의미

## 2) Graph Representations

- 객체 지향 언어
  - vertex 클래스: id, data1, data2, edge1, edge2, edge3, ...
  - edge 클래스: id, data1, vertex1, vertex2, ...

- Edge list

![image-20200402000839205](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200402000839205.png)

- Adjacency list

![image-20200402001125903](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200402001125903.png)

- Adjacency matrix

![image-20200402001237477](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200402001237477.png)

## 3) Graph Traversal

- 모든 엣지를 두 번씩 방문하게 됨 (탐색과 되돌아가기)

### (1) Depth First Search

- `O(|E|+|V|)`
- [visualization](https://www.cs.usfca.edu/~galles/visualization/DFS.html)

#### Stack 접근

1. 트리와 달리 root 노드가 존재하지 않으므로 임의의 노드에서 시작

2. 확인한 노드에 대해 확인했다는 표시, 해당 노드를 스택에 푸시, 임의의 edge를 골라 진행하는 과정을 반복

3. 확인했던 노드에 도달한 경우, 스택을 pop 하면서 방문했던 노드를 차례대로 되돌아감

4. 진행했던 경로를 되돌아가다가 확인하지 않은 노드와 연결된 노드가 있다면 다시 2, 3, 4 과정을 반복

#### Recursion 접근

- Stack에서 반복되는 한 라운드가 base case가 됨

### (2) Breadth First Search

- `O(|E|+|V|)`
- [visualization](https://www.cs.usfca.edu/~galles/visualization/BFS.html)

1. 임의의 노드에서 시작
2. 확인한 노드에 대해 확인했다는 표시
3. edge로 연결된 모든 노드를 차례대로 한 번씩 방문하면서 확인했다는 표시, 큐에 enqueque
4. 해당 노드에서 더 이상 방문할 노드가 없을 경우, 큐에서 하나씩 dequeque하면서 해당 노드를 기준으로 3, 4 과정을 반복



## 4) Notable Types of Paths

### (1) Eulerian Path

- 그래프의 edge들을 한 번씩만 방문하면서 모든 edge를 다 방문하는 경로
- 조건: 모든 node의 degree(= 해당 노드와 연결된 edge의 수)가 모두 짝수이거나 경로의 시작과 끝 지점의 두 개의 node만 홀수 degree를 갖는 경우

### (2) Eulerian Cycle

- Eulerian path 중 시작지점과 종료지점이 동일한 경로

- 조건: 모든 node의 degree(= 해당 노드와 연결된 edge의 수)가 모두 짝수

- eulerian cycle 을 찾는 알고리즘

  - `O(|E|)`

  1. 임의의 노드에서 출발하여 해당 노드로 되돌아 올 때까지 edge를 따라 진행
  2. 이를 통해 모든 edge를 방문하지 못한 경우, 방문했던 노드에 연결되어있는 방문하지 않은 edge에서 1 과정을 다시 시작
  3. 모든 edge를 방문할 때까지 1, 2 과정을 반복
  4. 만들어진 경로들을 각 경로에서 공통으로 포함하고 있는 노드를 이용해 연결

### (3) Hamiltonian Path

- 그래프의 node들을 한 번씩만 방문하면서 모든 node를 방문하는 경로
- 조건: 아직까지 해결되지 않음

### (4) Hamiltonial Cycle

- Hamiltonial path 중 시작지점과 종료지점이 동일한 경로

- 조건: 아직까지 해결되지 않음