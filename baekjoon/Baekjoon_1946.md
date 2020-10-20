# [BaekJoon#1946] 신입사원

> ### Problem
>
> https://www.acmicpc.net/problem/1946



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();
        StringTokenizer token;
        int T = Integer.parseInt(br.readLine());

        while(T-->0){
            int N = Integer.parseInt(br.readLine());
            int[][] volunteer = new int[N][2];
            for(int i=0; i<N; i++){
                token = new StringTokenizer(br.readLine(), " ");
                volunteer[i][0] = Integer.parseInt(token.nextToken());
                volunteer[i][1] = Integer.parseInt(token.nextToken());
            }
            result.append(peek(volunteer)).append("\n");
        }
        System.out.print(result);
    }
    public static int peek(int[][] volunteer){
        int count = 1;      // 1등 무조건 선발
        Arrays.sort(volunteer, (o1, o2) -> o1[0] - o2[0]);

        if(volunteer.length == 1) return count;

        int before = volunteer[0][1];
        for(int i=1; i<volunteer.length; i++){
            if(before > volunteer[i][1]){
                before = volunteer[i][1];
                count++;
            }
        }
        return count;
    }
}
```



>#### 문제 이해
>
>예시 ) 
>
>서류 / 면접 성적으로 선발
>
>A의 서류 성적이 4등이라면?
>
>*<u>면접시험이 적어도 다른 지원자보다 떨어지지 않는 자만 선발한다</u>*  `means`
>
>1,2,3등과 면접 성적을 비교해봤을 때 A의 면접 성적이 떨어지지 않는다면 선발 가능! 

