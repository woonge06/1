#김세웅 1,2주차 스터디
----------
**1주차 스터디 진행 내용** 
* 링크드리스트 :
  링크드리스트란 데이터 목록을 다루는 가장 단순한 자료구조로, 데이터가 순차적으로 연결된 선형 구조로 되어있습니다.
* 링크드리스트 구조 :
  링크드리스트는 노드로 구성되어 있는데, 노드란 데이터를 저장하는 부분과 다음 노드에 대한 포인터로 이루어져 있는 것을 뜻합니다.
  링크드리스트는 노드들이 일렬로 연결된 자료구조 형태로 되어 있습니다. 이 떄 첫 번째 노드를 헤드라고 하고, 마지막 노드를 테일이라고 합니다.
* 링크드리스트 장/단점
  * 장점 : 단순한 구조로 되어있어 구현이 쉽고 데이터의 추가, 삽입, 삭제가 쉽습니다., 현재 노드가 가지고 있는 포인터 정보를 사용하여 추가적인 연산 없이 다음 노드를 가져올 수 있습니다.
  * 단점 : 노드에는 다음 노드를 가르키는 포인터가 필요해 메모리가 추가로 필요합니다., 헤드 노드의 정보만을 가지고 있기에 다른 노드를 탐색하는데 많은 연산이 필요합니다.
* 주요 연산 구현 :
  링크드리스트를 사용하기 위해서는 5가지 기능이 구현되어야 합니다.
  * 1. 노드
       * 노드에는 노드의 데이터를 저장하는 변수, 다음 노드의 포인터를 가리키는 포인터 변수가 있습니다.
    2. 노드 추가/삽입
        * 리스트에 노드를 추가하기 위해서는 새로운 노드를 생성하고, 테일 노드의 포인터에 새로운 노드 주소를 입력해야합니다., 리스트에 노드를 삽입하기 위해서는 새로운 노드가 가리키는 포인터의 포인터를 현재 노드가 가리키는 포인터로 입력하고, 현재 노드가 가리키는 포인터를 새로운 노드의 주소값으로 
          변경해야 합니다.   
    3. 노드 탐색
       * 링크드리스트 구조에서는 헤드노드에 대한 정보만 가지고 있기 때문에 헤드노드부터 순차적으로 찾는 수 밖에 없어 리스트의 원하는 값을 찾기 위해 많은 연산이 필요하단 단점이 있습니다.
    4. 노드 삭제
       * 리스트 내의 노드를 삭제하기 위해서는 삭제 하려는 노드의 이전노드가 삭제하려는 노드의 다음노드를 가리키도록 포인터를 변경해야 하고, 삭제하려는 노드의 메모리를 해제 하여야 합니다.
    5. 노드 개수 세기
       * 링크드리스트 구조에서는 헤드노드에 대한 정보만 가지고 있어 리스트에 몇 개의 노드가 있는지에 대한 정보는 없습니다 따라서 반복문 등을 활용하여 노드의 개수를 셀 수 있습니다.
-------------
* Doubly 링크드리스트 : 
  Doubly 링크드리스트란 각 노드가 단방향에 대한 정보를 가지고 있는 것이 아닌 양방향에 대한 정보를 가지고 있는 링크드리스트로, 다음 노드의 포인터뿐만이 아닌 이전 노드의 포인터 정보도 가지고 있기 때문에 현재 노드에서 앞/뒤 양 쪽 방향의 노드에 대한 정보를 알 수 있다는 장점이 있습니다.
* 주요 연산 구현 :
  Doubly 링크드리스트에서는 다음노드의 포인터 뿐만아니라 이전 노드의 포인터도 가지고 있어야 하기 때문에 노드구조체에 이전 노드의 포인터를 가리키는 변수를 추가하여야합니다. 또한
  삽입, 삭제 연산을 할 때에도 새로운 노드에 현재 노드가 가리키는 노드의 주소값을 추가하고, 현재 노드의 포인터에 새로운 노드의 주소값을 추가하고, 새로운 노드와 그 다음 노드에 이전 노드에 대한 포인터 정보를 추가 하여야합니다.
