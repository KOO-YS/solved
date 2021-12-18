# [BaekJoon#2775] 부녀회장이 될테야



> ### Problem
>
> https://www.acmicpc.net/problem/2775



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class Main {
    public static int[][] apt;
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();
        apt = new int[15][15];

        // each value setting
        for (int i=0; i<apt.length; i++) {
            apt[0][i] = i;
        }
        for (int i=1; i<apt.length; i++) {
            for (int j=1; j<apt[0].length; j++) {
                apt[i][j] = apt[i-1][j] + apt[i][j-1];
            }
        }

        // test case
        int T = Integer.parseInt(br.readLine());

        while (T-- > 0) {
            result
              .append(
                apt[Integer.parseInt(br.readLine())][Integer.parseInt(br.readLine())]
              )
              .append('\n');
        }
        System.out.print(result.toString());
    }
}
```
