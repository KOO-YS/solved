# [BaekJoon#12865] 평범한 배낭



> ### Problem
>
> https://www.acmicpc.net/problem/12865



> ### Solution

```java

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
