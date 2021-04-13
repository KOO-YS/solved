# [Programmers] 줄 서는 방법



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12936
>



> ### Solution

```java
import org.junit.Assert;
import org.junit.Test;

import java.util.*;

import static org.hamcrest.core.Is.is;
// https://programmers.co.kr/learn/courses/30/lessons/12936
public class Solution {
    @Test
    public void test() {
        Solution s = new Solution();
        Assert.assertThat(s.solution(5, 4), is(new int[]{1, 2, 4, 5, 3}));
        Assert.assertThat(s.solution(3, 5), is(new int[]{3, 1, 2}));

    }

    public int[] solution(int n, long k) {
        int[] answer = new int[n];
        int index = 0;

        List<Integer> nums = new ArrayList<>();

        long[] factorial = new long[n+1];
        factorial[0] = 1;
        for(int i=1; i<=n; i++){
            factorial[i] = factorial[i-1]*i;
            nums.add(i);
        }

        long dung = factorial[n-1];
        answer[index] = nums.remove((int) (k/dung));
        System.out.println(answer[index]+"dun?"+dung);
        index++;
        n--;
        k = k%dung;

        dung = factorial[n-1];
        answer[index] = nums.remove((int) (k/dung));
        System.out.println(answer[index]+"dun?"+dung);
        index++;

        return answer;
    }
}
```

