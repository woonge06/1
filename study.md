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
	NODE *NextNode;
};

//링크드리스트 클래스 생성
class CLinkedList 
{
public:
	CLinkedList() 
	{
		//헤드와 테일의 포인터를 초기화
		m_Head = NULL;
		m_Tail = NULL;
	}
	//첫 번째(헤드) 노드 추가
	void AddFrontName( int N );
	//마지막(테일) 노드 추가
	void AddNode( int N );
	//노드 삽입
	void InsertNode( NODE* PrevNode, int nData );
	//노드 삭제
	void DeleteNode( NODE* PrevNode );
	//첫 번쨰 노드 가져오기
	NODE *GetHead() 
	{
		return m_Head;
	}
	//LinkedList 출력
	void display( NODE* m_Head );
private:
	NODE *m_Head;
	NODE *m_Tail;
};

//첫 번쨰 노드 추가
void CLinkedList::AddFrontName( int nData )
{
	NODE *Temp = new NODE;
	//temp의 데이터는 nData
	Temp->nData = nData;
	//LinkedList가 비어있으면
	if ( m_Head == NULL )
	{
		//첫 NODE는 temp
		m_Head = Temp;
		//마지막 NODE는 temp
		m_Tail = Temp;
	}
	//LinkedList에 데이터가 있으면
	else
	{
		//temp의 NextNode는 head
		Temp -> NextNode = m_Head;
		//head는 temp
		m_Head = Temp;
	}
}

//마지막에 노드 추가
void CLinkedList::AddNode( int nData )
{
	NODE *Temp = new NODE;
	//temp의 데이터는 nData
	Temp -> nData = nData;
	//temp의 NextNode = Null
	Temp -> NextNode = NULL;
	//LinkedList가 비어있으면
	if ( m_Head == NULL )
	{
		//첫 노드는 temp
		m_Head = Temp;
		//마지막 노드는 temp
		m_Tail = Temp;
	}
	//LinkedList에 데이터가 있으면
	else
	{
		//현재 마지막 노드의 NextNode는 temp
		m_Tail -> NextNode = Temp;
		//마지막 노드는 temp
		m_Tail = Temp;
	}
}

//노드 삽입
void CLinkedList::InsertNode( NODE *PrevNode, int nData )
{
	NODE *Temp = new NODE;
	//temp의 데이터는 nData
	Temp -> nData = nData;
	//temp의 NextNode 저장(삽입 할 앞 node의 NextNode를 temp의 NextNode에 저장)
	Temp -> NextNode = PrevNode -> NextNode;
	//temp 삽입
	//temp앞의 NODE의 NextNode를 temp로 저장
	PrevNode -> NextNode = Temp;
}

//노드 삭제
void CLinkedList::DeleteNode( NODE *PrevNode )
{
	//삭제할 노드를 temp에 저장(삭제할 노드의 1단계 전 노드의 NextNode)
	NODE *Temp = PrevNode -> NextNode;
	//삭제할 노드를 제외(삭제할 노드의 NextNode를 1단계 전 노드의 NextNode에 저장)
	PrevNode -> NextNode = Temp -> NextNode;
	//temp 삭제
	delete Temp;
}

//LinkedList 출력
void CLinkedList::display( NODE *m_Head )
{
	if ( m_Head != NULL )
	{
		cout << m_Head->nData << endl;
		display( m_Head->NextNode );
	}
	cout << endl;
}

//메인 함수
int main()
{
	CLinkedList LIst;
	//1추가
	LIst.AddNode( 1 );
	//2추가
	LIst.AddNode( 2 );
	//3추가
	LIst.AddNode( 3 );
	//display
	cout << "1,2,3을 LinkedList에 추가\n";
	LIst.display(LIst.GetHead());
	//0을 제일 앞에 추가
	LIst.AddFrontName( 0 );
	//1을 네번째에 추가
	LIst.InsertNode( LIst.GetHead() -> NextNode->NextNode, 1 );
	cout << "0을 첫번째에 추가, 1을 네번째에 추가\n";
	LIst.display( LIst.GetHead() );
	//세번째 노드 삭제
	LIst.DeleteNode( LIst.GetHead() -> NextNode );
	//display
	cout << "세번째 노드를 삭제\n";
	LIst.display( LIst.GetHead() );
	return 0;
}
```
```ruby
#include <iostream>
using namespace std;
struct NODE
{
	int nData;
	NODE *NextNode;
};

