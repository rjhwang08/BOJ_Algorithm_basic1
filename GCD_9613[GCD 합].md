[9613](https://www.acmicpc.net/problem/9613)

- 항상 입력 범위를 확인하고 1.시간 2.자료형 크기 고려하기!!

1. Java
```java
import java.io.*;
import java.util.*;

public class Main {
	public static long gcd(long a, long b) {
		if(b == 0)
			return a;
		else return gcd(b, a%b);
	}
	
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		int t = Integer.parseInt(br.readLine());
		
		for(int i=1; i <= t; i++) {
			String[] input = br.readLine().split(" ");
			int n = Integer.parseInt(input[0]);
			long[] arr = new long[n];
			for(int j=0; j < n; j++)
				arr[j] = Long.parseLong(input[j+1]);
			
			long sum = 0;
			for(int j=0; j < n-1; j++) {
				for(int k=j+1; k < n; k++)
					sum += gcd(arr[j], arr[k]);
			}
			bw.write(sum + "\n");
		}
		bw.flush();
		bw.close();
		br.close();
	}
}
```
