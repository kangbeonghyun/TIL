# Disjoint Set(서로소 집합)

### Concept

* 서로 중복되지 않는 부분 집합들로 나눠진 원소들에 대한 정보를 저장하고 조작하는 자료구조.
* 겹치지 않게 분할하는 용도로 자주 쓰임.

* Mutually disjoint: 집합 A와B가 공유되는 원소가 하나도 없을 때의 관계
* 분할(Partition)한다-1) 분할된 부분집합을 합치면 원래의 셋(S)이 된다.

​                                         2) 분할된 부분집합은 mutually disjoint이다.

* 트리 구조 이용(배열).

### Operation

* make-set(x): x를 유일한 원소로 하는 새로운 셋을 만듬(초기화)

* union(x,y): x가 속한 집합과 y가 속한 집합을 합침(루트끼리 합침)
                      - union-by-size(원소수가 적은 셋을 많은 셋의 서브트리로)
                      - union-by-height(트리 높이자 작은 셋을 큰 셋의 서브트리로)
* find(x): x가 속한 셋의 대표값(루트)를 반환

### Path compression

* 모든 노드가 루트를 가리키도록 만드는 것(find 연산 수행시 루트노드까지 올라가야 하는 비효율성 완화를 위함)(O(logN))

#### REFERENCE

 https://gmlwjd9405.github.io/2018/08/31/algorithm-union-find.html