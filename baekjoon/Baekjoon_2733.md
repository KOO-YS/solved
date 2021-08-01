# [BaekJoon#2733] Brainf*ck



> ### Problem
>
> https://www.acmicpc.net/problem/2733



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.HashMap;
import java.util.Stack;

class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();	// 전체 N개 프로그램 결과
        StringBuilder sb;		// i 번째 프로그램 결과
        
        int N = Integer.parseInt(br.readLine());
        
        String line;
        for (int i=1; i<=N; i++) {
            sb = new StringBuilder();
            while( !(line = br.readLine()).equals("end") ) {
                if( line.contains("%") ) {
                    sb.append(line.substring(0, line.indexOf("%")));
                } else sb.append(line);
            }
            // 결과 반환
            result.append("PROGRAM #").append(i).append(':').append('\n');
            result.append(brainfuck(sb.toString())).append('\n');
        }

        System.out.println(result.toString());

    }

    public static final int MAX_SIZE = 32768;
    public static final int MAX_VALUE = 256;
    
    private static String brainfuck(String string) {
        StringBuilder str = new StringBuilder();
        int max =0;
        int[] result = new int[MAX_SIZE];
        char[] cmd = string.toCharArray();

        int pointer = 0;

        HashMap<Integer, Integer> brackets = null;

        try {
            brackets = linkBracketPair(cmd);
        } catch (InvalidBracketException e) {
            return "COMPILE ERROR";
        }

        for (int i=0; i<cmd.length; i++) {
            char now = cmd[i];

            switch (now) {
                case '>' :
                    pointer = (pointer+1) % MAX_SIZE;
                    break;
                case '<' :
                    if(--pointer<0) pointer += MAX_SIZE;
                    break;
                case '+' :
                    result[pointer] = (result[pointer]+1) % MAX_VALUE;
                    break;
                case '-' :
                    if(--result[pointer] < 0) result[pointer] += MAX_VALUE;
                    break;
                case '.' :
                    str.append((char)result[pointer]);
                    break;
                case '[' :
                    if(result[pointer] == 0) {
                        // 짝이 되는 뒤쪽의 ]로 이동
                        i = brackets.get(i) - 1;
                    }
                    break;
                case ']' :
                    if(result[pointer] != 0) {
                        // 짝이 되는 앞의 [로 이동
                        i = brackets.get(i) - 1;
                    }
                    break;
                default: break;
            }
        }
        return str.toString();
    }

    private static HashMap<Integer, Integer> linkBracketPair(char[] cmd) {
        HashMap<Integer, Integer> brackets = new HashMap<>();
        Stack<Integer> stack = new Stack<>();

        try {
            for (int i = 0; i < cmd.length; i++) {
                if (cmd[i] == '[') {
                    stack.add(i);
                } else if (cmd[i] == ']') {
                    int open = stack.pop();
                    brackets.put(open, i);
                    brackets.put(i, open);
                }
            }
        } catch (Exception e) {
            throw new InvalidBracketException();
        }

        if(!stack.isEmpty()) throw new InvalidBracketException();

        return brackets;
    }

    private static class InvalidBracketException extends RuntimeException {
    }
}

```

