# [BaekJoon#1003] 피보나치



> ### Problem
>
> https://www.acmicpc.net/problem/1003



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

/**
 * n번째 피보나치 수를 구할때 0과 1이 출력되는 횟수를 출력
 * 
 * 0 -> 1 0
 * 1 -> 0 1
 * 2 -> 1 1 
 * 3 -> 1 2
 * 4 -> 2 3
 * n -> (n-1) + (n-2) 의 0 , 1 합
 * */

public class Main {
	public static void main(String[] args) throws NumberFormatException, IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int T = Integer.parseInt(br.readLine());
		
		int[][] leaf = new int[41][2];
		leaf[0][0] = 1;		// fibonacci(0) 일때 0-> 1번 | 1-> 0번
		leaf[1][1] = 1;		// fibonacci(1) 일때 0-> 0번 | 1-> 1번
		for(int i=2; i<leaf.length; i++) {
			leaf[i][0] = leaf[i-2][0]+leaf[i-1][0];
			leaf[i][1] = leaf[i-2][1]+leaf[i-1][1];
		}

		while(T-->0) {
			int n = Integer.parseInt(br.readLine());
			System.out.println(leaf[n][0]+" "+leaf[n][1]);
		}
	}	
}
```
