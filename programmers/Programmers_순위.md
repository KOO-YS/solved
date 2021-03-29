# [Programmers] 순위



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/49191
>
> <br>
>
> ##### 참고 블로그
>
> https://velog.io/@ajufresh/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-%EC%88%9C%EC%9C%84-%EB%AC%B8%EC%A0%9C%ED%92%80%EC%9D%B4-Java



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int n, int[][] results) {
        int answer = 0;
        List<Player> players = new ArrayList<>();

        for(int i=0; i<=n; i++){
            // init
            players.add(new Player(i));
        }

        for(int[] result : results){
            players.get(result[0]).win.add(result[1]);      // 이긴 기록
            players.get(result[1]).lose.add(result[0]);     // 진 기록
        }

        for(int i=0; i<=n; i++){
            Player now = new Player(0);
            for(int j=1; j<=n; j++){
                now = players.get(i);

                // now에게 진 플레이어들의 lose -> now 보다 순위가 낮다
                Set<Integer> linkedWin = new HashSet<>();

                for(int w : now.win){
                    linkedWin.addAll(players.get(w).win);
                }

                now.win.addAll(linkedWin);      // 직접 이김 + 간접 이김 = 합침

                // now가 진 플레이어들의 win -> now 보다 순위가 높다
                Set<Integer> linkedLose = new HashSet<>();

                for(int l : now.lose){
                    linkedLose.addAll(players.get(l).lose);
                }

                now.lose.addAll(linkedLose);      // 직접 짐 + 간접 짐 = 합침

            }
        }

        for(Player p : players){
            // 높은 순위 + 낮은 순위 플레이어 수가 (n-자신)이면 정확히 순위를 가릴 수 있다
            int count = p.win.size() + p.lose.size();       

            if(count == n-1) answer++;
        }

        return answer;
    }
    class Player {
        int id;

        Set<Integer> win;
        Set<Integer> lose;

        public Player(int id) {
            this.id = id;
            win = new HashSet<>();
            lose = new HashSet<>();
        }
    }
}
```

