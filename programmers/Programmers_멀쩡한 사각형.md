# [Programmers] 멀쩡한 사각형

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/62048



> ### Solution

```java
class Solution {
        public long solution(int w, int h) {
        long answer = (long)w*(long)h;

        long unit = GCD(w, h);

        // 한 묶음 단위당 사용할 수 없게 된 정사각형 개수 * 단위 갯수
        long count = ( (long)(w/unit) + (long)(h/unit) - 1 )*unit;
            
        answer -= count;
        return answer;
    }
    // 유클리드 호제법 : 최대 공약수
    public int GCD(int a, int b){
        if(b == 0) return a;        // 딱 나누어 떨어질때 종료
        return GCD(b, a%b);
    }
}
```
