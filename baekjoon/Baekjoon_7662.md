# [BaekJoon#7662] 이중 우선순위 큐



> ### Problem
>
> https://www.acmicpc.net/problem/7662



> ### Solution

```java

```

<br>



> ### 오답 -> 시간초과 1

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {

    public static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    public static StringTokenizer tokenizer;
    public static void main(String[] args) throws Exception {
        StringBuilder result = new StringBuilder();

        int T = Integer.parseInt(br.readLine());
        int k;
        int[] arr;
        while (T-- > 0) {
            k = Integer.parseInt(br.readLine());
            if((arr = operate(k)) == null) {
                result.append("EMPTY");
            } else result.append(arr[0]).append(' ').append(arr[1]);
            result.append('\n');
        }
        System.out.print(result.toString());
    }

    public static int[] operate(int k) throws IOException {
        Queue<Integer> p = new PriorityQueue<>();
        Deque<Integer> queue = new ArrayDeque<>();

        char cmd;
        int num;
        while (k-- >0) {
            tokenizer = new StringTokenizer(br.readLine());
            cmd = tokenizer.nextToken().charAt(0);
            num = Integer.parseInt(tokenizer.nextToken());

            if (cmd == 'D') {
                if(num > 0)
                    queue.pollLast();
                else
                    queue.pollFirst();
            } else {
                queue.add(num);

                p.clear();
                p.addAll(queue);

                queue.clear();
                queue.addAll(p);
            }
        }

        return queue.isEmpty()? null : new int[]{queue.peekFirst(), queue.peekLast()};
    }
}
```



<br>



> ### 오답 -> 시간초과 2

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {

    public static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    public static StringTokenizer tokenizer;
    public static void main(String[] args) throws Exception {
        StringBuilder result = new StringBuilder();

        int T = Integer.parseInt(br.readLine());
        int k;

        while (T-- >0) {        // Each Test Case
            k = Integer.parseInt(br.readLine());
            result.append(operate(k)).append('\n');
        }
        System.out.print(result.toString());
    }

    public static String operate(int k) throws IOException {

        PriorityQueue<Integer> min = new PriorityQueue<>();
        PriorityQueue<Integer> max = new PriorityQueue<>(Comparator.reverseOrder());

        char op;
        int num;
        int delete;
        while (k-- > 0) {   // Each operation
            tokenizer = new StringTokenizer(br.readLine());

            op = tokenizer.nextToken().charAt(0);
            num = Integer.parseInt(tokenizer.nextToken());
            if (op == 'I') {
                min.add(num);
                max.add(num);
            }
            else {
                if (max.size() == 0) continue;  // 값이 없으면 넘긴다
                if (num > 0) {  // delete MAX
                    delete = max.poll();
                    min.remove(delete);     // 끝 값에서 꺼낸 값을 'value' 의미로써 삭제
                } else {        // delete MIN
                    delete = min.poll();
                    max.remove(delete);     // 끝 값에서 꺼낸 값을 'value' 의미로써 삭제


                }
            }
        }
        if (min.size() >= 1) return max.peek()+" "+min.peek();
        return "EMPTY";
    }
}
```
