[1874](https://www.acmicpc.net/problem/1874)

1. JAVA
- [BufferedWriter를 사용하면 '출력초과'가 발생하는 이유](https://www.acmicpc.net/board/view/50019)

```java
import java.util.*;

public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		StringBuilder sb = new StringBuilder();
		Stack<Integer> stack = new Stack<Integer>();
		
		int n = sc.nextInt();
		int[] arr = new int[n];
		for(int i=0; i<n; i++)
			arr[i] = sc.nextInt();
		
		int num = 1;
		for(int x : arr) {
			if(x >= num) {
				while(x >= num) {
					stack.push(num++);
					sb.append("+\n");
				}
				stack.pop();
				sb.append("-\n");
			}
			else {
				if(stack.peek() != x) {
					System.out.println("NO\n");
					return;
				}
				else {
					stack.pop();
					sb.append("-\n");
				}
			}
		}
		System.out.println(sb);
	}
}
```

2. C++

```c++
#include<stdio.h>
#include<iostream>
#include<string>
#include<stack>
using namespace std;


int main() {
	stack<int> stk;
	string ans = "YES";
	string str;
	int T;
	int A[100000];
	int cnt = 1;

	cin >> T;
	for (int i = 0; i < T; i++)  {
		cin >> A[i];
		if (i == 0 || cnt <= A[i]) {
			while (cnt <= A[i]) {
				stk.push(cnt);
				str.push_back('+');
				cnt++;
			}
		}

		if (stk.top() == A[i]) {
			stk.pop();
			str.push_back('-');
		}
		else {
			ans = "NO";
		}
	}
	if (ans == "YES") {
		for (char ch : str) {
			cout << ch << '\n';;
		}
	}
	else {
		cout << ans << '\n';
	}

	return 0;
}
```
