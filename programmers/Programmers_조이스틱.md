# [Programmers] 조이스틱

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42860



> ### Solution

```java
class Solution {
    public int solution(String name) {
        int answer = 0;

        int length = name.length();

        // 총 길이(최댓값)로 초기화
        int min = length-1;

        for(int i=0; i<length; i++) {
            answer += Math.min(name.charAt(i)-'A', 'Z'-name.charAt(i)+1);

            int next = i+1; // 다음 인덱스부터

            // A가 계속 될동안 갯수 카운트
            while(next<length && name.charAt(next) == 'A') {
                next++;
            }
            min = Math.min(min, i+(length-next)+ i);
        }

        answer += min;

        return answer;
    }
}
```

