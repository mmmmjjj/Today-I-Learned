# 스택

- 물건을 쌓아 올리듯 자료를 쌓아 올린 형태의 자료구조.

- 선형구조를 갖는다. (자료 간의 관계가 1대1)
- 후입선출 (LIFO)

<img src="https://user-images.githubusercontent.com/67090601/135212986-a52922ae-f268-483e-bda8-f87b3f13a150.png" width="70%">

### java.util.Stack

- 주요 메소드
    - push()
    - pop()
    - isEmpty()
    - size()


### 스택 응용 - 계산기

- 문자열 수식 계산의 일반적 방법
    
    1) 중위 표기법을 후위 표기법으로 변경
    
    - 우선순위에 따라 괄호를 사용하여 표현한다.
    - 연산자를 그에 대응하는 오른쪽 괄호 뒤로 이동시킨다.
    - 괄호를 제거한다.
    
    <img src="https://user-images.githubusercontent.com/67090601/135213052-803df5d3-1fa9-4a31-b427-afdfb00ff3c9.png" width="70%">
    
    2) 후위 표기법의 수식을 스택을 이용하여 계산한다.
    
    - 피연산자를 만나면 push
    - 연산자를 만나면 필요한 만큼의 피연산자를 pop하여 연산하고, 연산결과를 다시 push
    - 수식이 끝나면 마지막으로 pop
    
    <img src="https://user-images.githubusercontent.com/67090601/135213069-222c2401-d020-4951-825d-58d09051d255.png" width="70%">

# 큐

- 스택과 마찬가지로 삽입과 삭제의 위치가 제한적인 자료구조

- 큐의 뒤에서는 삽입만 하고, 큐의 앞에서는 삭제만 이루어지는 구조.
- 선입선출 (FIFO)
- BFS에서 활용
- 주요 메소드
    - offer() : 삽입
    - poll() : 삭제  `* null일 경우 예외 처리 하지 않는다. null일 때 예외처리 하고 싶다면 remove 사용해라!`
    - isEmpty()
    - size()
  
<img src="https://user-images.githubusercontent.com/67090601/135213082-ae79bb93-8749-4ae3-8c7f-5df46b51d5e5.png" width="80%">

- 삽입 : enQueue
- 삭제 : deQueue

||공백 큐 생성 | enQueue 원소 삽입 | deQueue 원소 삭제
---|--- | ---| ---
front|-1|그대로| +=1
rear|-1|+=1|그대로


> front = rear : 큐에 있는 모든 데이터가 꺼내진 상태

### java.util.Queue

- 큐에 필요한 연산을 선언해놓은 인터페이스
- `LinkedList 클래스를 Queue 인터페이스의 구현체로 많이 사용`

### 큐 응용 - 버퍼

- 데이터를 한 곳에서 다른 한 곳으로 전송하는 동안 일시적으로 그 데이터를 보관하는 메모리의 영역
- 순서대로 입출력/전달되어야 하므로  FIFO 자료구조인 큐가 활용된다.

## 우선순위 큐 (Priority Queue)

- 우선순위를 가진 항목들을 저장하는 큐

- 선입선출 순서가 아니라 우선순위가 높은 순서대로 먼저 나가게 된다.

### java.util.PriorityQueue

- Heap 자료구조

- 최대 Heap
    - 가장 큰 값을 기준으로 먼저 나옴
- 최소 Heap
    - 가장 작은 값을 기준으로 먼저 나옴
