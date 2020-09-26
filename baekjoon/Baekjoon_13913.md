# [BaekJoon#13913] 숨바꼭질 4



> ### Problem
>
> https://www.acmicpc.net/problem/13913



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

        StringTokenizer token = new StringTokenizer(br.readLine()," ");

        N = Integer.parseInt(token.nextToken());
        K = Integer.parseInt(token.nextToken());

        // 경로가 커질지 작아질지 알 수 없기 때문에 전체 범위로 초기화
        isVisited = new int[100001];            
        parents = new int[100001];

        String answer = findFastRoute();
        System.out.println(answer);

    }

    public static int N;
    public static int K;

    public static int[] isVisited;
    public static int[] parents;

    public static String findFastRoute(){
        StringBuffer result = new StringBuffer();

        Queue<Integer> route = new LinkedList<>();
        route.add(N);
        isVisited[N] = 0;       // 시작점

        while(!route.isEmpty()){
            int X = route.poll();

            if(isVisited[K] != 0){
                int parent = parents[K];

                while(parent != -1){
                    result.insert(0, parent+" ");
                    parent = parents[parent];
                }
                result.insert(0, N+" ");        // 시작값
                result.append(K);                         // 도착값

                // 전체 루트
                result.insert(0, isVisited[K]+"\n");
                return result.toString();
            }
            /*
                case 1. (X-1)
                case 2. (X+1)
                case 3. 2X
            */
            if(isBoundary(X-1) && isVisited[X - 1] == 0){           // Case 1
               route.add(X-1);
               isVisited[X-1] = isVisited[X]+1;
               parents[X-1] = X;
            }

            if(isBoundary(X+1) && isVisited[X + 1] == 0){           // Case 2
                route.add(X+1);
                isVisited[X+1] = isVisited[X]+1;
                parents[X+1] = X;
            }
            if(isBoundary(X*2) && isVisited[X*2] == 0){             // Case 3
                route.add(2*X);
                isVisited[2*X] = isVisited[X]+1;
                parents[2*X] = X;
            }

        }
        return result.toString();
    }

    public static boolean isBoundary(int num){
        if( num <0 || num >100000 ) return false;
        return true;
    }
}

```
