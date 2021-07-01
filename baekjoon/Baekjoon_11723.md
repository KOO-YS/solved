# [BaekJoon#11723] 집합



> ### Problem
>
> https://www.acmicpc.net/problem/11723



> ### Solution

```java
import java.io.*;
import java.util.*;

class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        result = new StringBuilder();

        int M = Integer.parseInt(br.readLine());

        program = new HashSet<>();

        while(M-- >0) {
            parse(br.readLine());
        }
        System.out.print(result.toString());

    }
    
    public static Set<Integer> program;
    public static StringBuilder result;
    
    public static void parse(String input){
        StringTokenizer tokenizer = new StringTokenizer(input);

        String cmd = tokenizer.nextToken();
        int num = 0;
        if(tokenizer.hasMoreTokens()) num = Integer.parseInt(tokenizer.nextToken());
        switch (cmd){
            case "add":
                program.add(num);
                break;
            case "remove":
                program.remove(num);
                break;
            case "check":
                if (program.contains(num)) {
                    result.append("1\n");
                } else {
                    result.append("0\n");
                }
                break;
            case "toggle":
                if (program.contains(num)) {
                    program.remove(num);
                } else {
                    program.add(num);
                }
                break;
            case "all":
                program = new HashSet();
                for(int i=1; i<=20; i++) program.add(i);
                break;
            case "empty":
                program = new HashSet<>();
                break;
        }
    }
}
```
