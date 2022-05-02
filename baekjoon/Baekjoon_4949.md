# [BaekJoon#4949] 균형잡힌 세상



> ### Problem
>
> https://www.acmicpc.net/problem/4949

<br>

> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Stack;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        String line;
        while (!(line = br.readLine()).equals(".")) {
            result.append(isBalanced(line)).append('\n');
        }

        System.out.println(result.toString());
    }

    public static String isBalanced(String str) {
        Stack<Character> bracket = new Stack<>();
        for (char c : str.toCharArray()) {
            if (c == '[' || c == '(')
                bracket.add(c);
            else if (c == ']') {
                if (!bracket.isEmpty() && bracket.peek() == '[')
                    bracket.pop();
                else return "no";
            } else if (c == ')') {
                if (!bracket.isEmpty() && bracket.peek() == '(')
                    bracket.pop();
                else return "no";
            }
        }
        return bracket.isEmpty()? "yes" : "no";
    }
}

```
