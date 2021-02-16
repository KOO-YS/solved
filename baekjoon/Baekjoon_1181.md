# [BaekJoon#1181] 단어 정렬



> ### Problem
>
> https://www.acmicpc.net/problem/1181



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.Comparator;
import java.util.HashSet;
import java.util.Set;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(br.readLine());

        Set<String> words = new HashSet<>();

        for(int i=0; i<N; i++){
            words.add(br.readLine());
        }
        String[] order = new String[words.size()];
        words.toArray(order);

        Arrays.sort(order, new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                if(o1.length() < o2.length()) return -1;
                else if(o1.length() > o2.length()) return 1;

                return o1.compareTo(o2);
            }
        });

        for(String str : order){
            result.append(str).append("\n");
        }

        System.out.print(result.toString());
    }
}
```
