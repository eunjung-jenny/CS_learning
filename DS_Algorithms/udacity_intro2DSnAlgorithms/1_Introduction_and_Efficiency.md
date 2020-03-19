# 1. Introduction and Efficiency

`Efficiency (=Complexity) : 시간, 공간의 관점에서 자원을 얼마나 잘 사용할 수 있을 것인가`

## 1) Efficiency 란?

- 시간, 공간의 관점에서 자원을 얼마나 잘 사용할 수 있을 것인가.
  - 일반적으로 시간과 공간은 **trade-off** 관계에 있음.

## 2) 빅O 표기법 

- 일반적으로 efficiency 는 O(n), O(n^2), O(1) 등과 같이 표기하게 됨.
- `n` 은 함수에 전달되는 인자의 길이를 의미함.
- 괄호 안에 길이가 n 인 인자가 함수에 전달되었을 때, 몇 번의 연산이 실행되는가/얼마만큼의 메모리를 사용하는가를 작성하게 되는데, 근사를 활용해 가장 높은 차수의 항만 남기면 됨.
- 빅O 표기법으로 efficiency 를 논할 때에는 best case, average case, worst case 중 어떠한 경우를 전제하고 있는지를 밝혀야 함.
  - worst case scenario 는 시간/공간 차원에서 upper bound 가 되므로 조금 더 주목하여 다루는 경향이 있음.

```python
"""input manatees: a list of "manatees", where one manatee is represented by a dictionary
a single manatee has properties like "name", "age", et cetera
n = the number of elements in "manatees"
m = the number of properties per "manatee" (i.e. the number of keys in a manatee dictionary)"""

# O(n)
def example1(manatees):
    for manatee in manatees:
        print manatee['name']

# O(1)
def example2(manatees):
    print manatees[0]['name']
    print manatees[0]['age']

# O(n*m)
def example3(manatees):
    for manatee in manatees:
        for manatee_property in manatee:
            print manatee_property, ": ", manatee[manatee_property]

# O(n^2)
def example4(manatees):
    oldest_manatee = "No manatees here!"
    for manatee1 in manatees:
        for manatee2 in manatees:
            if manatee1['age'] < manatee2['age']:
                oldest_manatee = manatee2['name']
            else:
                oldest_manatee = manatee1['name']
    print oldest_manatee
```



