# [BaekJoon#1874] 스택 수열



> ### Problem
>
> https://www.acmicpc.net/problem/1874



> ### Solution 1

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Stack;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        int[] arr = new int[N];
        for (int i=0; i<N; i++) {
            arr[i] = Integer.parseInt(br.readLine());
        }

        StringBuilder result = new StringBuilder();
        Stack<Integer> stack = new Stack<>();

        int data = 1;
        for (int i=0; i<N; i++) {

            while (data <= arr[i]) {
                stack.push(data);
                data++;
                result.append("+\n");
            }
            if (stack.peek() == arr[i]) {
                stack.pop();
                result.append("-\n");
            } else {
                System.out.println("NO");
                return;
            }
        }
        System.out.println(result);
    }

}
```


