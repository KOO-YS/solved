# [BaekJoon#9012] 괄호



> ### Problem
>
> https://www.acmicpc.net/problem/9012



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.EmptyStackException;
import java.util.Stack;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(br.readLine());

        for(int i=0; i<N; i++){
            result.append(isVPS(br.readLine())).append("\n");
        }
        System.out.print(result);
    }
    public static String isVPS(String str){
        Stack<Integer> pairs = new Stack<>();
        try {
            for(char ch : str.toCharArray()){
                if(ch == '(') pairs.push(0);
                else pairs.pop();
            }
        } catch (EmptyStackException e){
            return "NO";
        }

        return pairs.isEmpty()? "YES":"NO";
    }
}
```
