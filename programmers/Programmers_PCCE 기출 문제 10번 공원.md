# [Programmers] [PCCE 기출문제] 10번 / 공원



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/340198

> ### Solution

```java
import java.util.*;


class Solution {
    public int solution(int[] mats, String[][] park) {
        int answer = -1;
        Arrays.sort(mats);
        
        // reverse
        for (int i=mats.length - 1; i>=0; i--) {
            
            int m = mats[i];
            // park
            for (int x=0; x<=park.length-m; x++) {
                for (int y=0; y<=park[0].length-m; y++) {
                    boolean available = true;
                    // mats
                    for (int w=x; w<x+m; w++) {
                        for (int h=y; h<y+m; h++) {
                            if (!park[w][h].equals("-1")) {
                                available = false;
                                break;
                            }
                        }
                    }
                    if (available)
                        return m;          
                }
            }         
        }
        return answer;
    }
}
```

