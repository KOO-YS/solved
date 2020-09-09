# [Programmers] 기능 개발



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42586



> ### Solution

```java
import java.util.*;

class Solution {
    public int[] solution(int[] progresses, int[] speeds) {

        Queue<Integer> deploy = new LinkedList<>();

        int days;           // 기능별 개발일자

        for(int i=0; i<progresses.length; i++){
            // 깔끔하게 나누어 지지 않는 날이면 하루 더 추가
            days = ((100-progresses[i])%speeds[i]==0)? 
                (100-progresses[i])/speeds[i] : (100-progresses[i])/speeds[i]+1;
            deploy.offer(days);
        }

        List<Integer> functions = new ArrayList<>();

        int count = 1;                      // 배포 갯수
        int front = deploy.poll();          // 배포를 시작할 기능의 개발일수
        int next;
        while(!deploy.isEmpty()){
            next = deploy.poll();
            if(front >= next){
                count ++;
            } else {
                front = next;
                functions.add(count);
                count = 1;
            }
        }
        functions.add(count);

        return convertIntArray(functions);
    }

    // 리스트 -> 정수 배열로 변환
    public int[] convertIntArray(List<Integer> list){
        int[] array = new int[list.size()];
        for(int i=0; i<array.length; i++){
            array[i] = list.get(i).intValue();
        }
        return array;
    }
}
```

