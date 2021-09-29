# 리스트

- 순서를 가진 데이터의 집합을 가리키는 추상자료형

- 동일한 데이터를 가지고 있어도 상관없다.
- 종류
    - 순차 리스트 : 배열을 기반으로 구현된 리스트
    - 연결 리스트 : 메모리의 동적할당을 기반으로 구현된 리스트

## 순차 리스트

- 1차원 배열에 항목들을 순서대로 저장한다.

- 데이터의 종류와 구조에 따라 구조화된 자료구조를 만들어 배열에 저장 할 수도 있다.
- 배열의 인덱스를 이용해 원하는 위치에 접근할 수 있다.

> 순차리스트의 문제점
>- 자료의 삽입/삭제 연산 과정에서 원소들을 이동시키는 작업이 필요하다.
>
>- 원소의 개수가 많고 삽입/삭제 연산이 빈번할수록 시간이 크게 증가한다.
>- 배열의 크기가 정해져 있으므로, 메모리의 낭비를 초래할 수도 있고,
>할당 메모리보다 많은 자료를 사용하여 새로운 배열을 만들 수 도 있다.

## 연결 리스트

- 자료의 논리적인 순서와 메모리 상의 물리적인 순서가 일치하지 않고, 개별적으로 위치하고 있는 각 원소를 연결하여 하나의 전체적인 자료구조를 이룬다.

- `링크` 를 통해 원소에 접근하므로, 물리적인 순서를 맞추기 위한 작업이 필요하지 않다.<br>
`한 원소가 삭제되면 원래 있던 링크들을 연결시켜 주고, 삽입되면 링크를 추가한다.`
- 자료구조의 크기를 동적으로 조정할 수 있어, 메모리의 효율적인 사용이 가능하다.


### 연결리스트의 기본 구조

![image](https://user-images.githubusercontent.com/67090601/135269800-9a88dc5a-b4db-4b5b-89e5-9053ba07c0e0.png)

- **노드**
    
    연결리스트에서 하나의 원소를 표현하는 building block
    
    - 구성 요소
        
        - **데이터 필드**
        
          - 원소의 값을 저장.
        
          - 저장할 원소의 종류, 크기에 따라 구조를 정의해서 사용함.
        
        - **링크 필드** 

          - 다음 노드의 참조값 

- **헤드**

    - 연결 리스트의 첫 노드에 대한 참조값을 갖고 있음

>헤드를 가지고 있으면 리스트 전체를 순회할 수 있다!
><br>헤드 = 첫번째 노드에 대한 포인터

### 연결리스트의 종류

- **단순 연결 리스트 (혼자 구현 할 줄 알아야 한다)**
    - 링크를 1개만 유지하는 리스트
    - 링크가 1개라면 어떤 노드를 삭제할 때, 이전 노드를 일일이 찾아야 하는 단점이 있다.
- **이중 연결 리스트**
    - 링크를 2개만 유지하는 리스트
    - 한 노드에서 이전 노드, 다음 노드의 정보가 있기 때문에 이전노드에 대한 탐색이 필요없다.
    - but, 관리는 더 힘들어진다.
- **원형 연결 리스트**
    
    - 리스트의 끝과 처음을 연결하는 리스트

>연결리스트에서 가장 중요한 것 : 링크 관리

## 단순 연결 리스트

- **연결 구조**
    - 노드가 하나의 링크 필드에 의해 다음 노드와 연결되는 구조
    - 링크 필드가 Null인 노드 = 마지막 노드

![image](https://user-images.githubusercontent.com/67090601/135269925-caf11800-4a7b-4ffc-8084-39f1499876c0.png)

- 링크 필드의 타입은 참조하는 객체의 데이터형으로 만들면 된다! + 헤드도
    

### 단순 연결 리스트 구현하기
```java
public class SignglyLinkedList {

	private Node head;

	// 첫번째 노드에 삽입하기
	// 기존 노드의 링크에 헤드의 노드를 삽입하고 헤드를 새로운 노드로 갱신한다.
	public void addFirstNode(String data) {
		Node newNode = new Node(data, head);
		head = newNode;
	}

	// 마지막 노드 찾기
	public Node getLastNode() {

		for (Node curNode = head; curNode != null; curNode = curNode.link) {
			if (curNode.link == null) { return curNode; }
		}
		return null;
	}

	// 마지막 노드에 삽입하기
	public void addLastNode(String data) {

		if (head == null) { // 공백리스트라면
			addFirstNode(data);
			return;
		}

		Node newNode = new Node(data);
		Node lastNode = getLastNode();
		lastNode.link = newNode;
	}

	// 기준 노드 뒤에 삽입하기
	public void insertAfterNode(Node preNode, String data) {

		if (preNode == null) {
			System.out.println("선행노드가 없어 삽입이 불가능합니다.");
			return;
		}

		Node newNode = new Node(data, preNode.link);
		preNode.link = newNode;

	}

	// data를 데이터로 갖고있는 노드 리턴
	public Node getNode(String data) {

		for (Node curNode = head; curNode != null; curNode = curNode.link) {
			if (curNode.data.equals(data)) { return curNode; }
		}

		return null;
	}

	// target의 이전노드 찾기
	public Node getPreviousNode(Node target) {

		for (Node curNode = head; curNode != null; curNode = curNode.link) {
			if (curNode.link == target) { return curNode; }
		}

		return null;
	}

	// data를 갖고 있는 노드 찾아 삭제
	public void deleteNode(String data) {

		Node targetNode = getNode(data);
		if (targetNode == null) {
			System.out.println("삭제할 노드가 없어서 삭제가 불가능합니다.");
			return;
		}

		Node preNode = getPreviousNode(targetNode);

		if (preNode == null) { // target이 헤드인 상황
			head = targetNode.link;
		} else {
			preNode.link = targetNode.link;

		}
		targetNode.link = null;
	}

	public void printList() {

		System.out.printf("L = ( ");
		for (Node currNode = head; currNode != null; currNode = currNode.link) {
			System.out.print(currNode.data + "  ");
		}
		System.out.println(" ) ");
	}

}
```


## 이중 연결 리스트

- 특성
    - 양쪽 방향으로 순회 할 수 있도록 노드를 연결한 리스트
    - 두개의 링크 필드, 한 개의 데이터 필드
   
![image](https://user-images.githubusercontent.com/67090601/135269983-aa92a690-5349-43a0-93b4-96fc1bb57775.png)
