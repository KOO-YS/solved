# [BaekJoon#10773] 제로



> ### Problem
>
> https://www.acmicpc.net/problem/10773




> ### Solution


```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader  br = new BufferedReader(new InputStreamReader(System.in));

        int K = Integer.parseInt(br.readLine());
        int[] input = new int[K];
        int index = 0;
        int total = 0;

        while ( K-- >0 ){
            input[index] = Integer.parseInt(br.readLine());
            if(input[index] == 0) {
                total -= input[--index];
            } else {
                total += input[index++];
            }
        }
        System.out.println(total);
    }
}

```
