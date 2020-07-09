[9093](https://www.acmicpc.net/problem/9093)  
- 스택의 LIFO 성질

1. JAVA
```java
import java.util.*;
import java.io.*;

public class Main {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		int T = Integer.parseInt(br.readLine());
		
		for(int i=0; i<T; i++) {
			String input = br.readLine() + "\n";
			Stack<Character> stack = new Stack<Character>();
			
			for(int j=0; j<input.length(); j++) {
				if(input.charAt(j) == ' ' || input.charAt(j) == '\n') {
					while(!stack.empty()) {
						bw.write(stack.pop());
					}
					bw.write(input.charAt(j));
				}
				else {
					stack.push(input.charAt(j));
				}
			}
		}
		bw.close();
	}
}
```
- 자바 String에서 인덱스를 통해 접근하기 위해서는 항상 'charAt'을 사용할 것


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
	cin.ignore();    //getline()함수에 개행 문자가 들어가는 것을 방지하기 위함
	while (T--) {
		stack<char> stk;
		string str;
		//cin >> s;   <- cin은 공백문자가 있으면 입력을 끊음
		getline(cin, str);
		str += '\n';
		int i;
		for (i = 0; i < str.size(); i++) {
			if (str[i] == ' ' || str[i] == '\n') {
				while (!stk.empty()) {
					cout << stk.top();
					stk.pop();
				}
				cout << str[i];
			} else stk.push(str[i]);
		}
	}
	return 0;
}
```