class CLinkedList2
{
public:
	CLinkedList2()
	{
		m_Head -> NextNode = m_Tail;
		m_Tail -> NextNode = NULL;
	}

	//맨 앞에 노드 추가
	void AddFront( int nData )
	{
		NODE *NewNode = new NODE;
		NewNode -> nData = nData;
		//노드가 한개도 없는 경우
		if ( m_Head -> NextNode == m_Tail )
		{
			m_Head -> NextNode = NewNode;
			NewNode -> NextNode = m_Tail;
		}
		//노드가 한개 이상인 경우
		else
		{
			NewNode -> NextNode = m_Head -> NextNode;
			m_Head -> NextNode = NewNode;
		}
	}

	//맨 뒤에 노드 추가
	void PushBack( int nData )
	{
		//노드가 한개도 없는 경우
		if ( m_Head->NextNode == NULL )
		{
			AddFront( nData );
		}
		//노드가 한개 이상인 경우
		else
		{
			//새로운 노드 생성
			NODE *NewNode = new NODE;
			NewNode -> nData = nData;
			//마지막 노드 찾기
			NODE *CurNode = m_Head -> NextNode;
			while ( CurNode -> NextNode != m_Tail )
			{
				CurNode = CurNode -> NextNode;
			}
			//tail 노드 앞에 삽입
			CurNode -> NextNode = NewNode;
			NewNode -> NextNode = m_Tail;
		}
	}

	//지정된 노드 뒤에 새 노드를 삽입
	void InsertNode(NODE *PrevNode, int nData)
	{
		if ( PrevNode == nullptr )
		{
			cout << "올바른 노드주소가 아닙니다. 데이터를 삽입할 수 없습니다.\n";
			return;
		}
		NODE *NewNode = new NODE;
		NewNode -> nData = nData;
		//prevNode가 맨 마지막에 있는 노드인 경우
		if ( PrevNode -> NextNode == m_Tail )
		{
			PrevNode -> NextNode = NewNode;
			NewNode -> NextNode = m_Tail;
			return;
		}
		//prevNode가 맨 마지막 노드가 아닌 경우
		NewNode -> NextNode = PrevNode -> NextNode;
		PrevNode -> NextNode = NewNode;
	}

	//특정 데이터를 가진 노드 삭제
	void DeleteNode( int nData )
	{
		NODE *TargetNode = nullptr;
		//빈 리스트인 경우
		if ( m_Head -> NextNode == m_Tail )
		{
			cout << "빈 리스트 입니다." << endl;
			return;
		}
		//첫번쨰 노드가 지우려는 노드일 때
		if ( m_Head -> NextNode -> nData == nData )
		{
			TargetNode = m_Head -> NextNode;
			m_Head -> NextNode = TargetNode -> NextNode;
			TargetNode = nullptr;
			delete TargetNode;
			return;
		}
		//지우려는 데이터의 이전 노드 찾기
		NODE *PrevNode = m_Head -> NextNode;
		while ( PrevNode -> NextNode != m_Tail )
		{
			if ( PrevNode -> NextNode -> nData == nData )
			{
				TargetNode = PrevNode -> NextNode;
				break;
			}
			PrevNode = PrevNode -> NextNode;
		}
		//지우려는 노드를 못찾은 경우
		if ( PrevNode -> NextNode == m_Tail )
		{
			cout << "해당 데이터는 존재하지 않습니다.\n";
			TargetNode = nullptr;
			return;
		}
		//지우려는 노드를 찾은 경우
		if ( TargetNode -> NextNode == m_Tail ) //현재 노드가 마지막 노드인 경우
		{
			PrevNode -> NextNode = m_Tail;
		}
		else //현재 노드가 마지막 노드가 아닌 경우
		{
			PrevNode -> NextNode = TargetNode -> NextNode;
		}
		//지우려는 노드 메모리 해제
		TargetNode -> NextNode = nullptr;
		TargetNode = nullptr;
		delete TargetNode;
	}

