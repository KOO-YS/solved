# [Programmers] 예상 대진표



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12985
>



> ### Solution

```java
class Solution
{
    public int solution(int n, int a, int b)
    {
        int answer = 1;
        int participant = n;        // 이번 라운드 참여자 수
        int winner = n/2;

        while(participant > 2){
            
            if(Math.abs(a-b) == 1 && Math.max(a, b)%2 == 0) return answer;

            // a와 b가 같은 라운드에 존재?
            int partA = (a/winner == 1 && a%winner > 0)? 2 : 1;
            int partB = (b/winner == 1 && b%winner > 0)? 2 : 1;

            a = setNextNum(a, partA, winner);
            b = setNextNum(b, partB, winner);

            participant /= 2;		// 이번 라운드에 이긴 사람 수
            winner /= 2;			// 다음 라운드에 남을 사람 수
            answer++;
        }

        return answer;
    }
    // 다음 라운드에 세팅될 참가자 번호
    public int setNextNum(int now, int part, int half){
        int next;
        next = (now%2 == 0)? now/2 : (now/2 + 1);
        if (part == 2) next += half;

        return next;
    }
}
```

<br>

> ### 오답

```java
class Solution
{
    public int solution(int n, int a, int b)
    {
        int answer = 1;
        int participant = n;        // 이번 라운드 참여자 수
        int winner = n/2;

        while(participant > 2){
            
            // ERROR !!!
            if(Math.abs(a-b) == 1) return answer;

            // a와 b가 같은 라운드에 존재?
            int partA = (a/winner == 1 && a%winner > 0)? 2 : 1;
            int partB = (b/winner == 1 && b%winner > 0)? 2 : 1;

            a = setNextNum(a, partA, winner);
            b = setNextNum(b, partB, winner);

            participant /= 2;
            winner /= 2;
            answer++;
        }

        return answer;
    }
    public int setNextNum(int now, int part, int half){
        int next;
        next = (now%2 == 0)? now/2 : (now/2 + 1);
        if (part == 2) next += half;

        return next;
    }
}
```

<br>

- ##### 반례 발견

  - n = 8, a = 2, b = 3 인 경우,
  - if(Math.abs(a-b) == 1) return answer; 에서 그냥 통과해버린다

- ##### 조건

  - 2는 1과 겨뤄야 하고, 3은 4와 겨뤄야한다
  - 2의 배수로 존재할 수 밖에 없다

- ##### 결론

  - a, b가 나란히 존재하면서 경쟁을 할려면 (홀수-> `작은 수`, 짝수-> `큰 수`)  구조를 이룰 수 밖에 없다
  - 큰 수 `Math.max(a, b)` 가 짝수여야하는 조건을 추가한다 

