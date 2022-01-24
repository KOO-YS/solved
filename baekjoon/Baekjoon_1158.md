# [BaekJoon#1158] 요세푸스 문제



> ### Problem
>
> https://www.acmicpc.net/problem/1158



> ### Solution


```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.List;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(tokenizer.nextToken());
        int K = Integer.parseInt(tokenizer.nextToken());

        List<Integer> people = new ArrayList<>();
        List<Integer> removeOrder = new ArrayList<>();
        for (int i=0; i<N; i++) {
            people.add(i+1);
        }

        int index = 0;
        while (N > 1) {
            index = (index + K) % people.size();
            index = (index == 0)? people.size()-1 : index - 1;

            removeOrder.add(people.remove(index));
            N--;
        }
        result.append('<');
        removeOrder.forEach(i -> result.append(i).append(", "));
        result.append(people.get(0));
        result.append('>');

        System.out.print(result);

    }
}
```