	//특정 데이터를 가진 노드 찾기
	NODE *FindNode( int nData )
	{
		NODE *CurNode = m_Head -> NextNode;
		//리스트 순회하며 데이터 탐색
		while ( CurNode -> NextNode != NULL )
		{
			if ( CurNode -> nData == nData )
			{
				return CurNode; //데이터가 일치하는 노드 반환
			}
			CurNode = CurNode -> NextNode;
		}
		return nullptr; //데이터를 찾지 못한 경우
	}

	//리스트의 모든 데이터 출력
	void ShowAll()
	{
		if ( m_Head -> NextNode == m_Tail )
		{
			cout << "빈 리스트입니다." << endl;
			return;
		}
		//첫 노드부터 모든 데이터 조회
		NODE *CurNode = m_Head -> NextNode;
		while ( true )
		{
			cout << CurNode -> nData;
			if ( CurNode -> NextNode == m_Tail )
			{
				break;
			}
			else
			{
				cout << "-";
				CurNode = CurNode -> NextNode;
			}
		}
		cout << endl;
	}

private:
	NODE *m_Head = new NODE;
	NODE *m_Tail = new NODE;
};

int main()
{
	CLinkedList2 LinkedList = CLinkedList2();
	LinkedList.ShowAll();
	//addFront 예제
	LinkedList.AddFront( 3 );
	LinkedList.ShowAll();
	LinkedList.AddFront( 2 );
	LinkedList.ShowAll();
	LinkedList.AddFront( 1 );
	LinkedList.ShowAll();
	//pushBack 예제
	LinkedList.PushBack( 4 );
	LinkedList.ShowAll();
	LinkedList.PushBack( 5 );
	LinkedList.ShowAll();
	//findNode
	NODE *CurNode = LinkedList.FindNode( 5 );
	//insert 예제
	if ( CurNode != 0 )
	{
		LinkedList.InsertNode( CurNode, 6 );
		LinkedList.ShowAll();
	}
	//deleteNode 예제
	LinkedList.DeleteNode( 1 );
	LinkedList.ShowAll();
	LinkedList.DeleteNode( 6 );
	LinkedList.ShowAll();
	LinkedList.DeleteNode( 5 );
	LinkedList.ShowAll();
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
	struct NODE *R_child; //오른쪽 자식 노드 정의
	struct NODE *L_child; //왼쪽 자식 노드 정의
};

//새 노드의 기능 만들기
struct NODE *New_node( int nData )
{
	struct NODE *Node_ptr; //NODE 구조체를 가리키는 포인터(동적으로 생성된 노드의 주소를 저장하는 데 사용)
	Node_ptr = new NODE(); //NODE 구조체 크기만큼의 공간을 할당
	Node_ptr -> nData = nData;
	Node_ptr -> L_child = NULL; //왼쪽 자식 노드 초기화
	Node_ptr -> R_child = NULL; //오른쪽 자식 노드 초기화
	return Node_ptr;
}

// 레벨순회 함수
void Levelorder( struct NODE *Root ) {
	if ( Root == NULL )
	{
		return; // 트리가 비어있으면 반환
	}
	queue<struct NODE*> Q; // 노드를 저장할 큐 생성
	Q.push( Root ); // 루트 노드를 큐에 추가

	while ( !Q.empty() ) { // 모든 노드를 처리할 때까지 반복적으로 큐에서 노드를 꺼내고, 그 노드의 자식들을 큐에 추가
		struct NODE *Current = Q.front(); // 큐의 앞부분 가져오기
		Q.pop(); // 큐에서 제거
		cout << Current -> nData << " "; // 현재 노드값 출력
		if ( Current -> L_child != NULL ) 
		{
			Q.push( Current -> L_child ); // 왼쪽 자식 노드가 있으면 큐에 추가
		}
		if ( Current -> R_child != NULL )
		{
			Q.push( Current -> R_child ); // 오른쪽 자식 노드가 있으면 큐에 추가
		}
	}
}

