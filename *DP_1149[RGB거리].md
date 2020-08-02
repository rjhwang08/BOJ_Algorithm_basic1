[1149](https://www.acmicpc.net/problem/1149)

1. Java
```java
import java.io.*;

public class Main {
	public static int min(int a, int b) {
		if(a > b) return b;
		return a;
	}
	
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());

		int[][] A = new int[N+1][3];   // N명에 대해 각각 RGB 비용
		int[][] D = new int[N+1][3];
		
		for(int i=1; i <= N; i++) {
			String[] input = br.readLine().split(" ");
			for(int j=0; j < 3; j++)
				A[i][j] = Integer.parseInt(input[j]);
		}
		
		for(int i=1; i <= N; i++) {
			D[i][0] = min(D[i-1][1], D[i-1][2]) + A[i][0];
			D[i][1] = min(D[i-1][0], D[i-1][2]) + A[i][1];
			D[i][2] = min(D[i-1][0], D[i-1][1]) + A[i][2];
		}
		
		int ans = D[N][0];
		for(int j=1; j < 3; j++) {
			if(D[N][j] < ans)
				ans = D[N][j];
		}
		System.out.println(ans);
//		System.out.println(Math.min(Math.min(D[N][0], D[N][1]),D[N][2])); <-- 출력 한 줄로 정리 가능!
		br.close();
	}
}
```
