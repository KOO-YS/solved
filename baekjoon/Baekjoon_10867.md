# [BaekJoon#10867] 나이순정렬  



> ### Problem
>
> https://www.acmicpc.net/problem/10867



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main{

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());
        StringTokenizer token = new StringTokenizer(br.readLine(), " ");
        Set<Integer> numbers = new HashSet<>();
        while(N-->0){
            numbers.add(Integer.parseInt(token.nextToken()));
        }
        List<Integer> sorted = new ArrayList<>(numbers);
        Collections.sort(sorted);
        for(int i : sorted){
            System.out.print(i + " ");
        }
    }
}
```