//전위순회 함수
void Preorder( struct NODE *Root )
{
	if ( Root ) //노드가 존재한다면
	{
		cout << Root -> nData << " "; //현재 노드값 출력
		Preorder( Root -> L_child ); //왼쪽 자식 노드 호출
		Preorder( Root -> R_child ); //오른쪽 자식 노드 호출
	}
}

//중위순회 함수
void Inorder( struct NODE *Root )
{
	if ( Root ) //노드가 존재한다면
	{
		Inorder( Root -> L_child ); //왼쪽 자식 노드 호출
		cout << Root -> nData << " "; //현재 노드값 출력
		Inorder( Root -> R_child ); //오른쪽 자식 노드 호출
	}
}

//후위순회 함수
void Postorder( struct NODE *Root )
{
	if ( Root ) //노드가 존재한다면
	{
		Postorder( Root -> L_child ); //왼쪽 자식 노드 호출
		Postorder( Root -> R_child ); //오른쪽 자식 노드 호출
		cout << Root -> nData << " "; //현재 노드값 출력
	}
}

//리프 기능 확인
bool Is_Leaf( struct NODE *Node ) {
	if ( Node == NULL )
	{
		return false; //n이 null이라면 false
	}
	if ( Node -> L_child == NULL && Node -> R_child == NULL )
	{
		return true; //만약 노드에 자식 노드가 없다면 리프 노드
	}
	return false; //자식 노드가 하나라도 있으면 false
}

//최대 함수 가져오기
int nGet_Max( int nA, int nB )
{
	return nA > nB ? nA : nB; //최댓값 비교
}

//깊이 함수 가져오기
int nGet_Depth( struct NODE *Node )
{
	if ( Is_Leaf( Node ) || Node == NULL ) //만약 n이 리프 노드이거나 NULL이라면 true
	{
		return 0;
	}
	else
	{
		// 왼쪽과 오른쪽 서브트리의 깊이를 비교하여 최댓값에 +1
		return nGet_Max( nGet_Depth( Node -> L_child ), nGet_Depth( Node -> R_child ) ) + 1;
	}
}

int main()
{
	struct NODE *Root; //트리의 루트 노드를 가리키는 포인터 root 선언
	//트리 구현
	Root = New_node(1);
	Root -> L_child = New_node(2);
	Root -> L_child -> L_child = New_node(4);
	Root -> R_child = New_node(3);
	Root -> R_child -> L_child = New_node(5);
	Root -> R_child -> R_child = New_node(6);
	//루트 노드 1,1의 왼쪽 자식 노드 2,2의 왼쪽 자식 노드 4,1의 오른쪽 자식 노드 3,3의 왼쪽 자식 노드 5,3의 오른쪽 자식 노드 6
	cout << "레벨순회 : "; //레벨순회 출력
	Levelorder( Root ); //레벨순회
	cout << endl;
	cout << "전위순회 : "; //전위순회 출력
	Preorder( Root ); //전위순회
	cout << endl;
	cout << "중위순회 : "; //중위순회 출력
	Inorder( Root ); //중위순회
	cout << endl;
	cout << "후위순회 : "; //후위순회 출력
	Postorder( Root ); //후위순회
	cout << endl;
	cout << "깊이(Depth) : " << nGet_Depth( Root ) << endl; //깊이 출력
	cout << "레벨(Level) : " << nGet_Depth( Root ) + 1; //깊이 +1 한 뒤 출력(레벨)
	cout << endl;
	return 0;
}
```
```ruby
#include <stdlib.h>
#include <crtdbg.h>
#include <iostream>
#include <string>
#include <queue>
#define _CRTDBG_MAP_ALLOC
using namespace std;
//노드 구조체 정의
struct NODE
{
	int nData;
	NODE *Left_child;
	NODE *Right_child;
};

//이진 탐색 트리 클래스 정의
class CTree2
{
public:
	NODE *Root;
	int nTree_size;
	CTree2() //트리 초기화
	{
		this->Root = NULL;
		nTree_size = 0;
	}

