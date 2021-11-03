# [Programmers] 피로도



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/87946

<br>

> ### solution (코드 정리)

```java
class Solution {
    public boolean[] visit;
    public int MAX;

    public int solution(int k, int[][] dungeons) {

        visit = new boolean[dungeons.length];
        MAX = 0;

        for (int i=0; i<dungeons.length; i++) {
            dfs(k, visit, dungeons);
        }
        return MAX;
    }

    public void dfs(int k, boolean[] visit, int[][] dungeons) {
        boolean noWhereToGo = true;
        int size = dungeons.length;

        for (int i=0; i<size; i++) {
            if (!visit[i] && k >= dungeons[i][0]) {
                noWhereToGo = false;
                k -= dungeons[i][1];
                visit[i] = true;
                dfs(k, visit, dungeons);
                // back tracking
                k += dungeons[i][1];
                visit[i] = false;
            }
        }

        if (noWhereToGo) {
            int count = size;
            for (int i=0; i<size; i++) {
                if (!visit[i]) count--;
            }
            MAX = Math.max(MAX, count);
        }
    }
}
```

<br>

> ### solution

```java
public boolean[] visit;
public int MAX;

public int solution(int k, int[][] dungeons) {
    int answer = -1;

    visit = new boolean[dungeons.length];
    MAX = 0;

    for (int i=0; i<dungeons.length; i++) {
        if (k >= dungeons[i][0]) {      // 최소 필요
            visit[i] = true;
            k -= dungeons[i][1];
            dfs(k, visit, dungeons);
            // back-tracking
            visit[i] = false;
            k += dungeons[i][1];
        }
    }
    return MAX;
}

public void dfs(int k, boolean[] visit, int[][] dungeons) {
    boolean noWhereToGo = true;
    int size = dungeons.length;

    for (int i=0; i<size; i++) {
        if (!visit[i] && k >= dungeons[i][0]) {
            noWhereToGo = false;
            k -= dungeons[i][1];
            visit[i] = true;
            dfs(k, visit, dungeons);
            // back tracking
            k += dungeons[i][1];
            visit[i] = false;
        }
    }

    if (noWhereToGo) {
        int count = size;
        for (int i=0; i<size; i++) {
            if (!visit[i]) count--;
        }
        MAX = Math.max(MAX, count);
    }
}
```
