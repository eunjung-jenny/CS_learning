# 4. Maps and Hashing



## 1) Sets

- collection 의 일부이지만 원소들 간 **순서가 없고 중복을 허용하지 않음**



## 2) Maps ( Dictionaries )

- `key - value` pair
  - key : uniqueness
- Array 가 list-based data structure 인 것과 마찬가지로 map 은 set-based data structure



## 3) Hash

### (1) Hash Function

- `Hash function` : 특정 값을 저장하고 찾기 쉽게끔 변환하기 위해 사용
  - 이을 이용하는 자료 구조는 탐색의 시간 복잡도가 `O(1)` : **constant!**
  - 대표 패턴: 끝에서부터 일부 숫자를 취한 뒤 이를 일정한 숫자로 나눈 나머지 `Hash value` 를 index 로 이용
    - 예시 : 0123456 => 56 / 10 => array[6] = 0123456
  - `Load Factor = # of Entries / # of Buckets` : how **full** a hash table is
- **Collisions**
  - 서로 다른 자료로부터 동일한 Hash value 가 발생
  - 해결 1 : Hash function 자체를 변경하여 동일한 Hash value 발생 방지
    - 기존의 자료들을 모두 새롭게 저장해야 함
    - 더 많은 저장 공간 필요
  - 해결 2 : Hash function 을 그대로 유지하는 한편 동일한 Hash value 를 갖는 자료들의 저장 방식 을 변경 (normal array => bucket)
    - 모든 자료가 동일한 Hash value 를 갖는 list 로서 저장될 수 있음
  - 해결 3 : Hash value 를 겹쳐서 사용

### (2) Hash Maps

- key - value => key 에 hash function 적용 => Hash value 에 따라 key - value 쌍을 저장 

### (3) String Keys

- ASCII 코드를 활용해 hash function 적용 가능

