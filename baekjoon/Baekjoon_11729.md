# [BaekJoon#11729] 하노이 탑 이동 순서



> ### Problem
>
> https://www.acmicpc.net/problem/11729



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {

    public static StringBuilder route = new StringBuilder();
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        // 원판의 개수
        int N = Integer.parseInt(br.readLine());

        int answer = hanoi(N, 1, 2, 3);

        System.out.println(answer);

        System.out.print(route.toString());
    }
    // 원판을 옮긴 횟수 계산 
    public static int hanoi(int n, int from, int by, int to){
        if( n == 1 ){
            move(from, to);
            return 1;
        }
        int total = 0;
        
        total += hanoi(n-1, from, to, by);
        total += hanoi(1, from, by, to);
        total += hanoi(n-1, by, from, to);

        return total;
    }
    // 옮긴 경로 입력
    public static void move(int from, int to){
        route.append(from+" "+to+"\n");
    }
}
```



> ###### 기둥 [1, 2, 3] 3개를 이용해 N개의 원판을 옮긴다
>
> -> N-1개의 원판을 [2] 기둥에 잠시 옮겨둔다
>
> -> 맨 밑 원판을 [3] 기둥에 옮긴다
>
> -> N-1개의 원판을 [3] 기둥으로 옮긴다
