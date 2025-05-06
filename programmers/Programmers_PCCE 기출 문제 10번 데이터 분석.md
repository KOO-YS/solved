# [Programmers] [PCCE 기출문제] 10번 / 데이터 분석



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/250121

> ### Solution

```java
import java.util.Arrays;
import java.util.Comparator;
import java.util.List;

class Solution {

    public final List<String> columns =  List.of("code", "date", "maximum", "remain");

    public int[][] solution(int[][] data, String ext, int val_ext, String sort_by) {
        int[][] answer = {};

        int extIndex = columns.indexOf(ext);
        int sortIndex = columns.indexOf(sort_by);

        return Arrays.stream(data)
                .filter(row -> row[extIndex] < val_ext)
                .sorted(Comparator.comparingInt(row -> row[sortIndex]))
//                .toArray(size -> new int[size][]);
                .toArray(int[][]::new);
    }
}
```

