[1158](https://www.acmicpc.net/problem/1158)

1. Java (출력 시 형변환 주의!!)
```java
import java.util.*;
import java.io.*;

public class Main {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		Queue<Integer> queue = new LinkedList<>();
		
		String input = br.readLine();
		int N = Integer.parseInt(input.split(" ")[0]);
		int K = Integer.parseInt(input.split(" ")[1]);
		
		for(int i=1; i <= N; i++)
			queue.offer(i);

		bw.write("<");
		while(!queue.isEmpty()) {
			for(int i=0; i < K-1; i++) {
				queue.offer(queue.poll());
			}
			// BufferedWriter에서 int형을 출력하기 위해서는 String으로 형변환 해줘야함
			bw.write(Integer.toString(queue.poll()));
			if(queue.isEmpty())
				bw.write(">");
			else
				bw.write(", ");
		}
		
		bw.flush();
		br.close();
		bw.close();
	}
}
```
