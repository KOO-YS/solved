# [Programmers] 지폐 접기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/340199



> ### Solution

```java
class Solution {
    
    public int solution(int[] wallet, int[] bill) {
        int answer = 0;

        int temp = Math.min(wallet[0], wallet[1]);
        wallet[0] = Math.max(wallet[0], wallet[1]);
        wallet[1] = temp;

        temp = Math.min(bill[0], bill[1]);
        bill[0] = Math.max(bill[0], bill[1]);
        bill[1] = temp;

        int longSide = 0;
        int shortSide = 0;

        while (!(bill[0] <= wallet[0] && bill[1] <= wallet[1])) {
            longSide = Math.max(bill[0]/2, bill[1]);
            shortSide = Math.min(bill[0]/2, bill[1]);

            bill[0] = longSide;
            bill[1] = shortSide;

            answer ++;

        }
        return answer;
    }
}
```

### Refactoring
```java
class Solution {
    
    public int solution(int[] wallet, int[] bill) {
        int answer = 0;

        while (!(min(bill) <= min(wallet) && max(bill) <= max(wallet))) {
            bill = new int[]{max(bill)/2, min(bill)};
            answer ++;
        }
        return answer;
    }

    public int min(int[] arr) {
        return Math.min(arr[0], arr[1]);
    }

    public int max(int[] arr) {
        return Math.max(arr[0], arr[1]);
    }
}
```