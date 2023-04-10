# [Programmers] 추억 점수



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/176963

> ### Solution

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int[] solution(String[] name, int[] yearning, String[][] photo) {
        int[] answer = new int[photo.length];

        Map<String, Integer> yearningMap = new HashMap<>();

        for (int i=0; i< name.length; i++) {
            yearningMap.put(name[i], yearning[i]);
        }

        String[] eachPhoto;
        for (int i=0; i<photo.length; i++) {
            eachPhoto = photo[i];
            for (int j=0; j<eachPhoto.length; j++) {
                answer[i] += yearningMap.getOrDefault(eachPhoto[j], 0);

            }
        }
        return answer;
    }
}
```

