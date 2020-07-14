[11576](https://www.acmicpc.net/problem/11576)
- StringBuilder의 reverse()메소드를 이용하여 풀어봤으나 틀림(원인은 모르겠음)
- 다른 사람들 해결책을 참고하여 그냥 스택을 이용하여 뒤집음(1번)
- 2번은 재귀함수를 이용한 다른 사람의 풀이

1. Java
```java
import java.io.*;
import java.util.*;

public class Main {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		Stack<Integer> stack = new Stack<>();
		String[] input = br.readLine().split(" ");
		int A = Integer.parseInt(input[0]);
		int B = Integer.parseInt(input[1]);
		int m = Integer.parseInt(br.readLine());
		int sum = 0;
		input = br.readLine().split(" ");
		
		for(int i=0; i < m; i++)
			sum += Integer.parseInt(input[i]) * (int)Math.pow(A, m-1-i);
		
		while(sum > 0) {
			int r = sum % B;
			stack.push(r);
			sum /= B;
		}
		int size = stack.size();
	    for(int i = 0; i < size; i++)
	    	System.out.print(stack.pop() + " ");	    
		br.close();
	}

```

2. Java(재귀 이용) + 10진법으로 변환하는 부분도 참고
```java
import java.util.*;

public class Main {
    public static void convert(int num, int base) {
        if (num == 0) {
            return;
        }
        convert(num/base, base);
        System.out.print(num%base + " ");
    }
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();
        int n = sc.nextInt();
        int ans = 0;
        for (int i = 0; i<n; i++) {
            int x = sc.nextInt();
            ans = ans * a + x;
        }
        convert(ans, b);
        System.out.println();
    }
}
```
