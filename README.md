BOJ 알고리즘 문제풀이 repo
=========================
### 더도 말고 하루 한 문제씩이라도 꾸준히..!
### 다른 정답코드는 BOJ 내 소스에서 확인하기

#### JAVA 자주 쓰는 문법 정리
- 입출력 - Scanner 클래스

>   [Scanner 설명](https://mine-it-record.tistory.com/103)
>  
>1. 클래스 호출 및 객체 생성
>```java
>// 둘 중 하나
>import java.util.Scanner;
>import java.util.*;
>
>// 객체 생성 - System.in : 키보드와 연결된 자바의 표준 입력 스트림으로 입력되는 키를 바이트로 리턴
>Scanner sc = new Scanner(System.in);
>```
>
>2. [주요 메소드](https://kutar37.tistory.com/entry/%EC%9E%90%EB%B0%94-String-%ED%81%B4%EB%9E%98%EC%8A%A4%EC%9D%98->%EB%A9%94%EC%86%8C%EB%93%9C)
>```java
>String next() // 공백 이전까지의 문자열을 입력 받음
>int nextInt(), double nextDouble() // 정수, 실수 등을 입력받을 때는 next + 자료형()
>String nextLine() // '\n'을 포함하는 한 라인을 읽고 '\n' 빼고 나머지 리턴
>```

- 입출력 - BufferedReader / BufferedWriter (버퍼를 이용해서 읽고 쓰는 함수 - Scanner보다 빠름)
>  
>  [참고 1](https://jhnyang.tistory.com/92)
>  [참고 2](https://coding-factory.tistory.com/251)
>
>1. 클래스 호출 및 객체 생성(+ main 문에 예외처리 throws IOException 꼭 넣어줘야 함!!)
>```java
>import java.io.*;
>
>// 객체 생성
>BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
>BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
>```
>
>2. BufferedReader 사용법
>```java
>String s = br.readLine();   // 라인 단위로 읽음(String 리턴)
>int i = Integer.parseInt(br.readLine()); // Int형으로 형변환
>```
>
>3. BufferedWriter 사용법
>```java
>String s = "rjhwang";
>bw.write(s+"\n");  // 출력(자동개행 없으므로 +"\n")
>bw.flush();        // 남아있는 데이터를 모두 출력시킴
>bw.close();        // 스트림을 닫음
>```
