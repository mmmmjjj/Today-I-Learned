# 서로소 집합 (Disjoint-Set)

- 서로소 ( 상호배타) 집합 (Disjoint-set)
- 서로 중복 포함된 원소가 없는 집합들. **교집합이 없는 집합들**
- 집합에 속한 하나의 특정 멤버를 통해 각 집합들을 구분한다. = 대표자
- 서로소 집합을 표현 하는 방법
    - 연결 리스트
    - 트리

<img width="1125" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-10-03%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2010 29 26" src="https://user-images.githubusercontent.com/67090601/135815734-0287adda-9cd5-40f9-afda-e3b1af04b4b7.png">

- 서로소 집합 연산
    - Make-Set(x)
        - 가장 작은 단위의 단위 집합을 만드는 연산
        - 원소 모두 각각 개별의 집합을 만들고 시작한다.
    - Find-Set(x)
        - 대표자를 찾는 연산
    - Union(x,y)
        - x가 속한 집합과 y가 속한 집합을 합치는 연산
- 연산의 효율을 높이는 방법
    - Rank를 이용한 Union
        ![Untitled](https://user-images.githubusercontent.com/67090601/135815904-b4dea6f2-2a6b-4c5b-8ace-8364c9576ac6.png)
      
        - 각 노드를 자신을 루트로 하는 subtree위 높이를 랭크라는 이름으로 저장.
        - 두 집합을 합칠 때 rank가 낮은 집합을 rank가 높은 집합에 붙인다.
    - Path compression
        ![Untitled-2](https://user-images.githubusercontent.com/67090601/135815977-064399fa-ba91-49f8-8548-33ad29f02208.png)

     ![Untitled-3](https://user-images.githubusercontent.com/67090601/135816001-6221b44f-7b8e-4344-89dd-661cfa81740f.png)

        - find-set을 행하는 과정에서 만나는 모든 노드들이 직접 root를 가리키도록 
        포인터를 바꾸어 준다. (오른쪽 처럼 바꾼다)
        - find-set을 행할 때 일어나기 때문에 find-set을 하지 않으면 저렇게 바뀌지 않는다.

 Union-Find 알고리즘 이라고 한다.
 
<img width="1125" alt="스크린샷 2021-10-03 오후 10 29 26" src="https://user-images.githubusercontent.com/67090601/135816223-433f05df-ad34-4fa6-83f3-22f78c2f03b0.png">


### 서로소 집합 (연결리스트)

- 같은 집합의 원소들은 하나의 연결리스트로 관리
- 연결리스트의 **맨 앞의 원소를 집합의 대표 원소**로 삼는다.
- 각 원소는 집합의 대표원소를 가리키는 링크를 갖는다.
- union(e,f) = e가 속한 집합에 f가 속한 집합이 흡수된다!

![Untitled-4](https://user-images.githubusercontent.com/67090601/135816454-620451dd-21c3-40d3-83ea-69fdfecce922.png)


### 서로소 집합 (트리)

- 하나의 집합을 하나의 트리로 표현한다.
- 자식 노드가 부모 노드를 가리키며 루트 노드가 대표자가 된다.
![Untitled-5](https://user-images.githubusercontent.com/67090601/135816484-b1533574-f258-47af-84ff-d6d825242e31.png)
![Untitled-6](https://user-images.githubusercontent.com/67090601/135816497-dbafe9d0-c9f3-4732-8a5e-e4bb425e2e0a.png)


연결리스트를 구현하는것은 번거롭기 때문에 자신의 집합에 속해있는 부모의 관계를 이용해 배열로 만든다.

부모를 가리키는 집합이기 때문에 보통 parents라고 명명한다.

## UnionFind 알고리즘

- 처음에 make-set으로 자신이 곧 대표자가 되도록 만들어준다.

- 연산의 효율을 높이는 방법
    - Rank을 이용한 Union
        - 각 노드는 자신을 루트로 하는 subtree의 높이를 랭크라는 이름으로 저장한다.
        - 두 집합을 합칠 때 랭크가 낮은 집합을 높은 집합에 붙인다.
    - Path compression
        - Find-set을 행하는 과정에서 만나는 모든 노드들이 직접 root를 가리키도록 포인터를 바꾼다.
        <img width="721" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-10-03%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2011 13 14" src="https://user-images.githubusercontent.com/67090601/135816522-37d24168-b5fc-4c62-8037-6c417e9323da.png">
    
