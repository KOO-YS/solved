# [BaekJoon#11650] 좌표 정렬하기



> ### Problem
>
> https://www.acmicpc.net/problem/11650



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

        Point[] points = new Point[N];

        for(int i=0; i<N; i++) {
            tokenizer = new StringTokenizer(br.readLine(), " ");
            int x = Integer.parseInt(tokenizer.nextToken());
            int y = Integer.parseInt(tokenizer.nextToken());

            points[i] = new Point(x, y);
        }

        Arrays.sort(points);

        for(Point p : points) {
            result.append(p.x).append(' ').append(p.y).append('\n');
        }

        System.out.println(result.toString());
    }

}

class Point implements Comparable<Point>{
    int x;
    int y;

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }

    @Override
    public int compareTo(Point o) {
        if(this.x > o.x) return 1;
        else if(this.x < o.x) return -1;
        return this.y - o.y;
    }
}
```

