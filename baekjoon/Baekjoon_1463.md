# [BaekJoon#1463] 1로 만들기



> ### Problem
>
> https://www.acmicpc.net/problem/1463



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        eachCount = new int[N+1];
        Arrays.fill(eachCount, -1);     // 0과 구분
        eachCount[0] = 0;
        eachCount[1] = 0;

        System.out.print(operate(N));

    }
    public static int[] eachCount;
    public static int operate(int N){

        if(eachCount[N] != -1) return eachCount[N];

        int minCount = Integer.MAX_VALUE;       // init

        if(N%3 == 0){
            minCount = Math.min(minCount, operate(N/3));
        }
        if(N%2 == 0){
            minCount = Math.min(minCount, operate(N/2));
        }
        minCount = Math.min(minCount, operate(N-1));

        return eachCount[N] = (minCount + 1);
    }
}
```



> ### Solution (시간초과 실패)

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        System.out.print(operate(N, 0));

    }

    public static int operate(int N, int count){
        if(N == 1) return count;

        int minCount = Integer.MAX_VALUE;       // init

        if(N%3 == 0){
            minCount = Math.min(minCount, operate(N/3, count+1));
        }
        if(N%2 == 0){
            minCount = Math.min(minCount, operate(N/2, count+1));
        }
        minCount = Math.min(minCount, operate(N-1, count+1));

        return minCount;
    }
}
```
