# [BaekJoon#13458] 시험감독



> ### Problem
>
> https://www.acmicpc.net/problem/13458



> ### Solution
>

```java
import java.io.*;
import java.util.*;

class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;

        // 시험장 개수
        int N = Integer.parseInt(br.readLine());
        token = new StringTokenizer(br.readLine(), " ");

        // 각 시험장에 있는 응시자의 수
        int[] A = new int[N];
        for(int i=0; i<A.length; i++){
            A[i] = Integer.parseInt(token.nextToken());
        }
        token = new StringTokenizer(br.readLine(), " ");
        // 총감독관이 감시할 수 있는 응시자의 수
        int B = Integer.parseInt(token.nextToken());
        // 부감독관이 감시할 수 있는 응시자의 수
        int C = Integer.parseInt(token.nextToken());

        System.out.println(getMin(A, B, C));
        
    }

    public static long getMin(int[] rooms, int head, int assistant){
        long supervision = 0;
        for(int i : rooms){
            i = (i-head);
            supervision++;
            if(i > 0) supervision += (i%assistant == 0)? i/assistant : i/assistant+1;
        }

        return supervision;
    }
}
```



> -> 결과값의 범위가 int 범위를 벗어날 가능성이 있다
>
> 1,000,000 * 1,000,000....