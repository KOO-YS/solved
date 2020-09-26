# [BaekJoon#1541] 잃어버린 괄호



> ### Problem
>
> https://www.acmicpc.net/problem/1541



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.List;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer token = new StringTokenizer(br.readLine(), "(?-|+)", true);

        List<Integer>[] calculator = new ArrayList[token.countTokens()];

        int index = 0;

        // 초기화
        calculator[index] = new ArrayList<>();

        while(token.hasMoreTokens()){
            String next = token.nextToken();
            if(next.equals("-")){
                calculator[++index] = new ArrayList<>();
            } else if(next.equals("+")){
                continue;
            } else {            // number
                calculator[index].add(Integer.parseInt(next));
            }
        }

        int sum = 0;
        int bundle;
        int idx = 0;
        while(idx <= index){
            bundle = 0;
            for(int i=0; i<calculator[idx].size(); i++){
                bundle += calculator[idx].get(i);
            }
            if(idx == 0){
                sum += bundle;
            } else{
                sum -= bundle;
            }
            idx++;
        }

        System.out.println(sum);
    }
}
```
