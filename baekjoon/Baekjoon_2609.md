# [BaekJoon#2609] 최대공약수와 최소공배수



> ### Problem
>
> https://www.acmicpc.net/problem/2609



> ### Solution

```java
import java.io.*;
import java.util.*;

class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;

        token = new StringTokenizer(br.readLine());

        int a = Integer.parseInt(token.nextToken());
        int b = Integer.parseInt(token.nextToken());

        int max = gcd(a, b);
        int min = a*b/max;

        System.out.println(max);
        System.out.println(min);

    }
    public static int gcd(int a, int b){
        if(b == 0) return a;

        return gcd(b, a%b);
    }
}
```
