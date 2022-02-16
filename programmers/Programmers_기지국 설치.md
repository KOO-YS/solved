# [Programmers] 기지국 설치

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12979



> ### Solution

```java
class Solution {
    /**
    *
    * @param n 나열된 아파트 개수
    *  -> { 200,000,000 이하의 자연수 }
    * @param stations 이미 설치되어 있는 아파트 기지국
    *  -> { 오름차순 정렬 / N보다 같거나 작은 수 / 10,000 이하의 크기 }
    * @param w 기지국 양쪽으로 퍼지는 전파 길이
    *  -> {10,000 이하의 자연수}
    *
    * @return 추가 설치해야 하는 기지국 수
    */
    public int solution(int n, int[] stations, int w) {
        int answer = 0;

        int search = 1;
        int i = 0;
        int waveLength = 2 * w + 1;

        while (search <= n) {
            if (i < stations.length && search >= stations[i]-w) {    // 탐색 포인트가 전파망 안에 있다
                search = stations[i] + w + 1;
                i++;
            }
            else {    // 새 기지국 추가
                answer++;
                search += waveLength;
            }
        }

        return answer;
    }
}
```

