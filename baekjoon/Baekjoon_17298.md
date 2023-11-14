# [BaekJoon#17298] 오큰수 구하기



> ### Problem
>
> https://www.acmicpc.net/problem/17298



> ### Solution


```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.Stack;
import java.util.StringTokenizer;
import java.util.stream.Collectors;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        int[] arr = new int[N];
        StringTokenizer token = new StringTokenizer(br.readLine());
        for (int i=0; i<N; i++) {
            arr[i] = Integer.parseInt(token.nextToken());
        }
        int[] answer = new int[N];

        Stack<Integer> stack = new Stack();
        stack.push(0);
        for (int i=1; i<N; i++) {
            while (!stack.isEmpty() && arr[stack.peek()] < arr[i]) {
                answer[stack.peek()] = arr[i];
                stack.pop();
            }
            stack.push(i);
        }
        while (!stack.isEmpty()) {
            answer[stack.pop()] = -1;
        }

        System.out.println(Arrays.stream(answer).mapToObj(i -> i+"").collect(Collectors.joining(" ")));

    }

}
```
