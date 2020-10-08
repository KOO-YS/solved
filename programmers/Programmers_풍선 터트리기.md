# [Programmers] 풍선 터트리기

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/68646



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int[] a) {
        HashSet <Integer> possible = new HashSet<Integer>();
        int min = a[0];     // init
        for (int i = 1; i < a.length; i++) {
            possible.add(min);
            min = Math.min(a[i], min);      // 왼쪽부터 비교 후 가장 작은 값이 될 수 있다면 (오른쪽에 가장 작은 값이 있어도 상관 없이) 끝까지 남을 수 있다
        }
        min = a[a.length-1];  // init
        for (int i = a.length-2; i >= 0; i--) {
            possible.add(min);
            min = Math.min(a[i], min);      // 오른쪽부터 비교 후 가장 작은 값이 될 수 있다면 (왼쪽에 가장 작은 값이 있어도 상관 없이) 끝까지 남을 수 있다
        }
        return possible.size();
    }
}
```







> ###  오답

```java
/*
*
*
*
*     시 간 초 과
*
*
*
*/

import java.util.*;

class Solution {
    public int solution(int[] a) {
        int answer = 0;

        for(int i : a){
            if(isPossible(a, i)) answer++;
        }
        return answer;
    }
    public boolean isPossible(int[] a, int pick){
        int chance = 1;
        Deque<Integer> compare = new LinkedList<>();
        for(int i : a){
            compare.add(i);
        }
        int x, y;
        while(true){        // 뒤에서 확인

            // 비교할 두 값을 꺼낸다 -> 그 중 pick이 있으면 break
            if(compare.getLast() != pick) {
                x = compare.pollLast();
                if (compare.getLast() != pick) y = compare.pollLast();
                else {
                    compare.addLast(x);
                    break;
                }
            } else break;

            compare.addLast(Math.min(x,y));
        }

        while(true){        // 앞에서 확인
            if(compare.getFirst() != pick){
                x = compare.pollFirst();
                if(compare.getFirst() != pick) y = compare.pollFirst();
                else {
                    compare.addFirst(x);
                    break;
                }
            } else break;

            compare.addFirst(Math.min(x,y));
        }
        // 2개밖에 안 남으면 비교할 필요 없이 chance 써서 바로 가능

        // 3개가 남았을때 가장 pick이 가장 크다면 실패
        if(compare.size() == 3){
            int[] sorted = new int[3];
            for(int i=0; i<sorted.length; i++){
                sorted[i] = compare.pollFirst();
            }
            Arrays.sort(sorted);
            if(sorted[2] == pick) return false;
        }
        return true;
    }
}
```

```java
/*
*
*
*
*     또 다른 시 간 초 과
*
*
*
*/

import java.util.*;

class Solution {
    public int solution(int[] a) {
        int answer = 0;

        int index = 0;
        for(int i : a){
            if(isPossible(a, i, index++)) {
                answer++;
            }
        }
        return answer;
    }
    public boolean isPossible(int[] a, int pick, int index){
        int front = Integer.MAX_VALUE;
        int back = Integer.MAX_VALUE;
        if(index >= 1){
            for(int i=0; i<index; i++){
                if(a[i] < front) front = a[i];
            }
        }
        if(a.length - index >= 2){
            for(int i= index+1; i<a.length; i++){
                if(a[i] < back) back = a[i];
            }
        }
        int[] sorted = new int[]{front, back, pick};
        Arrays.sort(sorted);
        if(sorted[2] == pick) return false;
        return true;
    }
}
```



