# [BaekJoon#1717] 집합의 표현



> ### Problem
>
> https://www.acmicpc.net/problem/1717



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer token = new StringTokenizer(br.readLine(), " ");

        int n = Integer.parseInt(token.nextToken());
        int m = Integer.parseInt(token.nextToken());

        parents = new int[n+1];

        // init
        for(int i=0; i<=n; i++){
            parents[i] = i;
        }

        StringBuilder result = new StringBuilder();
        while(m-->0){
            token = new StringTokenizer(br.readLine(), " ");
            int operator = Integer.parseInt(token.nextToken());

            if(operator == 0){
                isUnion(Integer.parseInt(token.nextToken()), Integer.parseInt(token.nextToken()));
            } else { // == 1
                int s1 = Integer.parseInt(token.nextToken());
                int s2 = Integer.parseInt(token.nextToken());

                if(getParent(s1) == getParent(s2)){
                    result.append("YES\n");
                } else {
                    result.append("NO\n");
                }
            }
        }
        // print answer
        System.out.println(result.toString());
    }

    public static int[] parents;

    public static void isUnion(int s1, int s2){
        int p1 = getParent(s1);
        int p2 = getParent(s2);
        if(p1<p2){
            parents[p2] = p1;
        } else {
            parents[p1] = p2;
        }
    }

    public static int getParent(int num){
        if(parents[num] != num) return getParent(parents[num]);
        return parents[num];
    }
}

```
