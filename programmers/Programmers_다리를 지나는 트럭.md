# [Programmers] 다리를 지나는 트럭

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42583



> ### Solution

```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public int solution(int bridge_length, int weight, int[] truck_weights) {
        int answer = 0;

        Queue<Truck> trucks = new LinkedList<>();
        Queue<Truck> removes = new LinkedList<>();       // 다리 위에서 제거해야할 트럭 리스트

        int size = 0;
        for(int truckWeight : truck_weights){
            trucks.add(new Truck(truckWeight));
        }

        while(!trucks.isEmpty() || !removes.isEmpty()){
            answer++;
            if(!removes.isEmpty()){
                Truck r = removes.peek();
                if(answer - r.start >= bridge_length){     // 트럭이 다리의 길이만큼 머물었다면
                    size -= r.weight;
                    removes.poll();
                }
            }
            if(!trucks.isEmpty()){
                Truck t = trucks.peek();
                if(size + t.weight <= weight ){         // 다리 진입
                    size += t.weight;
                    removes.add(new Truck(trucks.poll().weight, answer));       // 제거 리스트에 삽입
                }
            }
        }
        return answer;
    }

}
class Truck {
    int weight;
    int start;

    public Truck(int weight) {
        this.weight = weight;
        this.start = 0;
    }

    public Truck(int weight, int start) {
        this.weight = weight;
        this.start = start;
    }
}
```

