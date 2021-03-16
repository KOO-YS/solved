# [BaekJoon#1629] 곱셈



> ### Problem
>
> https://www.acmicpc.net/problem/1629



> ### Solution
>
> ```java
> import java.io.*;
> import java.util.*;
> 
> class Main {
>     public static void main(String[] args) throws Exception {
>         BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
>         StringTokenizer token = new StringTokenizer(br.readLine(), " ");
> 
>         long A = Integer.parseInt(token.nextToken());
>         long B = Integer.parseInt(token.nextToken());
>         long C = Integer.parseInt(token.nextToken());
> 
> 
>         System.out.println(pow(A%C, B, C));
>     }
>     public static long pow(long A, long B, long C){
>         if(B == 1) return A;
> 
>         long value = pow(A, B/2, C)%C;
> 
>         // 짝수
>         if(B%2 == 0) return (value*value)%C;
>         // 홀수
>         else return (((value*value)%C)*A)%C;
>     }
> }
> ```
>
> <br>



#### [참고](https://velog.io/@hyeon930/BOJ-1629-%EA%B3%B1%EC%85%88-Java)

제곱 연산을 `O(log n)` 처리

> (제곱근이 짝수)
>
> A^10 = A^5 * A^5 



> (제곱근이 홀수)
>
> A^11 = A^5 * A^5 * A



- 짝수 :  `A^제곱수/2 * A^제곱수/2`
- 홀수 :  `A^제곱수/2 * A^제곱수/2 * 밑`