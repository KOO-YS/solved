# [Programmers] [PCCE 기출문제] 1번 / 동영상 재생기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/340213

> ### Solution

```java
import java.util.*;
import java.time.*;

class Solution {
    public Duration getDuration(String strTime) {
        String[] timeSplit = strTime.split(":");
        return Duration.ofMinutes(Long.parseLong(timeSplit[0]))
                .plusSeconds(Long.parseLong(timeSplit[1]));

    }

    final Duration jump = Duration.ofMinutes(0).plusSeconds(10);

    public String solution(String video_len, String pos, String op_start, String op_end, String[] commands) {
        Duration posDuration = getDuration(pos);

        Duration opStartDuration = getDuration(op_start);
        Duration opEndDuration = getDuration(op_end);
        Duration videoDuration = getDuration(video_len);

        if (opStartDuration.compareTo(posDuration) <= 0 && opEndDuration.compareTo(posDuration) > 0) {
            posDuration = opEndDuration;
        }

        for (String command : commands) {
            if (opStartDuration.compareTo(posDuration) <= 0 && opEndDuration.compareTo(posDuration) > 0) {
                posDuration = opEndDuration;
            }
            switch (command) {
                case "next":
                    posDuration = posDuration.plus(jump);

                    if (posDuration.compareTo(videoDuration) > 0)
                        posDuration = videoDuration;
                    break;
                case "prev":
                    if (posDuration.minus(jump).isNegative())
                        posDuration = Duration.ZERO;
                    else posDuration = posDuration.minus(jump);
                    break;
            }
        }
        if (opStartDuration.compareTo(posDuration) <= 0 && opEndDuration.compareTo(posDuration) > 0) {
            posDuration = opEndDuration;
        }
        return String.format("%02d:%02d", posDuration.toMinutesPart(), posDuration.toSecondsPart());
    }
}
```


### Solution - Code Refactoring
```java
import java.util.*;
import java.time.*;

class Solution {
    public Duration getDuration(String strTime) {
        String[] timeSplit = strTime.split(":");
        return Duration.ofMinutes(Long.parseLong(timeSplit[0]))
                .plusSeconds(Long.parseLong(timeSplit[1]));
    }

    private Duration skipOpening(Duration pos, Duration opStart, Duration opEnd) {
        return (opStart.compareTo(pos) <= 0 && opEnd.compareTo(pos) > 0) ? opEnd : pos;
    }

    final Duration JUMP = Duration.ofMinutes(0).plusSeconds(10);

    public String solution(String video_len, String pos, String op_start, String op_end, String[] commands) {
        Duration posDuration = getDuration(pos);

        Duration opStart = getDuration(op_start);
        Duration opEnd = getDuration(op_end);
        Duration videoDuration = getDuration(video_len);

        posDuration = skipOpening(posDuration, opStart, opEnd);

        for (String command : commands) {
            switch (command) {
                case "next":
                    posDuration = posDuration.plus(JUMP);

                    if (posDuration.compareTo(videoDuration) > 0)
                        posDuration = videoDuration;
                    break;
                case "prev":
                    if (posDuration.minus(JUMP).isNegative())
                        posDuration = Duration.ZERO;
                    else posDuration = posDuration.minus(JUMP);
                    break;
            }
            posDuration = skipOpening(posDuration, opStart, opEnd);
        }

        return String.format("%02d:%02d", posDuration.toMinutesPart(), posDuration.toSecondsPart());
    }
}
```