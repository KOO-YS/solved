# [BaekJoon#1764] 듣보잡



> ### Problem
>
> https://www.acmicpc.net/problem/1764



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(tokenizer.nextToken());
        int M = Integer.parseInt(tokenizer.nextToken());

        Set<String> neverSeen = new HashSet<>();
        Set<String> evenNeverHeard = new TreeSet<>();

        for(int i=0; i<N; i++){
            neverSeen.add(br.readLine());
        }

        for(int i=0; i<M; i++){
            String name = br.readLine();
            if(neverSeen.contains(name)){
                evenNeverHeard.add(name);
            }
        }

        System.out.println(evenNeverHeard.size());
        Iterator<String> iterator = evenNeverHeard.iterator();
        while(iterator.hasNext()){
            System.out.println(iterator.next());
        }
    }
}
```
