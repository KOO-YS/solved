# [BaekJoon#1446] 지름길



> ### Problem
>
> https://www.acmicpc.net/problem/1446



> ### Solution

```java
import java.io.*;
import java.util.*;

//    https://www.acmicpc.net/problem/1446
class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine());
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(token.nextToken());    // 지름길 개수
        int D = Integer.parseInt(token.nextToken());    // 고속도로 길이

        int[] min = new int[10001];
        Arrays.fill(min, 10001);
        min[0] = 0;

        int[][] shortcut = new int[N][3];
        for(int i=0; i<N; i++){
            token = new StringTokenizer(br.readLine());
            // 시작점
            shortcut[i][0] = Integer.parseInt(token.nextToken());
            // 끝점
            shortcut[i][1] = Integer.parseInt(token.nextToken());
            // 지름길 거리
            shortcut[i][2] = Integer.parseInt(token.nextToken());
        }
        Arrays.sort(shortcut, new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return o1[0] - o2[0];       // 시작점 기준 정렬
            }
        });

        int index = 0;      // 지름길 배열의 인덱스
        int i = 0;          // 고속도로 i 킬로미터
        /*
        *  for문으로 i를 순차적으로 증가시키면 같은 출발시에서 시작하는 여러 지름길을 체크하지 못한다
        */
        while(i <= D) {
            if (index<N && i == shortcut[index][0]) {        // 지름길의 시작점과 같다면
                if (shortcut[index][1] <= D)
                    min[shortcut[index][1]] = Math.min(min[shortcut[index][1]], min[shortcut[index][0]] + shortcut[index][2]);
                index++;
            } else {
                min[i + 1] = Math.min(min[i + 1], min[i] + 1);
                i++;
            }
        }
        System.out.println(min[D]);
    }
}
```
