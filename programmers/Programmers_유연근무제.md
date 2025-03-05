# [Programmers] 유연근무제



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/388351



> ### Solution

```java
class Solution {
    
    public final int WEEK = 7;

    public int solution(int[] schedules, int[][] timelogs, int startday) {
        int answer = 0;

        for (int i = 0; i<schedules.length; i++) {
            answer += isEmployeeToReceivePrize(schedules[i], timelogs[i], startday);
        }
        return answer;
    }

    /**
    * 각 직원 별 출근시간 준수 여부 확인
    */
    public int isEmployeeToReceivePrize(int schedule, int[] timelogs, int startday) {
        int changedSchedule = changedTimeUnit(schedule) + 10;
        int changedTimelog;
        for (int i = 0; i < WEEK; i++) {
            if (startday < 6) {
                changedTimelog = changedTimeUnit(timelogs[i]);
                if (changedSchedule < changedTimelog)
                    return 0;
            }   
            startday ++;
            if (startday == 8) {
                startday = 1;
            }
        }
        return 1;
    }

    public int changedTimeUnit(int time) {
        return (time / 100) * 60 + (time % 100);
    }
}
```
- startday 에 대한 조건문을 확인 로직 뒤로 보냄


> ### 오답

```java
class Solution {
    
    public final int WEEK = 7;

    public int solution(int[] schedules, int[][] timelogs, int startday) {
        int answer = 0;

        for (int i = 0; i<schedules.length; i++) {
            answer += isEmployeeToReceivePrize(schedules[i], timelogs[i], startday);
        }
        return answer;
    }

    /**
    * 각 직원 별 출근시간 준수 여부 확인
    */
    public int isEmployeeToReceivePrize(int schedule, int[] timelogs, int startday) {
        int changedSchedule = changedTimeUnit(schedule) + 10;
        int changedTimelog;
        for (int i = 0; i < WEEK; i++) {
            if (startday == 6 || startday == 7) {
                i += (8 - startday); // startday가 6이면 2 증가, 7이면 1 증가
                startday = 1;
            } else {
                changedTimelog = changedTimeUnit(timelogs[i]);
                if (changedTimelog > changedSchedule)
                    return 0;
                startday ++;
            }
        }
        return 1;
    }

    public int changedTimeUnit(int time) {
        return (time / 100) * 60 + (time % 100);
    }
}
```
- 주말이면 index i값을 조절하였으나, i가 WEEK 범위를 넘어서는 경우가 존재해보임 
