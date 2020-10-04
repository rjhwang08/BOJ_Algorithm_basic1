[1149](https://www.acmicpc.net/problem/1149)

- 이걸 왜 처음 풀었을 때는 별 한개만 줬을지 모르겠지만, 방법을 모르면 꽤 까다로웠음
- d배열에서 나는 해당 순서의 집까지에 대한 최소합을 저장하려 했는데, 그러면 다음 집에서 최소를 고르지 못하게 되는 문제가 어려웠음
- 근데 해답을 보니 결국 이럴 땐 무식하게 R을 칠했을 때 최소값, G를 칠했을 때 최소값, B를 칠했을 때 최소값 모두 구해서 최소값을 비교하면 되는 

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
