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
    public static int N;
    public static int K;

    public static int[] isVisited = new int[100001];
    public static int[] parents = new int[100001];

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer token = new StringTokenizer(br.readLine()," ");

        N = Integer.parseInt(token.nextToken());
        K = Integer.parseInt(token.nextToken());

        findFastRoute();
        printRoute();
    }

    public static void findFastRoute(){

        Queue<Integer> route = new LinkedList<>();
        route.add(N);
        isVisited[N] = 1;       // 시작점

        while(!route.isEmpty()){
            int X = route.poll();

            if(X == K) return;

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
    }
    public static boolean isBoundary(int num){
        if( num <0 || num >100000 ) return false;
        return true;
    }

    public static void printRoute(){
        StringBuilder route = new StringBuilder();

        route.append(isVisited[K]-1+"\n");

        Stack<Integer> reverse = new Stack<>();

        reverse.push(K);
        int parent = K;
        while (parent != N){
            reverse.push(parents[parent]);
            parent = parents[parent];
        }

        while(!reverse.isEmpty()){
            route.append(reverse.pop()+" ");
        }
        System.out.println(route.toString());
    }

}
```





##### 시간 초과 해결 

---

`오답`

```java
reverse.push(K);
int parent = parents[K];

while (parent != N){
	reverse.push(parent);
	parent = parents[parent];

}
reverse.push(N);
```

-> K 와 N을 비교하지 않는다

 N와 K가 같을 경우를 비교하지 못한다



`정답`

```java
reverse.push(K);
int parent = K;
while (parent != N){
    reverse.push(parents[parent]);
    parent = parents[parent];
}
```

-> K N이 같을 경우도 비교가 가능하다 