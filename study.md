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
```ruby
#include <iostream>
using namespace std;
struct NODE
{
	int nData;
	NODE *nextNode;
};
class LinkedList
{
private:
	NODE *head = new NODE;
	NODE *tail = new NODE;
public:
	LinkedList()
	{
		head -> nextNode = tail;
		tail -> nextNode = NULL;
	}
	//맨 앞에 노드 추가
	void AddFront( int nData )
	{
		NODE *newNode = new NODE;
		newNode -> nData = nData;
		//노드가 한개도 없는 경우
		if ( head->nextNode == tail )
		{
			head -> nextNode = newNode;
			newNode -> nextNode = tail;
		}
		//노드가 한개 이상인 경우
		else
		{
			newNode -> nextNode = head -> nextNode;
			head -> nextNode = newNode;
		}
	}
	//맨 뒤에 노드 추가
	void PushBack( int nData )
	{
		//노드가 한개도 없는 경우
		if ( head->nextNode == NULL )
		{
			AddFront( nData );
		}
		//노드가 한개 이상인 경우
		else
		{
			//새로운 노드 생성
			NODE *newNode = new NODE;
			newNode -> nData = nData;
			//마지막 노드 찾기
			NODE *curNode = head -> nextNode;
			while ( curNode -> nextNode != tail )
			{
				curNode = curNode -> nextNode;
			}
			//tail 노드 앞에 삽입
			curNode -> nextNode = newNode;
			newNode -> nextNode = tail;
		}
	}
	//지정된 노드 뒤에 새 노드를 삽입
	void InsertNode(NODE *prevNode, int nData)
	{
		if ( prevNode == nullptr )
		{
			cout << "올바른 노드주소가 아닙니다. 데이터를 삽입할 수 없습니다.\n";
			return;
		}
		NODE *newNode = new NODE;
		newNode -> nData = nData;
		//prevNode가 맨 마지막에 있는 노드인 경우
		if ( prevNode->nextNode == tail )
		{
			prevNode -> nextNode = newNode;
			newNode -> nextNode = tail;
			return;
		}
		//prevNode가 맨 마지막 노드가 아닌 경우
		newNode -> nextNode = prevNode -> nextNode;
		prevNode -> nextNode = newNode;
	}
	//특정 데이터를 가진 노드 삭제
	void DeleteNode( int nData )
	{
		NODE *targetNode = nullptr;
		//빈 리스트인 경우
		if ( head -> nextNode == tail )
		{
			cout << "빈 리스트 입니다." << endl;
			return;
		}
		//첫번쨰 노드가 지우려는 노드일 때
		if ( head -> nextNode -> nData == nData )
		{
			targetNode = head -> nextNode;
			head -> nextNode = targetNode -> nextNode;
			targetNode = nullptr;
			delete targetNode;
			return;
		}
		//지우려는 데이터의 이전 노드 찾기
		NODE *prevNode = head -> nextNode;
		while ( prevNode -> nextNode != tail )
		{
			if ( prevNode -> nextNode -> nData == nData )
			{
				targetNode = prevNode -> nextNode;
				break;
			}
			prevNode = prevNode -> nextNode;
		}
		//지우려는 노드를 못찾은 경우
		if ( prevNode -> nextNode == tail )
		{
			cout << "해당 데이터는 존재하지 않습니다.\n";
			targetNode = nullptr;
			return;
		}
		//지우려는 노드를 찾은 경우
		if ( targetNode -> nextNode == tail ) //현재 노드가 마지막 노드인 경우
		{
			prevNode -> nextNode = tail;
		}
		else //현재 노드가 마지막 노드가 아닌 경우
		{
			prevNode -> nextNode = targetNode -> nextNode;
		}
		//지우려는 노드 메모리 해제
		targetNode -> nextNode = nullptr;
		targetNode = nullptr;
		delete targetNode;
	}
	//특정 데이터를 가진 노드 찾기
	NODE *findNode( int nData )
	{
		NODE *curNode = head -> nextNode;
		//리스트 순회하며 데이터 탐색
		while ( curNode -> nextNode != NULL )
		{
			if ( curNode -> nData == nData )
			{
				return curNode; //데이터가 일치하는 노드 반환
			}
			curNode = curNode -> nextNode;
		}
		return nullptr; //데이터를 찾지 못한 경우
	}
	//리스트의 모든 데이터 출력
	void ShowAll()
	{
		if ( head -> nextNode == tail )
		{
			cout << "빈 리스트입니다." << endl;
			return;
		}
		//첫 노드부터 모든 데이터 조회
		NODE *curNode = head -> nextNode;
		while ( true )
		{
			cout << curNode -> nData;
			if ( curNode -> nextNode == tail )
			{
				break;
			}
			else
			{
				cout << "-";
				curNode = curNode -> nextNode;
			}
		}
		cout << endl;
	}
};
int main()
{
	LinkedList linkedList = LinkedList();
	linkedList.ShowAll();
	//addFront 예제
	linkedList.AddFront( 3 );
	linkedList.ShowAll();
	linkedList.AddFront( 2 );
	linkedList.ShowAll();
	linkedList.AddFront( 1 );
	linkedList.ShowAll();
	//pushBack 예제
	linkedList.PushBack( 4 );
	linkedList.ShowAll();
	linkedList.PushBack( 5 );
	linkedList.ShowAll();
	//findNode
	NODE *curNode = linkedList.findNode( 5 );
	//insert 예제
	if ( curNode != 0 )
	{
		linkedList.InsertNode( curNode, 6 );
		linkedList.ShowAll();
	}
	//deleteNode 예제
	linkedList.DeleteNode( 1 );
	linkedList.ShowAll();
	linkedList.DeleteNode( 6 );
	linkedList.ShowAll();
	linkedList.DeleteNode( 5 );
	linkedList.ShowAll();
	return 0;
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
레벨 순회를 하기 위해선 큐를 이용해야 합니다. 왜냐하면 레벨 순회는 각 노드를 방문한 순서대로 저장하고 이를 처리하기 위해 선입선출 방식이 필요한데, 이때 선입선출 구조로 저장하는 선형 자료구조인 큐가 레벨 순회를 구현하는데 가장 적합하기 때문입니다.
```ruby
#include <iostream>
#include <queue> // 큐를 사용하기 위한 헤더
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
	struct NODE* node_ptr; //NODE 구조체를 가리키는 포인터(동적으로 생성된 노드의 주소를 저장하는 데 사용)
	node_ptr = new NODE(); //NODE 구조체 크기만큼의 공간을 할당
	node_ptr->nData = nData;
	node_ptr->l_child = NULL; //왼쪽 자식 노드 초기화
	node_ptr->r_child = NULL; //오른쪽 자식 노드 초기화
	return node_ptr;
}
// 레벨순회 함수
void levelorder(struct NODE* root) {
	if (root == NULL) return; // 트리가 비어있으면 반환

	queue<struct NODE*> q; // 노드를 저장할 큐 생성
	q.push(root); // 루트 노드를 큐에 추가

	while (!q.empty()) { // 모든 노드를 처리할 때까지 반복적으로 큐에서 노드를 꺼내고, 그 노드의 자식들을 큐에 추가
		struct NODE* current = q.front(); // 큐의 앞부분 가져오기
		q.pop(); // 큐에서 제거
		cout << current->nData << " "; // 현재 노드값 출력

		if (current->l_child != NULL) {
			q.push(current->l_child); // 왼쪽 자식 노드가 있으면 큐에 추가
		}
		if (current->r_child != NULL) {
			q.push(current->r_child); // 오른쪽 자식 노드가 있으면 큐에 추가
		}
	}
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
	root = new_node(1);
	root->l_child = new_node(2);
	root->l_child->l_child = new_node(4);
	root->r_child = new_node(3);
	root->r_child->l_child = new_node(5);
	root->r_child->r_child = new_node(6);
	//루트 노드 1,1의 왼쪽 자식 노드 2,2의 왼쪽 자식 노드 4,1의 오른쪽 자식 노드 3,3의 왼쪽 자식 노드 5,3의 오른쪽 자식 노드 6
	cout << "레벨순회 : "; //레벨순회 출력
	levelorder(root); //레벨순회
	cout << endl;
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
```ruby
#include <iostream>
#include <string>
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
#include <queue>
using namespace std;
//노드 구조체 정의
struct NODE
{
	int nData;
	NODE *left_child;
	NODE *right_child;
};
//이진 탐색 트리 클래스 정의
class CBinarySearchTree
{
public:
	NODE *root;
	int nTree_size;
	CBinarySearchTree() //트리 초기화
	{
		this->root = NULL;
		nTree_size = 0;
	}
	//트리의 모든 노드를 재귀적으로 제거
	void deleteAll( NODE *root )
	{
		if ( root == NULL ) //노드가 없으면 작업 종료
		{
			return;
		}
		deleteAll( root -> left_child );
		deleteAll( root -> right_child );
		delete root;
		root = NULL; //포인터가 해제된 메모리 영역 가리킴 방지
	}
	//메모리 정리 및 메모리 누수 확인
	~CBinarySearchTree()
	{
		deleteAll( this -> root );
		this -> root = NULL;  //포인터가 해제된 메모리 영역 가리킴 방지
		_CrtDumpMemoryLeaks(); //메모리 누수 체크
	}
	//새로운 노드 생성
	NODE *createNode( int nData )
	{
		NODE *new_node = new NODE;
		new_node -> nData = nData;
		new_node -> left_child = NULL;
		new_node -> right_child = NULL;
		return new_node;
	}
	//노드를 트리에 추가
	void AddNode( int nData )
	{
		NODE *new_node = createNode(nData);
		NODE *temp = this -> root; //트리의 루트에서 시작
		if ( temp == NULL ) //트리가 비어있는 경우
		{
			this -> root = new_node;
			nTree_size++;
			cout << " 새 노드 추가 성공 " << nData << "\n";
		}
		else //트리가 비어있지 않은 경우
		{
			while ( true )
			{
				if ( temp -> nData >= nData ) //현재 노드 값보다 작거나 같은 경우
				{
					if ( temp->left_child == NULL ) //왼쪽 자식이 비어있으면
					{
						temp -> left_child = new_node;
						nTree_size++;
						break;
					}
					else
					{
						temp = temp -> left_child; //왼쪽 자식으로 이동
					}
				}
				else if ( temp -> nData < nData ) //현재 노드 값보다 큰 경우
				{
					if ( temp -> right_child == NULL ) //오른쪽 자식이 비어있으면
					{
						temp -> right_child = new_node;
						nTree_size++;
						break;
					}
					else
					{
						temp = temp -> right_child; //오른쪽 자식으로 이동
					}
				}
			}
			cout << " 새 노드 추가 성공 " << nData << "\n";
		}
	}
	//트리의 크기 출력
	void TreeSize()
	{
		cout << " 이진 탐색 트리의 크기 :  " << this->nTree_size << "\n";
	}
	//트리에서 특정 값을 가진 노드를 검색 
	NODE *findNode( NODE *temp, int nData )
	{
		if ( temp == NULL ) //노드가 NULL이면 값이 없음
		{
			cout << "데이터를 찾지 못했습니다!\n";
			return NULL;
		}
		else if ( temp -> nData == nData ) //값이 현재 노드와 일치하면 찾음
		{
			cout << "데이터를 찾았습니다!\n";
			return temp;
		}
		else if ( temp -> nData > nData ) //값이 작으면 왼쪽으로 이동
		{
			return findNode( temp -> left_child, nData );
		}
		else if ( temp -> nData < nData ) //값이 크면 오른쪽으로 이동
		{
			return findNode( temp -> right_child, nData );
		}
	}
	//트리에서 특정 값을 가진 노드를 삭제
	NODE *deleteNode( NODE *root, int nData )
	{
		if ( root == NULL ) //노드가 없으면 작업 종료
		{
			return root;
		}
		if ( nData < root -> nData) //값이 작으면 왼쪽 자식으로 이동
		{
			root -> left_child = deleteNode( root -> left_child, nData );
		}
		else if ( nData > root -> nData ) //값이 크면 오른쪽 자식으로 이동
		{
			root -> right_child = deleteNode( root -> right_child, nData );
		}
		else //삭제할 노드를 찾은 경우
		{
			NODE *temp;
			if ( root -> left_child == NULL ) //왼쪽 자식이 없는 경우
			{
				temp = root -> right_child; //오른쪽 자식으로 대체
				delete root;
				return temp;
			}
			else if ( root -> right_child == NULL ) //오른쪽 자식이 없는 경우
			{
				temp = root -> left_child; //왼쪽 자식으로 대체
				delete root;
				return temp;
			}
			else //두 자식이 있는 경우
			{
				temp = findMinNode( root -> right_child ); //오른쪽 서브트리의 최소값 찾기
				root -> nData = temp -> nData; //현재 노드 데이터 교체
				root -> right_child = deleteNode( root -> right_child, temp -> nData ); //최소값 삭제
			}
		}
		return root;
	}
	//오른쪽 서브트리에서 최소값을 가진 노드를 찾음
	NODE *findMinNode( NODE *root )
	{
		NODE *temp = root;
		while ( temp -> left_child != NULL )
		{
			temp = temp -> left_child; //왼쪽으로 계속 이동
		}
		return temp;
	}
	//중위 순회
	NODE *inorderTraversal( NODE *root )
	{
		if ( root == NULL ) 
		{
			return NULL;
		}
		inorderTraversal( root->left_child );
		cout << root -> nData << ' ';
		inorderTraversal( root -> right_child );
	}
	//전위 순회
	NODE *preorderTraversal( NODE *root )
	{
		if ( root == NULL )
		{
			return NULL;
		}
		cout << root -> nData << ' ';
		preorderTraversal( root -> left_child );
		preorderTraversal( root -> right_child );
	}
	//후위 순회
	NODE *postorderTraversal( NODE *root )
	{
		if ( root == NULL )
		{
			return NULL;
		}
		postorderTraversal( root -> left_child );
		postorderTraversal( root -> right_child );
		cout << root -> nData << ' ';
	}
	//레벨 순회
	void levelOrderTraversal(NODE* root)
	{
		if (root == NULL) // 트리가 비어있으면 종료
		{
			cout << "트리가 비어있습니다.\n";
			return;
		}
		queue<NODE*> q; // 노드를 저장할 큐
		q.push(root);   // 루트 노드를 큐에 추가

		while (!q.empty())
		{
			NODE* current = q.front(); // 큐의 앞에 있는 노드 가져오기
			q.pop();                   // 큐에서 제거
			cout << current->nData << " "; // 현재 노드의 값 출력

			// 왼쪽 자식이 있으면 큐에 추가
			if (current->left_child != NULL)
			{
				q.push(current->left_child);
			}
			// 오른쪽 자식이 있으면 큐에 추가
			if (current->right_child != NULL)
			{
				q.push(current->right_child);
			}
		}
		cout << "\n";
	}

};
int main()
{
	int nNum;
	nNum = 1000000; //초기 반복 횟수
	string Command; //사용자로부터 입력받을 명령어 저장 변수
	CBinarySearchTree bst; //이진 탐색 트리 객체 생성
	while ( nNum )
	{
		cin >> Command; //명령어 입력
		if ( Command == "add" )
		{
			int nData;
			cin >> nData;
			bst.AddNode(nData);
		}
		else if ( Command == "find" )
		{
			int nData;
			cin >> nData;
			bst.findNode( bst.root, nData );
		}
		else if ( Command == "delete" )
		{
			int nData;
			cin >> nData;
			bst.root = bst.deleteNode( bst.root, nData );
		}
		else if ( Command == "inorder" )
		{
			bst.inorderTraversal( bst.root );
			cout << "\n";
		}
		else if ( Command == "preorder" )
		{
			bst.preorderTraversal( bst.root );
			cout << "\n";
		}
		else if ( Command == "postorder" )
		{
			bst.postorderTraversal( bst.root );
			cout << "\n";
		}
		else if (Command == "levelorder")
		{
			bst.levelOrderTraversal(bst.root);
			cout << "\n";
		}
		else if ( Command == "size" )
		{
			bst.TreeSize();
		}
		else
		{
			cout << "올바른 명령어 양식을 입력해 주세요(add, find, delete, inorder, preorder, postorder, levelorder, size)" << "\n";
		}
	}
	//프로그램 종료 전 트리의 모든 노드 삭제 및 메모리 정리
	bst.deleteAll( bst.root );
	bst.root = NULL; //포인터가 해제된 메모리 영역 가리킴 방지
	return 0;
}
```
* 출력
![image](https://github.com/user-attachments/assets/723bfe60-af85-42d6-a44e-69d8b658bbec)
-----------------------
* 덱 : 
  덱이란 양쪽 끝에서 삽입과 삭제가 모두 가능한 선형 자료 구조의 한 형태로, 큐와 스택을 합친 형태라고 할 수 있습니다.
* 덱의 종류
  * 스크롤 : 입력이 한쪽 끝으로만 가능하도록 설정한 덱(입력 제한 덱)
  * 셀프 : 출력이 한쪽 끝으로만 가능하도록 설정한 덱(출력 제한 덱)
------------------
* 코드
```ruby
#include <iostream>
#include <deque>
using namespace std;
int main()
{
	deque<int> DQ;
	DQ.push_front(1); //덱의 앞쪽에 1 삽입
	DQ.push_back(2); //덱의 뒤쪽에 2 삽입
	DQ.push_front(3); //덱의 앞쪽에 3 삽입 
	DQ.insert(DQ.begin() + 1, 5); //begin()은 덱의 시작 위치, 시작 위치 +1 = 두 번째 위치이므로 두 번째 위치에 5 삽입
	cout << DQ.size() << '\n'; //덱의 크기 출력
	if (!DQ.empty()) //덱이 비어있지 않은경우
	{
		cout << "덱이 비어있지 않습니다!" << '\n';
	}
	cout << DQ.front() << '\n'; //덱의 앞쪽 첫 번째 요소 출력
	cout << DQ.back() << '\n'; //덱의 마지막 요소 출력
	cout << DQ[1] << '\n'; //덱의 두 번쨰 요소 출력
	return 0;
}
```
* 출력
  ![image](https://github.com/user-attachments/assets/99d59e0b-d405-4060-84be-2afc24ac27fc)
