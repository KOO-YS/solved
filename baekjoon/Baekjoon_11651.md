# [BaekJoon#11651] 거짓말



> ### Problem
>
> https://www.acmicpc.net/problem/11651



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        Point[] points = new Point[N];
        StringTokenizer tokenizer;
        for (int i=0; i<N; i++) {
            tokenizer = new StringTokenizer(br.readLine());
            points[i] = new Point(Integer.parseInt(tokenizer.nextToken()), Integer.parseInt(tokenizer.nextToken()));
        }

        Arrays.sort(points);

        for (Point p : points) {
            System.out.println(p);
        }

    }

    static class Point implements Comparable<Point>{

        int x;
        int y;

        public Point(int x, int y) {
            this.x = x;
            this.y = y;
        }

        @Override
        public int compareTo(Point o) {
            if (this.y > o.y)
                return 1;
            else if (this.y < o.y)
                return -1;
            else return (this.x > o.x)?1:-1;
        }

        @Override
        public String toString() {
            return x + " " + y;
        }
    }
}
```
