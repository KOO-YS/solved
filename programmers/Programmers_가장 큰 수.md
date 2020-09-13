# [Programmers] 가장 큰 수



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42746



> ### Solution

```java
import java.util.Arrays;
import java.util.Comparator;

class Solution {
    public String solution(int[] numbers) {
        StringBuilder answer = new StringBuilder();

        String[] str = new String[numbers.length];

        for(int i=0; i<str.length; i++){
            str[i] = Integer.toString(numbers[i]);
        }

        Arrays.sort(str, new Comparator<String>() {
            // 조건 : 숫자를 더했을때 더 큰쪽 순으로 정렬
            @Override
            public int compare(String o1, String o2) {
                return (o2+o1).compareTo(o1+o2);
            }
        });

        // test case parameter : {0, 0, 0, 0}  
        if(str[0].equals("0")) return "0";      // -> 하나라도 0이 아닌 수가 있으면 앞에 정렬되기 때문에 0만 비교

        for(int i=0; i<str.length; i++){
            answer.append(str[i]);
        }

        return answer.toString();
    }
}
```

