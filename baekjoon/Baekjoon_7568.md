# [BaekJoon#7568] 덩치



> ### Problem
>
> https://www.acmicpc.net/problem/7568



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(br.readLine());

        Bulk[] arr = new Bulk[N];
        int[] rank = new int[N];
        for (int i=0; i<N; i++) {
            tokenizer = new StringTokenizer(br.readLine());
            arr[i] = new Bulk(Integer.parseInt(tokenizer.nextToken()), Integer.parseInt(tokenizer.nextToken()));
        }
        for (int i=0; i<N; i++) {
            for (int j=0; j<N; j++) {
                if(arr[i].weight < arr[j].weight && arr[i].height < arr[j].height)
                    rank[i]++;
            }
        }
        for (int i=0; i<N; i++) {
            result.append(rank[i]+1).append(' ');
        }
        System.out.println(result);
    }
}
class Bulk {
    int height;
    int weight;

    public Bulk(int height, int weight) {
        this.height = height;
        this.weight = weight;
    }
}
```
