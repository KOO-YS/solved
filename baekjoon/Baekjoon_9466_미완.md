# [BaekJoon#9466] 텀 프로젝트



> ### Problem
>
> https://www.acmicpc.net/problem/9466

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static StringBuilder result;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;
        result = new StringBuilder();
        
        int T = Integer.parseInt(br.readLine());
        while(T-->0){
            // 학생 수
            int n = Integer.parseInt(br.readLine());
            bfs(n, br.readLine());
        }
        System.out.print(result.toString());
    }

    public static void bfs(int n, String str){
        StringTokenizer token = new StringTokenizer(str, " ");
        Student[] picks = new Student[n+1];
        for(int i=1; i<n+1; i++){
            picks[i] = new Student(i);
        }

        // 각 학생의 선택
        Queue<Integer> queue = new LinkedList<>();
        for(int i=1; i<picks.length; i++){
            int each = Integer.parseInt(token.nextToken());
            if(i != each){
                picks[each].mentioned.add(i);
            } else {
                queue.add(i);
                picks[i].checked = true;
            }
        }

        int notIncluded = 0;

        while(!queue.isEmpty()){
            int linked = queue.poll();

            List<Integer> mention = picks[linked].mentioned;
            for (Integer index : mention) {
                Student student = picks[index];
                if (!student.checked) {
                    queue.add(index);
                    picks[index].checked = true;
                    notIncluded++;
                }
            }
        }

        for(int i=1; i<picks.length; i++){
            if(!picks[i].checked) notIncluded++;
        }
        result.append(notIncluded).append("\n");
    }
}
class Student{
    int num;
    List<Integer> mentioned;
    boolean checked;

    public Student(int num) {
        this.num = num;
        this.mentioned = new ArrayList<>();
        this.checked = false;
    }
}
```



반례

```
1
6
2 3 4 5 6 2

> 1
```