# [BaekJoon#10828] 스택  



> ### Problem
>
> https://www.acmicpc.net/problem/10828



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.EmptyStackException;
import java.util.Stack;
import java.util.StringTokenizer;

public class Main {

    public static Stack<Integer> stack;
    public static StringBuffer result;          // 결과 문자열

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        // 명령의 수
        int N = Integer.parseInt(br.readLine());

        stack = new Stack<>();
        result = new StringBuffer();

        while(N-->0){
            readCommand(br.readLine());
        }
        System.out.print(result.toString());
    }

    // 명령 문자열 구분 처리
    public static void readCommand(String cmd){
        StringTokenizer token = new StringTokenizer(cmd, " ");
        if(token.countTokens() == 2){
            if(token.nextToken().equals("push")){
                int item = Integer.parseInt(token.nextToken());
                stack.push(item);
            }
        } else {
            switch (token.nextToken()){
                case "top":
                    try {
                        result.append(stack.peek());
                    } catch (EmptyStackException e){
                        result.append("-1");
                    }
                    break;
                case "size":
                    result.append(stack.size());
                    break;
                case "pop":
                    try{
                        result.append(stack.pop());
                    }catch (EmptyStackException e){
                        result.append("-1");
                    }
                    break;
                case "empty":
                    result.append((stack.isEmpty())?1:0);
                    break;
            }
            result.append("\n");
        }
    }
}

```

