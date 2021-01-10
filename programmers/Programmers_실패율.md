# [Programmers] 실패율 



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42889

> ### Solution

```java
import java.util.*;
// 성공 X
class Solution {
    // 클리어 X / 스테이지 도달 
    public int[] solution(int N, int[] stages) {
        int[] answer = new int[N];
        Arrays.sort(stages);

        int[] reached = new int[N+1];
        int[] passed = new int[N+1];

        List<Stage> result = new ArrayList<>();

        for(int i=0; i<stages.length; i++){
            int j = stages[i];

            int pass = 1;

            while(pass < j && pass<=N){

                reached[pass]++;
                passed[pass]++;
                pass++;
            }
            if(pass <=N) reached[j]++;
    }

        for(int i=1; i<=N; i++){
            if (reached[i] != 0) {        // 스테이지에 닿은 사람이 있다
                double failure = (reached[i] - passed[i]) / (double) reached[i];
                result.add(new Stage(i, failure));
            } else{
                result.add(new Stage(i, 1));

            }
        }
        Collections.sort(result);

        int index = 0;
        for(Stage s : result){
            answer[index++] = s.num;
        }
        return answer;
    }
    class Stage implements Comparable<Stage>{
        int num;
        double failure;

        public Stage(int num, double failure) {
            this.num = num;
            this.failure = failure;
        }

        @Override
        public int compareTo(Stage o) {
            if(this.failure == o.failure){
                if(this.num < o.num) return -1;
                else return 1;
            } else {
                if(this.failure > o.failure) return -1;
                else return 1;
            }
        }

        @Override
        public String toString() {
            return this.num+"(" +this.failure+") ";
        }
    }
}
```

