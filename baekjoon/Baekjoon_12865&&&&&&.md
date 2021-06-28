# [BaekJoon#12865] 평범한 배낭



> ### Problem
>
> https://www.acmicpc.net/problem/12865



> ### Solution
>
> <br>
>
> [참고 블로그](https://st-lab.tistory.com/141)
>
> ###### Knapsack 알고리즘
>
> 배낭에 넣을 수 있는 최댓값이 정해지고 해당 한도 물건을 넣어 가치의 합이 최대가 되도록 고르는 방법을 찾음 -> 조합 최적화
>
> - ###### 분류
>
>   - 짐을 쪼갤 수 있는 경우
>
>     - 그리디 알고리즘
>
>   - 짐을 쪼갤 수 없는 경우
>
>     - DP 알고리즘
>
>     > :bulb: 지금 경우는 짐을 쪼갤 수 없으므로 DP 사용

```java
import java.io.*;
import java.util.*;

//https://www.acmicpc.net/problem/5430
class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;

        token= new StringTokenizer(br.readLine());

        int N = Integer.parseInt(token.nextToken());
        int K = Integer.parseInt(token.nextToken());

        weight = new int[N];
        value = new int[N];

        for(int i=0; i<N; i++){
            token = new StringTokenizer(br.readLine());

            weight[i] = Integer.parseInt(token.nextToken());
            value[i] = Integer.parseInt(token.nextToken());
        }

        dp = new int[N][K+1];

        int answer = knapsack(N-1, K);
        System.out.println(answer);

    }
    public static int[][] dp;
    public static int[] weight;
    public static int[] value;

    public static int knapsack(int i, int k){

        if(i<0) return 0;

        // 탐색하지 않은 위치
        if(dp[i][k] == 0) {
            
            // i번째 물건을 추가로 담지 못하는 경우
            if(weight[i] > k) {
                dp[i][k] = knapsack(i-1, k);
            }
            // i번째 물건을 추가로 담을 수 있는 경우
            else {
                dp[i][k] = Math.max(
                        // i-1번째 값에 대한 값
                        knapsack(i-1, k),
                        // i가 추가된 값
                        knapsack(i-1, k-weight[i]) + value[i]);
            }
        }
        return dp[i][k];
    }
}
```



> ##### 메모리 초과
>
> ```java
> import java.io.*;
> import java.util.*;
> 
> class Main {
>     public static int N;
>     public static int K;
> 
>     public static List<Bag> bags;
>     public static Queue<Bag> packing;
> 
>     public static void main(String[] args) throws Exception {
>         BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
>         StringTokenizer token;
> 
>         token = new StringTokenizer(br.readLine());
>         N = Integer.parseInt(token.nextToken());
>         K = Integer.parseInt(token.nextToken());
> 
>         bags = new ArrayList<>();
>         packing = new PriorityQueue<>();
>         for(int i=0; i<N; i++){
>             token = new StringTokenizer(br.readLine());
>             int W = Integer.parseInt(token.nextToken());
>             int V = Integer.parseInt(token.nextToken());
> 
>             if(W <= K){      // 무게가 덜 나가면서
>                 packing.add(new Bag(W, V));   // 좀 더 많은 가치 패킹
> 
>                 bags.add(new Bag(W, V));
>             }
>         }
>         Bag now;
>         for(int i = 0; i<bags.size(); i++){
>             now = bags.get(i);
>             for(int j = i+1; j<bags.size(); j++){
>                 add(j, now);
>             }
>         }
> 
>         System.out.println(packing.peek().value);
>     }
>     public static void add(int index, Bag now){
>         if(now.weight > K || index >= bags.size()) return;
>         for(int i = index; i<bags.size(); i++){
>             Bag next = bags.get(i);
>             if(now.weight + next.weight <= K){
>                 packing.add(new Bag(now.weight+next.weight, now.value+next.value));
> 
>                 add(i+1, new Bag(now.weight+next.weight, now.value+next.value));
>             }
>         }
>     }
>     static class Bag implements Comparable<Bag>{
>         int weight;
>         int value;
> 
>         public Bag(int weight, int value){
>             this.weight = weight;
>             this.value = value;
>         }
> 
>         @Override
>         public int compareTo(Bag o) {
>             return o.value - this.value;
>         }
>     }
> }
> ```
