# [Programmers] 이진 변환 반복하기

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/70129



> ### Solution

```java
class Solution {
    public int[] solution(String s) {
        StringBuilder str = new StringBuilder(s);
        int zero = 0;
        int one;
        int count = 0;
        while(str.length() > 1) {
            one = 0;
            for (char ch : str.toString().toCharArray()) {
                // 0을 제거 & 1만 담기
                if(ch == '1') one++;
                else zero++;
            }
            // 1의 갯수를 이진수로 변환
            str = new StringBuilder(Integer.toBinaryString(one));
            count++;
        }
        return new int[]{count, zero};
    }
}
```

