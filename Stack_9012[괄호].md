1. Java(스택 사용 O)
```java
import java.util.*;
import java.io.*;

public class Main {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		int T = Integer.parseInt(br.readLine());
		
		while(T-- > 0) {
			Stack<Character> stack = new Stack<Character>();
			String input = br.readLine();
			int flag = 1;
			
			for(int i = 0; i < input.length(); i++) {
				if(input.charAt(i) == '(') {
					stack.push(input.charAt(i));
				}
				else if(input.charAt(i) == ')') {
					if(stack.size() == 0) {
						flag = 0;
						break;
					}
					else {
						stack.pop();
					}
				}
			}
			if(stack.size() != 0)
				flag = 0;
			
			if(flag == 1)
				bw.write("YES"+"\n");
			else
				bw.write("NO"+"\n");
		}
		bw.close();
	}
}
```

2. Java(스택 사용 X)
```java
import java.io.*;

public class Main {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		int T = Integer.parseInt(br.readLine());
		
		for(int i=0; i<T; i++) {
			String input = br.readLine();
			int cnt = 0;
			for(int j=0; j<input.length(); j++) {
				if(input.charAt(j) == '(')
					cnt++;
				else if(input.charAt(j) == ')') {
					if(cnt == 0) {
						cnt--;
						break;
					} else cnt--;
				}
			}
			if(cnt == 0) bw.write("YES\n");
			else bw.write("NO\n");
		}
		bw.flush();
		bw.close();
		br.close();
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
	int T;
	cin >> T;
	while (T--) {
		stack<char> stk;
		bool flag = true;
		string str;

		cin >> str;
		for (char ch : str) {
			if (ch == '(') {
				stk.push(ch);
			} else {
				if (stk.empty()) {
					flag = false;
					break;
				} else stk.pop();
			}
		}
		if (flag && stk.empty()) cout << "YES" << '\n';
		else cout << "NO" << '\n';
	}
	return 0;
}
```
