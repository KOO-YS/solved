# [Programmers] PCCE 기출 문제 1번 붕대 감기

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/250137

<br>

> ### solution

```javaimport java.util.*;

class Solution {
    public int solution(int[] bandage, int health, int[][] attacks) {
        int answer = 0;
        
        int hp = health;
        int attackIndex = 0;
        int nonStop = 1;
        for (int i=0; i<=attacks[attacks.length - 1][0]; i++) {
            if (hp <= 0 || attackIndex >= attacks.length)
                return -1;
            else if (i == attacks[attackIndex][0]) {
                hp -= attacks[attackIndex][1];
                attackIndex ++;
                nonStop = 1;
            } else if (hp == health)
                continue;
            else {
                if (nonStop == bandage[0]) {
                    hp = Math.min(health, hp+=bandage[2]);
                    nonStop = 1;
                } else 
                    nonStop ++;
                hp = Math.min(health, hp+=bandage[1]);
            }
            
        }
        return (hp==0)? -1: hp;
    }
}
```
