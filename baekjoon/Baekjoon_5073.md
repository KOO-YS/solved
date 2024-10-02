# [BaekJoon#5073] 삼각형과 세 변



> ### Problem
>
> https://www.acmicpc.net/problem/5073



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;
        StringBuilder result = new StringBuilder();

        while (true) {
            tokenizer = new StringTokenizer(br.readLine(), " ");

            int[] triangles = new int[3];
            for (int i = 0; i < 3; i++) {
                triangles[i] = Integer.parseInt(tokenizer.nextToken());
            }
            if (triangles[0] == 0)
                break;

            Arrays.sort(triangles);
            if (triangles[0] + triangles[1] <= triangles[2])
                result.append("Invalid");
            else {
                if (triangles[0] == triangles[1] && triangles[1] == triangles[2])
                    result.append("Equilateral");
                else if (triangles[0] == triangles[1] || triangles[1] == triangles[2])
                    result.append("Isosceles");
                else
                    result.append("Scalene");
            }
            result.append('\n');
        }
        System.out.print(result);
    }
}
```

