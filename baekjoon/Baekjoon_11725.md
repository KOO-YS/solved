# [BaekJoon#11725] 골드바흐의 추측



> ### Problem
>
> https://www.acmicpc.net/problem/11725



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {

    // 연결된 두 정점
    static List<Integer>[] relation;
    // 방문 여부
    static boolean[] isVisited;
    // 반환할 부모값
    static int[] parents;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer token;
        int N = Integer.parseInt(br.readLine());

        relation = new ArrayList[N+1];
        for(int i=1; i<relation.length; i++){
            relation[i] = new ArrayList<>();
        }
        isVisited = new boolean[N+1];
        parents = new int[N+1];

        N--;
        while(N-->0){
            token = new StringTokenizer(br.readLine(), " ");
            int num1 = Integer.parseInt(token.nextToken());
            int num2 = Integer.parseInt(token.nextToken());

            relation[num1].add(num2);
            relation[num2].add(num1);
        }
        DFS(1);     // 루트노드 1부터 시작

        for(int i=2; i<parents.length; i++){
            System.out.println(parents[i]);
        }
    }
    
    public static void DFS(int node){
        isVisited[node] = true;
        for(int i=0; i<relation[node].size(); i++){
            int linked = relation[node].get(i);     // node와 인접한 노드
            if(!isVisited[linked]){     // 인접한 노드에 아직 접근하지 않았다면
                parents[linked] = node;
                DFS(linked);
            }
        }
    }
}
```

