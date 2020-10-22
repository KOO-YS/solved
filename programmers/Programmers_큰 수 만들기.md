# [Programmers] 큰 수 만들기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42883



> ### Solution

```java
class Solution {
    public String solution(String number, int k) {
        char[] ch = number.toCharArray();
        StringBuilder answer = new StringBuilder();

        int index = 0;
        for(int i=0; i<ch.length-k; i++){
            char max = '0';
            for(int j=index; j<i+k+1; j++){
                if(max < ch[j]){
                    max = ch[j];
                    index = j+1;
                }
            }
            answer.append(max);

        }

        return answer.toString();
    }
}
```
