# 3. Searching and Sorting



## 1) Binary Search and Efficiency

- 임의의 중복되지 않고 오름순으로 정렬된 숫자들로 이루어진 array 에서 특정 숫자가 array 에 포함되어 있는지를 찾아보자.
  - 한 쪽 끝에서 차례대로 확인한다면, `O(N))` (worst case)
  - 중간에서부터 확인을 시작하여 작은 쪽, 큰 쪽으로 범위를 줄여가며 확인한다면, `O(logN)` (worst case) => **binary search**
- Binary Search 를 수행할 때 원소의 개수가 홀수이면, 중간을 기준으로, 짝수이면 중간을 기점으로 왼쪽이나 오른쪽 중 하나를 기준으로 하여 **일관성**을 지켜줘야 함

```python
# binary search

def binary_search(input_array, value):
    lb = 0
    ub = len(input_array) - 1
    
    while lb <= ub:
        idx = (lb + ub)//2
        if input_array[idx] == value:
            return idx
        else:
            if input_array[idx] < value:
                lb = idx + 1
            else:
                ub = idx - 1
                
    return -1
```

### [Tip] 새로운 알고리즘의 복잡도 추정은 results table 로!

| Array Size | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    |
| ---------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Iterations | 0    | 1    | 2    | 2    | 3    | 3    | 3    | 3    | 4    |



## 2) Recursion

- **A function that calls itself** with an alteration of an input parameter ( or 무한루프)
- **Base case** : exit condition ( or 무한루프 )

```python
# fibonacci sequence
def get_fib(position):
    if position <= 1:
        return position
    else:
        return get_fib(position-1) + get_fib(position-2)
```



## 3) Bubble Sort

- Naive approach
- 제일 앞에서부터 두 개의 숫자를 비교하며 필요에 따라 순서를 변경, 한 라운드를 마칠 때마다 제일 큰 원소가 제일 뒤로 정렬됨.
- 예시: 8 3 1 7 0
  - 1 라운드
    - 3 8 1 7 0
    - 3 1 8 7 0
    - 3 1 7 8 0
    - 3 1 7 0 8
  - 2 라운드
    - 1 3 7 0 8
    - 1 3 7 0 8
    - 1 3 0 7 8
  - 3 라운드
    - 1 3 0 7 8
    - 1 0 3 7 8
  - 4 라운드
    - 0 1 3 7 8
- 복잡도
  - time
    - worst case  `O(N^2)`  : Iteration (N - 1) * Comparisons (N - 1)
    - best case `O(N)` : 이미 정렬되어 있는 경우
  - space
    - `O(1)` : *in-place sorting algorithm* - 주어진 array 내에서 원소의 순서를 변경해가면서 정렬 => low space complexity

## 4) Merge Sort

- *Divide and Conquer*

- 예시: 8 3 1 7 0 10 2

  - | 8 | 3 | 1 | 7 | 0 | 10 | 2 |
  - 1 라운드 ( 8: 깍두기 ) : 3회 비교
    - | 8 | 1 3 | 0 7 | 2 10 |
  - 2 라운드 ( 각각의 조각은 이미 정렬된 상태 ) : 5회 비교
    - | 1 3 8 | 0 2 7 10 |
  - 3 라운드 : 6회 비교
    - | 0 1 2 3 7 8 10 |

- 복잡도

  - time
    - `O(N * log(N))` : (# of comparisons per step) * (# of steps)
  - space
    - `O(N)` : Auxillary Space 

- [추가](https://algs4.cs.princeton.edu/22mergesort/)

  - Top-down Merge Sort

    ![스크린샷 2020-03-23 오후 7.58.12](/Users/eunjung/Documents/CS_learning/DS_Algorithms/udacity_intro2DSnAlgorithms/images/스크린샷 2020-03-23 오후 7.58.12.png)

  - Bottom-up Merge Sort

    ![스크린샷 2020-03-23 오후 7.59.12](/Users/eunjung/Documents/CS_learning/DS_Algorithms/udacity_intro2DSnAlgorithms/images/스크린샷 2020-03-23 오후 7.59.12.png)

## 5) Quick Sort

- **In many cases, Quick Sort is one of the most efficient sorting algorithms.**
- array 내의 임의의 원소( `pivot` )를 선택, 이를 기준으로 왼편으로는 더 작은 수를, 오른편으로는 더 큰 수를 보내고, 왼편과 오른편에서 이와 같은 과정을 각각 반복하여 진행
- 예시: 8 3 1 7 0 10 2
  - 1 라운드 (pivot: 마지막 원소 `2` 선택)
    - 8 3 1 7 0 10 | 2 |
    - 10 3 1 7 0 | 2 | 8 
    - 0 3 1 7 | 2 | 10 8
    - 0 7 1 | 2 | 3 10 8
    - 0 1 | 2 | 7 3 10 8
  - 2 라운드 - 1
    - 0 | 1 2 | 7 3 10 8
    - 0 1 2 | 7 3 10 8
  - 2 라운드 - 2
    - 0 1 2 | 7 3 10 | 8 |
    - 0 1 2 | 7 3 | 8 10 |
  - 3 라운드
    - 0 1 2 | 7 | 3 | 8 10 |
    - 0 1 2 3 7 8 10
- 복잡도
  - time
    - worst case `O(N^2)` : 임의로 선택한 pivot 이 제자리에 위치해있는 경우
    - average / best case `O(NlogN)`
  - space
    - `O(1)`



## 참고

- [visualgo](https://visualgo.net/en/sorting) : sort visualization & pseudo code