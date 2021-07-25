# [BaekJoon#11000] 강의실 배정



> ### Problem
>
> https://www.acmicpc.net/problem/11000



> ### Solution

```java
import java.io.*;
import java.util.*;

class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(br.readLine());

        int[][] classes = new int[N][2];

        for(int i=0; i<N; i++) {
            tokenizer = new StringTokenizer(br.readLine());
            int S = Integer.parseInt(tokenizer.nextToken());
            int T = Integer.parseInt(tokenizer.nextToken());

            classes[i][0] = S;
            classes[i][1] = T;
        }

        // sorted by first column
        Arrays.sort(classes, (o1, o2) -> o1[0] - o2[0]);

        PriorityQueue<Integer> classroom = new PriorityQueue<>();

        classroom.add(classes[0][1]);
        for(int i=1; i<N; i++) {
            if(classroom.peek() <= classes[i][0]) {
                classroom.poll();
            }
            classroom.add(classes[i][1]);
        }

        System.out.println(classroom.size());
    }
}
```