---------------
* Circular 링크드리스트 :
  Circular 링크드리스트란 Doubly 링크드리스트에서 헤드와 테일을 연결한 구조로, 머리와 꼬리를 연결하여 원형으로 만든 링크드리스트입니다.
* 주요 연산 구현
  Circular 링크드리스트를 구현하기 위해서는 헤드 노드와 테일 노드를 연결시켜야합니다. 따라서 테일 노드는 NULL포인터가 아닌 헤드노드를 다시 찾는 순간으로 바꾸고 새로운 테일 노드의 이전 노드 포인터와 다음 노드 포인터(헤드)를 업데이트 해주고 헤드 노드에 이전 노드 포인터를 업데이트 해주어야합니다.
---------------
* 코드
```ruby
#include <iostream>
using namespace std;
//노드 struct 구현
struct NODE 
{
	int nData;
	NODE* nextNode;
};
//링크드리스트 클래스 생성
class LinkedList 
{
private:
	NODE* head;
	NODE* tail;
public:
	LinkedList() 
	{
		//헤드와 테일의 포인터를 초기화
		head = NULL;
		tail = NULL;
	}
	//첫 번째(헤드) 노드 추가
	void addFrontName(int n);
	//마지막(테일) 노드 추가
	void addNode(int n);
	//노드 삽입
	void insertNode(NODE* prevNode, int n);
	//노드 삭제
	void deleteNode(NODE* prevNode);
	//첫 번쨰 노드 가져오기
	NODE* getHead() 
	{
		return head;
	}
	//LinkedList 출력
	void display(NODE* head);
};
//첫 번쨰 노드 추가
void LinkedList::addFrontName(int n)
{
	NODE* temp = new NODE;
	//temp의 데이터는 n
	temp->nData = n;
	//LinkedList가 비어있으면
	if (head == NULL)
	{
		//첫 NODE는 temp
		head = temp;
		//마지막 NODE는 temp
		tail = temp;
	}
	//LinkedList에 데이터가 있으면
	else
	{
		//temp의 nextNode는 head
		temp->nextNode = head;
		//head는 temp
		head = temp;
	}
}
//마지막에 노드 추가
void LinkedList::addNode(int n)
{
	NODE* temp = new NODE;
	//temp의 데이터는 n
	temp->nData = n;
	//temp의 nextNode = Null
	temp->nextNode = NULL;
	//LinkedList가 비어있으면
	if (head == NULL)
	{
		//첫 노드는 temp
		head = temp;
		//마지막 노드는 temp
		tail = temp;
	}
	//LinkedList에 데이터가 있으면
	else
	{
		//현재 마지막 노드의 nextNode는 temp
		tail->nextNode = temp;
		//마지막 노드는 temp
		tail = temp;
	}
}
//노드 삽입
void LinkedList::insertNode(NODE* prevNode, int n)
{
	NODE* temp = new NODE;
	//temp의 데이터는 n
	temp->nData = n;
	//temp의 nextNode 저장(삽입 할 앞 node의 nextNode를 temp의 nextNode에 저장)
	temp->nextNode = prevNode->nextNode;
	//temp 삽입
	//temp앞의 NODE의 nextNode를 temp로 저장
	prevNode->nextNode = temp;
}
//노드 삭제
void LinkedList::deleteNode(NODE* prevNode)
{
	//삭제할 노드를 temp에 저장(삭제할 노드의 1단계 전 노드의 nextNode)
	NODE* temp = prevNode->nextNode;
	//삭제할 노드를 제외(삭제할 노드의 nextNode를 1단계 전 노드의 nextNode에 저장)
	prevNode->nextNode = temp->nextNode;
	//temp 삭제
	delete temp;
}
//LinkedList 출력
void LinkedList::display(NODE* head)
{
	if (head == NULL)
	{
		cout << "\n";
	}
	else
	{
		cout << head->nData << endl;
		display(head->nextNode);
	}
	cout << endl;
}
//메인 함수
int main()
{
	LinkedList a;
	//1추가
	a.addNode(1);
	//2추가
	a.addNode(2);
	//3추가
	a.addNode(3);
	//display
	cout << "1,2,3을 LinkedList에 추가\n";
	a.display(a.getHead());
	//0을 제일 앞에 추가
	a.addFrontName(0);
	//1을 네번째에 추가
	a.insertNode(a.getHead()->nextNode->nextNode, 1);
	cout << "0을 첫번째에 추가, 1을 네번째에 추가\n";
	a.display(a.getHead());
	//세번째 노드 삭제
	a.deleteNode(a.getHead()->nextNode);
	//display
	cout << "세번째 노드를 삭제\n";
	a.display(a.getHead());
}
```
* 출력
![image](https://github.com/user-attachments/assets/2da3df6b-e528-4f65-ae02-85c1a398b484)
--------------
* 트리 : 
  트리란 노드와 노드 사이를 연결하는 edge를 이용하여 계층을 구성하는 대표적인 비선형 자료구조입니다.
* 구성 요소 :
  * 노드 node: 데이터가 저장된 부분
  * 엣지 edge : 노드와 노드를 연결하는 선
  * 루트(root) 노드 : 최상단에 위치한 노드로 부모 노드가 없는 노드
  * 리프(leaf) 노드 : 최하단에 위치한 노드로 자식 노드가 없는 노드
  * 비단말(internal) 노드 : 자식 노드가 있는 노드
  * 형제(sibling) 노드 : 같은 부모를 가지는 노드들
* 특징 용어
  * 높이(height) : 자신 -> 리프노드까지의 최대 엣지 수 - 트리의 높이 = 루트노드의 높이
  * 깊이(depth) : 루트 노드 -> 자신까지의 최대 엣지 수
  * 레벨(Level) : 루트 노드 -> 자신까지의 최대 엣지 수 +1
  * degree : 노드의 자식 수 (서브트리의 수)
* 트리의 종류
  * 이진 트리(Binary tree) : 각 노드당 자식 노드의 개수가 최대 2개로 제한된 트리
  * 편향 이진 트리(Skewed Binary tree) : 높이에 대한 최소 노드를 가지면서 한쪽 방향의 자식노드만 가지는 트리
  * 이진 탐색 트리(Binary Search tree) : 각 노드의 왼쪽 서브트리는 현재 노드의 데이터보다 작은 값이, 오른쪽 서브트리는 현재 노드의 데이터보다 큰 값이 저장되는 이진 트리
  * 전 이진트리(Full Binary tree) : 모든 노드의 자식 노드 수가 2개 혹은 0개인 이진 트리
  * 포화 이진트리(Perfect Binary tree) : 모든 리프 노드의 깊이(depth)가 동일한 전 이진트리
  * 완전 이진트리(Complete Binary tree) : 리프 노드를 제외한 트리 부분은 포화 이진트리 이면서, 리프노드들이 왼쪽에서부터 차례로 저장되어 있는 이진 트리
  * 등등 다양한 트리들이 있습니다.
* 트리 탐색 법 :
  * 트리 중에서 대표적인 이진 트리를 탐색하는 방법에는 크게 4가지가 있습니다.
    * 전위순회(Preorder Traversal) : 전위순회는 루트 노드를 먼저 탐색하고 자식 노드를 탐색하는 방식입니다.
    * 중위순회(inorder traversal) : 중위순회는 왼쪽 자식 노드를 탐색하고, 루트 노드를 탐색하고, 오른쪽 자식 노드를 탐색하는 방식입니다.
    * 후위순회(postorder traversal) : 후위순회는 왼쪽 자식 노드를 탐색하고, 오른쪽 자식 노드를 탐색하고, 루트 노드를 탐색하는 방식입니다.
    * 레벨순회(levelorder traversal) : 레벨순회는 루트 노드를 먼저 탐색하고, 그 다음 레벨의 노드를 탐색하는 방식입니다.
-------------------
* 코드
코드는 이진 트리를 만들고, 이진 트리를 순회하는 코드입니다.
```ruby
#include <iostream>
using namespace std;
//노드 정의
struct NODE
{
	int nData;
	struct NODE* r_child; //오른쪽 자식 노드 정의
	struct NODE* l_child; //왼쪽 자식 노드 정의
};
//새 노드의 기능 만들기
struct NODE* new_node(int nData)
{
	struct NODE* node_ptr;
	node_ptr = new NODE();
	node_ptr->nData = nData;
	node_ptr->l_child = NULL; //왼쪽 자식 노드 초기화
	node_ptr->r_child = NULL; //오른쪽 자식 노드 초기화
	return node_ptr;
}
//전위순회 함수
void preorder(struct NODE* root)
{
	if (root) //노드가 존재한다면
	{
		cout << root->nData << " "; //현재 노드값 출력
		preorder(root->l_child); //왼쪽 자식 노드 호출
		preorder(root->r_child); //오른쪽 자식 노드 호출
	}
}
//중위순회 함수
void inorder(struct NODE* root)
{
	if (root) //노드가 존재한다면
	{
		inorder(root->l_child); //왼쪽 자식 노드 호출
		cout << root->nData << " "; //현재 노드값 출력
		inorder(root->r_child); //오른쪽 자식 노드 호출
	}
}
//후위순회 함수
void postorder(struct NODE* root)
{
	if (root) //노드가 존재한다면
	{
		postorder(root->l_child); //왼쪽 자식 노드 호출
		postorder(root->r_child); //오른쪽 자식 노드 호출
		cout << root->nData << " "; //현재 노드값 출력
	}
}
//리프 기능 확인
bool is_Leaf(struct NODE* n) {
	if (n == NULL)
	{
		return false; //n이 null이라면 false
	}
	if (n->l_child == 0 && n->r_child == 0)
	{
		return true; //만약 노드에 자식 노드가 없다면 리프 노드
	}
	return false; //자식 노드가 하나라도 있으면 false
}
//최대 함수 가져오기
int get_Max(int a, int b)
{
	return a > b ? a : b; //최댓값 비교
}
//깊이 함수 가져오기
int get_Depth(struct NODE* n)
{
	if (is_Leaf(n) || n == NULL) //만약 n이 리프 노드이거나 NULL이라면 true
	{
		return 0;
	}
	else
	{
		if (n == NULL) return 0; // NULL이면 깊이는 0
		if (is_Leaf(n)) return 1; // 리프 노드는 깊이 1
		// 왼쪽과 오른쪽 서브트리의 깊이를 비교하여 최댓값에 +1
		return get_Max(get_Depth(n->l_child), get_Depth(n->r_child)) + 1;
	}
}
int main()
{
	struct NODE* root; //트리의 루트 노드를 가리키는 포인터 root 선언
	//트리 구현
	root = new_node(4);
	root->r_child = new_node(5);
	root->r_child->r_child = new_node(6);
	root->l_child = new_node(2);
	root->l_child->l_child = new_node(1);
	root->l_child->r_child = new_node(3);
	//루트 노드 4, 4의 자식 노드 5, 5의 자식 노드 6, 4의 자식 노드 2, 2의 자식 노드 1, 2의 자식 노드 3
	cout << "전위순회 : "; //전위순회 출력
	preorder(root); //전위순회
	cout << endl;
	cout << "중위순회 : "; //중위순회 출력
	inorder(root); //중위순회
	cout << endl;
	cout << "후위순회 : "; //후위순회 출력
	postorder(root); //후위순회
	cout << endl;
	cout << "깊이(Depth) : " << get_Depth(root) << endl; //깊이 출력
	cout << "레벨(Level) : " << get_Depth(root) + 1; //깊이 +1 한 뒤 출력(레벨)
}
```
* 출력
![image](https://github.com/user-attachments/assets/e96d985a-5113-4ee6-8d0e-0b1ce8863b4b)
