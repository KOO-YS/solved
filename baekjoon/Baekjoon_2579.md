# [BaekJoon#2579] 계단 오르기



> ### Problem
>
> https://www.acmicpc.net/problem/2579



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
    public static long[] stair;
    public static int[] step;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        step = new int[N+1];

        for(int i=1; i<=N; i++){
            step[i] = Integer.parseInt(br.readLine());
        }
        stair = new long[N+1];   // i번째까지 계단이 주어졌을 때, 최대값 담을 배열
        /**
         *  N = 1 or 2,
         *      모든 계단을 밟으면 된다
         *  N = 3,
         *      stair[3] = 3번째 계단과 1 or 2 중 더 값이 큰 계단을 밟으면 된다
         *  N >= 4,
         *      N번째 계단과 Math.max((N-1번째 계단 + stair[N-3]), (stair[N-2)) -> 점화식 시작
         */

        if(N ==1){
            System.out.println(step[1]);
            return;
        }

        stair[1] = step[1];
        stair[2] = step[1]+step[2];

        System.out.println(dp(N));
    }

    public static long dp(int num){
        if(num < 3) {
            return stair[num];
        }
        if(stair[num] == 0){        // not initialized yet
            long case1 = dp(num-2);
            long case2 = step[num-1] +dp(num-3);
            stair[num] = Math.max(case1, case2) + step[num];
        }
        return stair[num];
    }
}
```



```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
	public static void main(String[] args) throws NumberFormatException, IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int n = Integer.parseInt(br.readLine());
		long[] stair = new long[n+1];
		for(int i=1; i<stair.length; i++) {
			stair[i] = Integer.parseInt(br.readLine());
		}
		long answer = climbing(stair);
		System.out.println(answer);
	}
	public static long climbing(long[] stair) {
		long[] score = new long[stair.length];
		
		score[1] = stair[1];
		if(score.length == 2) return score[1];
		
		score[2] = stair[1]+stair[2];
		
		for(int  i=3; i<stair.length; i++) {
			long one = score[i-2];
			long two = stair[i-1]+score[i-3];
			score[i] = (one>two? one:two) + stair[i];
		}
		
		return score[stair.length-1];
	}
}
```

