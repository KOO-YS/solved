# [BaekJoon#10866] 덱



> ### Problem
>
> https://www.acmicpc.net/problem/10866



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static Deque<Integer> deque;
    public static void main(String[] args) throws NumberFormatException, IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());

        deque = new LinkedList<Integer>();

        StringBuilder result = new StringBuilder();
        StringTokenizer token;

        while(N-->0){
            token = new StringTokenizer(br.readLine(), " ");
            if(token.countTokens()>1) commandDeque(token.nextToken(), Integer.parseInt(token.nextToken()));
            else result.append(commandDeque(token.nextToken())).append("\n");
        }
        System.out.println(result);
    }
    public static int commandDeque(String cmd){
        int result;
        switch (cmd){
            case "pop_front":
                try {
                    return deque.pollFirst();
                } catch (NullPointerException e){
                    return -1;
                }
            case "pop_back":
                try {
                    return deque.pollLast();
                } catch (NullPointerException e){
                    return -1;
                }
            case "size":
                return deque.size();
            case "empty":
                return deque.isEmpty()? 1:0;
            case "front":
                try{
                    return deque.getFirst();
                } catch (NoSuchElementException e){
                    return -1;
                }
            case "back":
                try{
                    return deque.getLast();
                } catch (NoSuchElementException e){
                    return -1;
                }
            default:
                return 0;
        }
    }
    public static void commandDeque(String cmd, int num){
        switch (cmd){
            case "push_front":
                deque.addFirst(num);
                break;
            case "push_back":
                deque.addLast(num);
                break;
        }
    }
}
```
