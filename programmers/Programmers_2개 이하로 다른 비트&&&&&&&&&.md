# [Programmers] 2개 이하로 다른 비트



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/77885

<br>

> ### solution

```java

```

<br>

> ##### 오답
>
> ```java
> class Solution {
>     public long[] solution(long[] numbers) {
>         long[] answer = new long[numbers.length];
> 
>         for(int i=0; i<numbers.length; i++){
>             answer[i] = compare(numbers[i]);
>         }
>         return answer;
>     }
> 
>     public long compare(long n){
>         int count = Integer.MAX_VALUE;
>         int m = (int)n;
>         char[] Nbin = Integer.toBinaryString((int)n).toCharArray();
>         while(count > 2){
>             count = 0;
>             m++;
>             char[] Mbin = Integer.toBinaryString(m).toCharArray();
>             int Nlen = Nbin.length - 1;
>             int Mlen = Mbin.length - 1;
>             while(Nlen>=0) {
>                 if (Mbin[Mlen--] != Nbin[Nlen--]) count++;
> 
>                 if(count>2) break;
>             }
>             count += (Mbin.length - Nbin.length);
> 
>         }
>         return m;
>     }
> }
> ```
