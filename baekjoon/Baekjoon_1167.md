# [BaekJoon#1167] 트리의 지름



> ### Problem
>
> https://www.acmicpc.net/problem/1167



> ### Solution
>

```java
import java.io.*;
import java.util.*;

class Main {
//    https://www.acmicpc.net/problem/1167
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;

        // 트리의 정점의 개수
        int V = Integer.parseInt(br.readLine());

        // 간선 정보
        while(V-->0){
            token = new StringTokenizer(br.readLine(), " ");

            int from = Integer.parseInt(token.nextToken());

            while(true){
                int to = Integer.parseInt(token.nextToken());
                if(to == -1) break;
                int length = Integer.parseInt(token.nextToken());
            }
        }

        // 
    }


}
```
