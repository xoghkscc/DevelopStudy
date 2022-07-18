# DevelopStudy
## 0. 소개
* 자료구조, 알고리즘 등을 공부한 내용을 정리한 ReadMe입니다.
* 제가 배운 모든 내용을 필기해 놓은 파일은 word 파일로 정리하였습니다.
## 1. 자료구조

### 자료구조란?
* 대량의 데이터를 효율적으로 관리할 수 있는 데이터의 구조를 의미
* 코드상에서 효율적으로 데이터를 처리하기 위해, 데이터 특성에 따라 체계적으로 데이터를 구조화해야 함
* 어떤 게이터 구조를 사용하느냐에 따라 코드 호율이 달라짐

### 대표적인 자료구조
* 배열, 스택, 큐, 링크드 리스트, 해쉬 테이블, 힙 등

## 2. 배열
* 데이터를 나열하고, 각 데이터를 인덱스에 대응하도록 구성한 데이터 구조
### 배열의 장점
* 빠른 접근 가능
* 첫 데이터의 위치에서 상대적인 위치로 데이터 접근(인덱스 번호로 접근)
### 배열의 단점
* 데이터의 추가/삭제가 어려움
* 미리 최대 길이를 지정해야함 --> 비가변적

![image](https://user-images.githubusercontent.com/82793713/179519613-90c098fb-bfe7-4dc7-a780-34b2df2cb664.png)

## 3. 큐
### 큐 구조
* 가장 먼저 넣는 데이터를 가장 먼저 꺼낼 수 있는 구조
* FIFO(First-In, First-Out) 또는 LILI(Last-In, Last-Out) 방식으로 스택과 꺼내는 순서가 반대
### 알아둘 용어
* Enqueue: 큐에 데이터를 넣는 기능
* Dequeue: 큐에서 데이터를 꺼내는 기능

![image](https://user-images.githubusercontent.com/82793713/179519898-3610f5c7-9e7e-4d2d-8bae-c381c41d4b90.png)

## 4. 스택
### 스택 구조
* 데이터를 제한적으로 접근할 수 있는 구조
* 한쪽 끝에서만 자료를 넣거나 뺄 수 있는 구조
* 가장 나중에 쌓은 데이터를 가장 먼저 빼낼 수 있는 데이터 구조
    * 큐: FIFO 정책
    * 스택: LIFO 정책
 ### 대표적인 스택의 활용
 *  컴퓨터 내부의 프로세스 구조의 함수 동작 방식
 ### 주요 기능
 *  push(): 데이터를 스택에 넣기
 *  pop(): 데이터를 스택에서 꺼내기

![image](https://user-images.githubusercontent.com/82793713/179520326-fdecaba3-da38-4519-8fca-a0ccc0397e55.png)

### 스택의 장점
* 구조가 단순해서 구현이 쉽다
* 데이터 저장/읽기 속도가 빠르다
### 스택의 단점
* 데이터 최대 개수를 미리 정해야 한다.(파이썬에 경우 재귀 함수는 1000번까지만 호출이 가능함)
* 저장 공간의 낭비가 발생할 수 있음

![image](https://user-images.githubusercontent.com/82793713/179520538-adf71824-28f8-4a23-b1f9-561d63fe5b88.png)

```C
이때 stack_list[-1]은 맨 끝에 있는 값을 가지고 오는 거임(파이썬)
```

## 5. 링크드 리스트(Linked List)
### 링크드 리스트 구조
*  떨어진 곳에 존재하는 데이터를 화살표로 연결해서 관리하는 데이터 구조
*  배열과 달리 미리 데이터를 예약하지 않고 필요할 때마다 추가 가능
### 링크드 리스트 기본 구조와 용어
*  노드(Node): 데이터 저장 단위(데이터값, 포인터)로 구성
*  포인터(Pointer): 각 노드 안에서 다음이나 이전의 노드와의 연결 정보를 가지고 있는 공간

![image](https://user-images.githubusercontent.com/82793713/179521183-e38acb43-7b71-47ce-a34e-5dfbfbabc819.png)
![image](https://user-images.githubusercontent.com/82793713/179521188-3a8735f3-405c-4851-b944-2658fbd6801c.png)

### 파이썬으로 링크드 리스트 구현해괴

```C
calss Node:
   def __init__(self, data, next=None):
      self.data = data
      self.next = next

class NodeMgmt:
   def __init__(self, data): //생성자
      self.head = Node(data) //생성자의 입력된 데이터가 링크드리스트의 헤드가 되는 거임
   
   def add(self, data): //링크드 리스트의 데이터 추가 메서드
      node = self.head  //head를 설정
      whiel node.next:  
         node = node.next  //반복문을 탈출한 Node는 마지막 노드
      node.next = Node(data)  //마지막 노드의 포인터에 추가하고자 하는 데이터 입력
   
   def delete(self, data): //링크드 리스트의 데이터 삭제 메서드
      if self.head.data == data:    //만약 삭제하려는 데이터가 head라면
         temp = self.head  //해드를 임시로 두고
         self.head = temp.next   //헤드가 삭제되어야 하므로 헤드는 삭제되어야 할 헤드의 다음 노드
         del temp //헤드 삭제
      else:    //만약 삭제하려는 데이터가 head가 아니라면
         node = self.head
         while node.next:
            if node.next.data == data: //삭제하려는 데이터를 찾은 경우
               temp = node.next     
               node.next = temp.next   //지우고자 하는 노드(A)의 next를 A의 앞 노드 next에 달아주는 당식
               del temp  //노드 삭제
            else:
               node = node.nexgt //삭제하고자 하는 노드가 아니라면 다음 노드로 이동
               
   def get(self, data):    //원하는 데이터가 들어있는 노드의 주소값 찾기
      node = self.head
      while node.next:
         if node.data == data:
            return node
         else:
            node = node.next
```



