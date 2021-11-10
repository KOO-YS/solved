# [BaekJoon#4153] 직각삼각형



> ### Problem
>
> https://www.acmicpc.net/problem/4153



> ### Solution 1

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

public class Main {

    public static char[][] chess;
    public static int MIN;
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        while(true) {
            int[] input = Arrays.stream(br.readLine().split(" "))
                        .mapToInt(Integer::parseInt).sorted().toArray();
            if (input[2] == 0) break;

            if (Math.pow(input[2], 2) == (Math.pow(input[0], 2) + Math.pow(input[1], 2)))
                result.append("right\n");
            else {
                result.append("wrong\n");
            }
        }
        System.out.print(result);
    }
}
```

<br>



> ### Solution 2
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

public class Main {

    public static char[][] chess;
    public static int MIN;
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        boolean isLast = false;
        while(!isLast) {
            int[] input = Arrays.stream(br.readLine().split(" "))
                        .mapToInt(Integer::parseInt).sorted().toArray();
            
            isLast = !(input[2]>0);	// 마지막 줄 0 0 0인지
            if (!isLast) {
                if (Math.pow(input[2], 2) == (Math.pow(input[0], 2) + Math.pow(input[1], 2)))
                    result.append("right\n");
                else {
                    result.append("wrong\n");
                }
            }
        }
        System.out.print(result.toString());
    }
}
```
