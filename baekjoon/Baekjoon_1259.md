# [BaekJoon#1259] 팰린드롬수



> ### Problem
>
> https://www.acmicpc.net/problem/1259



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Deque;
import java.util.LinkedList;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();
        String input;
        while(!(input = br.readLine()).equals("0")){
            result.append(palindrome(input)).append("\n");
        }

        System.out.print(result.toString());
    }
    
    public static String palindrome(String str){
        boolean isSymmetry = true;

        Deque<Character> sequence = new LinkedList<>();
        for(char c : str.toCharArray()){
            sequence.add(c);
        }
        while(sequence.size() >= 2){
            if(sequence.pollFirst() != sequence.pollLast()){
                isSymmetry = false;
            }
        }
        return isSymmetry? "yes":"no";
    }
}
```
