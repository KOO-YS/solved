# [BaekJoon#1920] 수 찾기



> ### Problem
>
> https://www.acmicpc.net/problem/1920



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(br.readLine());

        String[] target = br.readLine().split(" ");
        Set<String> A = new HashSet<>();
        for(String num : target){
            A.add(num);
        }

        int M = Integer.parseInt(br.readLine());

        String[] compare = br.readLine().split(" ");
        for(String num : compare){
            if(A.contains(num)) result.append(1).append("\n");
            else result.append(0).append("\n");
        }
        System.out.print(result);
    }

}
```



> ####  반례
>
> ```
> 5
> -1 
> 0 
> 1 
> 2 
> 3
> 답 : 7
> ```
>
> ```
> 4
> -1 
> -1 
> -1 
> 3
> 답 : 3
> ```
>
> ```
> 3
> -6 
> -5 
> -1
> 답 : 29
> ```
>
> ```
> 2
> 1
> 2
> 답 : 3
> ```

