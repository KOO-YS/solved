# [BaekJoon#1966] 프린터 큐



> ### Problem
>
> https://www.acmicpc.net/problem/1966



> ### Solution 

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;
        StringBuilder result = new StringBuilder();

        int T = Integer.parseInt(br.readLine());

        while (T-- > 0) {
            tokenizer = new StringTokenizer(br.readLine());

            int N = Integer.parseInt(tokenizer.nextToken());
            int M = Integer.parseInt(tokenizer.nextToken());

            Queue<Document> printer = new LinkedList<>();
            int[] sorted = new int[N];

            tokenizer = new StringTokenizer(br.readLine());
            for (int i=0; i<N; i++) {
                sorted[i] = Integer.parseInt(tokenizer.nextToken());
                Document doc = new Document(i, sorted[i]);
                printer.add(doc);
            }

            Arrays.sort(sorted);

            int count = 0;
            boolean done = false;
            while (!done) {
                Document now = printer.poll();
                if (now.priority == sorted[N-1-count]) {
                    count++;
                    if(now.index == M) {
                        result.append(count).append('\n');
                        done = true;
                    }

                } else printer.add(now);
            }
        }
        System.out.print(result.toString());
    }
}
class Document{
    int index;
    int priority;

    public Document(int index, int priority) {
        this.index = index;
        this.priority = priority;
    }
}
```

추측 : 우선순위를 기준으로 priorityQueue로 정렬하던 중 index 순서가 섞인듯하여 priority queue 대신 배열을 이용했다

<br>



> ### Wrong

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;
        StringBuilder result = new StringBuilder();

        int T = Integer.parseInt(br.readLine());

        while (T-- > 0) {
            tokenizer = new StringTokenizer(br.readLine());

            int N = Integer.parseInt(tokenizer.nextToken());
            int M = Integer.parseInt(tokenizer.nextToken());

            Queue<Document> printer = new LinkedList<>();
            Queue<Document> priority = new PriorityQueue<>();

            tokenizer = new StringTokenizer(br.readLine());
            for (int i=0; i<N; i++) {
                Document doc = new Document(i, Integer.parseInt(tokenizer.nextToken()));
                printer.add(doc);
                priority.add(doc);
            }
            int count = 0;
            while (!printer.isEmpty()) {
                if (priority.peek().index == printer.peek().index) {
                    count++;
                    priority.poll();
                    if(M == printer.poll().index) {
                        result.append(count).append('\n');
                        break;
                    }
                } else printer.add(printer.poll());
            }
        }
        System.out.print(result.toString());
    }
    static class Document implements Comparable<Document>{
        int index;
        int priority;

        public Document(int index, int priority) {
            this.index = index;
            this.priority = priority;
        }

        @Override
        public int compareTo(Document o) {
            return o.priority - this.priority;
        }
    }
}
```



