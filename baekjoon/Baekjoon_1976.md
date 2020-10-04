# [BaekJoon#1976] 여행 가자



> ### Problem
>
> https://www.acmicpc.net/problem/1976



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;
public class Main {

    public static int[] parent;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());
        int M = Integer.parseInt(br.readLine());

        // 도시의 부모 배열 init
        parent = new int[N];
        for(int i=0; i<N; i++){
            parent[i] = i;
        }

        StringTokenizer token;

        for(int i=0; i<N; i++){
            token = new StringTokenizer(br.readLine(), " ");
            for(int j=0; j<N; j++){
                int connect = Integer.parseInt(token.nextToken());
                if(connect>0){
                    // 연결되어있는 도시들의 부모를 통합
                    unionParent(i, j);
                }
            }
        }

        // 여행 계획의 속한 도시들의 부모를 담을 set
        Set<Integer> parentCount = new HashSet<>();
        token = new StringTokenizer(br.readLine(), " ");
        while(token.hasMoreTokens()){
            int par = getParent(Integer.parseInt(token.nextToken())-1);
            parentCount.add(par);
        }

        // 모든 도시들의 부모가 같다면 size 1을 반환한다
        if(parentCount.size() == 1) System.out.println("YES");
        else System.out.println("NO");
    }
    public static void unionParent(int c1, int c2){
       int p1 = getParent(c1);
       int p2 = getParent(c2);
       if(p1 < p2) {
           parent[p2] = p1;
       } else {
           parent[p1] = p2;
       }
    }

    public static int getParent(int num){
        if(parent[num] != num) return getParent(parent[num]);
        return parent[num];
    }
}
```
