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

        int stop = 1;
        while (stop != 0) {
            tokenizer = new StringTokenizer(br.readLine(), " ");

            int[] triangles = new int[3];
            for (int i = 0; i < 3; i++) {
                triangles[i] = Integer.parseInt(tokenizer.nextToken());
            }

            Arrays.sort(triangles);
            if (triangles[0] + triangles[1] <= triangles[2])
                System.out.println("Invalid");
            else {
                int side = triangles[0];



            }
        }




    }
}
```

