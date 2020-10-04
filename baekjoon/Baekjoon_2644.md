# [BaekJoon#2644] 촌수 계산



> ### Problem
>
> https://www.acmicpc.net/problem/2644

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        // 전체 사람의 수
        int n = Integer.parseInt(br.readLine());

        StringTokenizer token = new StringTokenizer(br.readLine(), " ");
        int person1 = Integer.parseInt(token.nextToken());      // 촌수 계산 기준
        int person2 = Integer.parseInt(token.nextToken());      // 촌수 계산 대상

        List<Integer>[] family = new LinkedList[n+1];
        int[] isVisited = new int[n+1];
        for(int i=1; i<family.length; i++){
            family[i] = new LinkedList<>();
        }

        // 부모 자식들 간의 관계 개수
        int m = Integer.parseInt(br.readLine());

        while(m-->0){
            token = new StringTokenizer(br.readLine(), " ");
            int p1 = Integer.parseInt(token.nextToken());
            int p2 = Integer.parseInt(token.nextToken());

            family[p1].add(p2);
            family[p2].add(p1);
        }

        int answer = bfs(family, isVisited, person1, person2);
        System.out.println(answer);

    }
    public static int bfs(List<Integer>[] family, int[] isVisited, int person1, int person2){

        Queue<Integer> queue = new LinkedList<>();
        queue.add(person1);     // 기준부터 시작
        isVisited[person1] = 0;

        while(!queue.isEmpty()){
            int thatPerson = queue.poll();
            if(thatPerson == person2){
                return isVisited[person2];
            }

            for(int i=0; i<family[thatPerson].size(); i++){
                int connect = family[thatPerson].get(i);
                if(isVisited[connect] == 0) {           // 아직 방문하지 않은 사람만 접근
                    queue.add(connect);
                    isVisited[connect] = isVisited[thatPerson]+1;
                }
            }
        }

        return -1;
    }
}
```
