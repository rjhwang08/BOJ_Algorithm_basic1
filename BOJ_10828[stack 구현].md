```c++
#include<stdio.h>
#include<iostream>
#include<string>
using namespace std;

struct stack {                     //최근 컴파일러 버전에서는 typedef를 쓰지 않아도 struct를 생략 가능함
	int arr[10000];				   //C의 구조체와 C++의 구조체는 차이점이 있음. https://twinparadox.tistory.com/268
	int size = 0;
};

void push(stack *stk, int x) {
	stk->arr[(*stk).size++] = x;       //구조체 포인터 멤버 접근 방법 두가지 복습
}

bool empty(stack *stk) {
	if (stk->size == 0) return true;
	else return false;
}

int pop(stack *stk) {
	if (empty(stk)) return -1;
	else return stk->arr[--stk->size];
}

int top(stack *stk) {
	if (empty(stk)) return -1;
	else return stk->arr[stk->size - 1];
}

int main() {
	int N;
	stack s;
	scanf("%d", &N);

	while(N--){
		string str;
		cin >> str;
		if (str == "push") {
			int num;
			cin >> num;
			push(&s, num);
		}
		else if (str == "pop") {
			int num = pop(&s);
			cout << num << '\n';
		}
		else if (str == "size") {
			cout << s.size << '\n';
		}
		else if (str == "empty") {
			cout << empty(&s) << '\n';
		}
		else if (str == "top") {
			cout << top(&s) << '\n';
		}
	}
	return 0;
}
```
- 구조체와 클래스 차이