	//트리의 모든 노드를 재귀적으로 제거
	void DeleteAll( NODE *Root )
	{
		if ( Root == NULL ) //노드가 없으면 작업 종료
		{
			return;
		}
		DeleteAll( Root -> Left_child );
		DeleteAll( Root -> Right_child );
		delete Root;
		Root = NULL; //포인터가 해제된 메모리 영역 가리킴 방지
	}

	//메모리 정리 및 메모리 누수 확인
	~CTree2()
	{
		DeleteAll( this -> Root );
		this -> Root = NULL;  //포인터가 해제된 메모리 영역 가리킴 방지
		_CrtDumpMemoryLeaks(); //메모리 누수 체크
	}

	//새로운 노드 생성
	NODE *CreateNode( int nData )
	{
		NODE *New_node = new NODE;
		New_node -> nData = nData;
		New_node -> Left_child = NULL;
		New_node -> Right_child = NULL;
		return New_node;
	}

	//노드를 트리에 추가
	void AddNode( int nData )
	{
		NODE *New_node = CreateNode( nData );
		NODE *Temp = this -> Root; //트리의 루트에서 시작
		if ( Temp == NULL ) //트리가 비어있는 경우
		{
			this -> Root = New_node;
			nTree_size++;
			cout << " 새 노드 추가 성공 " << nData << "\n";
		}
		else //트리가 비어있지 않은 경우
		{
			while ( true )
			{
				if ( Temp -> nData >= nData ) //현재 노드 값보다 작거나 같은 경우
				{
					if ( Temp -> Left_child == NULL ) //왼쪽 자식이 비어있으면
					{
						Temp -> Left_child = New_node;
						//nTree_size++;
						break;
					}
					else
					{
						Temp = Temp -> Left_child; //왼쪽 자식으로 이동
					}
				}
				else if ( Temp -> nData < nData ) //현재 노드 값보다 큰 경우
				{
					if ( Temp -> Right_child == NULL ) //오른쪽 자식이 비어있으면
					{
						Temp -> Right_child = New_node;
						//nTree_size++;
						break;
					}
					else
					{
						Temp = Temp -> Right_child; //오른쪽 자식으로 이동
					}
				}
			}
			cout << " 새 노드 추가 성공 " << nData << "\n";
		}
	}

	//트리의 크기 출력
	void TreeSize()
	{
		cout << " 이진 탐색 트리의 크기 :  " << this -> nTree_size << "\n";
	}
	//트리에서 특정 값을 가진 노드를 검색 
	NODE *FindNode( NODE *Temp, int nData )
	{
		if ( Temp == NULL ) //노드가 NULL이면 값이 없음
		{
			cout << "데이터를 찾지 못했습니다!\n";
			return NULL;
		}
		else if ( Temp -> nData == nData ) //값이 현재 노드와 일치하면 찾음
		{
			cout << "데이터를 찾았습니다!\n";
			return Temp;
		}
		else if ( Temp -> nData > nData ) //값이 작으면 왼쪽으로 이동
		{
			return FindNode( Temp -> Left_child, nData );
		}
		else if ( Temp -> nData < nData ) //값이 크면 오른쪽으로 이동
		{
			return FindNode( Temp -> Right_child, nData );
		}
	}

	//트리에서 특정 값을 가진 노드를 삭제
	NODE *DeleteNode( NODE *Root, int nData )
	{
		if ( Root == NULL ) //노드가 없으면 작업 종료
		{
			return Root;
		}
		if ( nData < Root -> nData) //값이 작으면 왼쪽 자식으로 이동
		{
			Root -> Left_child = DeleteNode( Root -> Left_child, nData );
		}
		else if ( nData > Root -> nData ) //값이 크면 오른쪽 자식으로 이동
		{
			Root -> Right_child = DeleteNode( Root -> Right_child, nData );
		}
		else //삭제할 노드를 찾은 경우
		{
			NODE *Temp;
			if ( Root -> Left_child == NULL ) //왼쪽 자식이 없는 경우
			{
				Temp = Root -> Right_child; //오른쪽 자식으로 대체
				delete Root;
				return Temp;
			}
			else if ( Root -> Right_child == NULL ) //오른쪽 자식이 없는 경우
			{
				Temp = Root -> Left_child; //왼쪽 자식으로 대체
				delete Root;
				return Temp;
			}
			else //두 자식이 있는 경우
			{
				Temp = FindMinNode( Root -> Right_child ); //오른쪽 서브트리의 최소값 찾기
				Root -> nData = Temp -> nData; //현재 노드 데이터 교체
				Root -> Right_child = DeleteNode( Root -> Right_child, Temp -> nData ); //최소값 삭제
			}
		}
		return Root;
	}

