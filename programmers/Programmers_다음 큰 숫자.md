# [Programmers] 다음 큰 숫자 



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12911

> ### Solution

```java
class Solution {
    public int solution(int n) {
        // 자연수 n의 1의 갯수
        int answer = countOne(n);

        int next = n+1;     // n+1부터 비교
        
        while(true){
            
            if(answer == countOne(next))   // 1의 갯수가 일치할 때 반환
                return next;
            
            next++;
        }
    }
    
    /** 
    * 1의 갯수 반환
    */
    public int countOne(int n){
        char[] digits = Integer.toBinaryString(n).toCharArray();
        int count = 0;
        for(char ch : digits){
            if(ch == '1') count++;
        }
        return count;
    }
}
```

