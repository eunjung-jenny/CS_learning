# 7. Popular Algorithms Case

## 1) Shortest path problem

- A graph with unweighted edges = `Edges/3` => **BFS**
- A graph with weighted edges = `min(sum(weight of edge))` 

### (1) Dijkstra's Algorithms

- A Solution for a shortest path problem for a **weighted undirected** graph
- 방식: **min priority queue** & **Greedy algorithm**
  1. 시작 노드에 0, 그 외의 각 노드에 무한의 값을 대응시키고 min priority queue에 모두 enqueque
  2. queue에서 차례로 dequeue 를 하면서 시작 노드부터 해당 노드의 인접 노드까지의 sum of weight of edges를 재확인하고 기존의 대응값보다 작은 경우 이를 갱신
  3. 2 과정을 반복
- `O(2^N)`

## 2) Knapsack problem

> 무게 제한이 있는 배낭과 이를 초과하는 양의 물건들이 존재한다. 각 물건들은 무게와 가치 속성을 가질 때, 무게 제한을 지키면서 배낭 속 물건들의 총 가치를 최대로 최적화하는 방법은?

#### 0-1 knapsack problem

> 각각의 물건은 단 하나 존재하며, 가방에 넣거나 넣지 않거나의 선택지만 존재

### (1) Brute force

- `O(2^N)` : exponential time
- Exponential time vs. Polynomial tims
  - Exponential time: `O(x^N)`
  - Polynomial time: `O(xN^y)`
  - N이 커지면 polynomial time algorithms 가 exponential time algorithms 보다 훨씬 빠름

### (2) Dynamic Programming

- `Max value for min weight` 방식의 테이블을 작성한 후 작은 무게들의 합으로 무게 제한을 달성

![image-20200402142951847](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200402142951847.png)

![image-20200402143016600](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200402143016600.png)

![image-20200402143048790](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200402143048790.png)

![image-20200402143156882](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200402143156882.png)

![image-20200402143210952](/Users/eunjung/Documents/github-blog/_drafts/images/image-20200402143210952.png)

- `O(n*W)` : Pseudo-polynomial time
  - n: number of elements
  - W: weight limit
- Dynamic programming?

> 모든 경우의 수를 생각해야 할 것 같은 복잡한 문제를 만났을 때, sub-problem 으로 쪼갤 수 있을 것인가? 를 생각해 봐야 함

- 특징 1: 문제가 더 작은 문제로 쪼개짐
  - Problem: Max value for weight limit
  - Sub-problem: Max value for some **smaller** weight
  - Base case: Smallest computation
- 특징 2: sub-problem의 해를 저장하는 lookup table을 작성
  - **Memoization 기법** : 사전에 계산했던 결과값을 저장
  - lookup table을 활용하여 원 문제의 복잡도 수준까지 복잡도를 서서히 증가시킴
- 특징 3: 문제의 복잡도를 증가시키는 단계마다 사용하는 계산식이 존재함
  - 위의 예시에서는 `value of weight limit (11) = value of current object (weight 4: 5) + value in table at [weight limit - current object] (weight 2: 6)`

## 3) Traveling salesman problem

> What is the fasstest way for our salesman to travel between every city and return home

- **NP-hard problems** : polynomial time 으로 해결할 수 있는 알고리즘이 밝혀지지 않은 문제들 (Knapsack problem 도 NP-hard problem)
  - Exact algorithms : 정확한 답을 구해주지만 polynomial time 이 아님
    - Brute force : `O(N!)`
    - DP :
      - Held-Karp algorithm : `O(N^2 * 2^N)`
  - Approximation algorithms : 정확하진 않지만 근사한 답을 구해주며 시간 복잡도의 측면에서 exact algorithms 보다 개선됨
    - Christofides algorithms : 그래프를 트리로 보고 접근하는 방식