	//오른쪽 서브트리에서 최소값을 가진 노드를 찾음
	NODE *FindMinNode( NODE *Root )
	{
		NODE *Temp = Root;
		while ( Temp -> Left_child != NULL )
		{
			Temp = Temp -> Left_child; //왼쪽으로 계속 이동
		}
		return Temp;
	}

	//중위 순회
	NODE *InorderTraversal( NODE *Root )
	{
		if ( Root == NULL ) 
		{
			return NULL;
		}
		InorderTraversal( Root->Left_child );
		cout << Root -> nData << ' ';
		InorderTraversal( Root -> Right_child );
	}

	//전위 순회
	NODE *PreorderTraversal( NODE *Root )
	{
		if ( Root == NULL )
		{
			return NULL;
		}
		cout << Root -> nData << ' ';
		PreorderTraversal( Root -> Left_child );
		PreorderTraversal( Root -> Right_child );
	}

	//후위 순회
	NODE *PostorderTraversal( NODE *Root )
	{
		if ( Root == NULL )
		{
			return NULL;
		}
		PostorderTraversal( Root -> Left_child );
		PostorderTraversal( Root -> Right_child );
		cout << Root -> nData << ' ';
	}

	//레벨 순회
	void LevelOrderTraversal(NODE* Root)
	{
		if (Root == NULL) // 트리가 비어있으면 종료
		{
			cout << "트리가 비어있습니다.\n";
			return;
		}
		queue<NODE*> Q; // 노드를 저장할 큐
		Q.push( Root );   // 루트 노드를 큐에 추가

		while (!Q.empty())
		{
			NODE *Current = Q.front(); // 큐의 앞에 있는 노드 가져오기
			Q.pop();                   // 큐에서 제거
			cout << Current->nData << " "; // 현재 노드의 값 출력

			// 왼쪽 자식이 있으면 큐에 추가
			if ( Current -> Left_child != NULL )
			{
				Q.push( Current -> Left_child );
			}
			// 오른쪽 자식이 있으면 큐에 추가
			if ( Current -> Right_child != NULL )
			{
				Q.push( Current -> Right_child );
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
	CTree2 Bst; //이진 탐색 트리 객체 생성
	while ( nNum )
	{
		cin >> Command; //명령어 입력
		if ( Command == "add" )
		{
			int nData;
			cin >> nData;
			Bst.AddNode(nData);
		}
		else if ( Command == "find" )
		{
			int nData;
			cin >> nData;
			Bst.FindNode( Bst.Root, nData );
		}
		else if ( Command == "delete" )
		{
			int nData;
			cin >> nData;
			Bst.Root = Bst.DeleteNode( Bst.Root, nData );
		}
		else if ( Command == "inorder" )
		{
			Bst.InorderTraversal( Bst.Root );
			cout << "\n";
		}
		else if ( Command == "preorder" )
		{
			Bst.PreorderTraversal( Bst.Root );
			cout << "\n";
		}
		else if ( Command == "postorder" )
		{
			Bst.PostorderTraversal( Bst.Root );
			cout << "\n";
		}
		else if (Command == "levelorder")
		{
			Bst.LevelOrderTraversal(Bst.Root);
			cout << "\n";
		}
		else if ( Command == "size" )
		{
			Bst.TreeSize();
		}
		else
		{
			cout << "올바른 명령어 양식을 입력해 주세요(add, find, delete, inorder, preorder, postorder, levelorder, size)" << "\n";
		}
	}
	//프로그램 종료 전 트리의 모든 노드 삭제 및 메모리 정리
	Bst.DeleteAll( Bst.Root );
	Bst.Root = NULL; //포인터가 해제된 메모리 영역 가리킴 방지
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
