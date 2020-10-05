# [BaekJoon#9466] 텀 프로젝트



> ### Problem
>
> https://www.acmicpc.net/problem/9466

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static StringBuilder result;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;
        result = new StringBuilder();

        int T = Integer.parseInt(br.readLine());
        while(T-->0){
            // 학생 수
            int n = Integer.parseInt(br.readLine());
            int[] pick = new int[n+1];
            token = new StringTokenizer(br.readLine(), " ");
            for(int i=1; i<pick.length; i++){
                pick[i] = Integer.parseInt(token.nextToken());
            }
            result.append(notBelong(n, pick)+"\n");
        }
        System.out.print(result.toString());
    }
    public static int[] checked;
    public static int[] union;
    public static int notBelong(int n, int[] pick){
        int answer = 0;
        checked = new int[pick.length];
        union = new int[pick.length];

        // 언급되지 않은 학생 -> 팀에 속하지 못함
        for(int i=1; i<pick.length; i++){
            if(checked[i] == 0){
                answer += dfs(pick, i, i, 1);
            }
        }
        return n - answer;
    }
    // 순환을 이루는 학생 수 계산
    public static int dfs(int[] pick, int num, int start, int count){
        if(checked[num]>0){
           if(union[num] != start) return 0;

           return count - checked[num];
        }
        union[num] = start;
        checked[num] = count;
        return dfs(pick,pick[num], start, count+1);
    }

}
```



반례

```
1
6
2 3 4 5 6 2

> 1
```