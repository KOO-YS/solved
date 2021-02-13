# [BaekJoon#1085] 직사각형에서 탈출



> ### Problem
>
> https://www.acmicpc.net/problem/1085



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer stringTokenizer = new StringTokenizer(br.readLine());

        int x = Integer.parseInt(stringTokenizer.nextToken());
        int y = Integer.parseInt(stringTokenizer.nextToken());
        int w = Integer.parseInt(stringTokenizer.nextToken());
        int h = Integer.parseInt(stringTokenizer.nextToken());

        int verticalMin = Math.min(y, h-y);
        int horizontalMin = Math.min(x, w-x);

        int totalMin = Math.min(verticalMin, horizontalMin);

        System.out.println(totalMin);

    }
}
```
