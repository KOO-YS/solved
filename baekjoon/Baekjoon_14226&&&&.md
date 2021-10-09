# [BaekJoon#14226] 이모티콘



> ### Problem
>
> https://www.acmicpc.net/problem/14226


> ### Solution (WRONG)

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

// https://www.acmicpc.net/problem/14226
public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int S = Integer.parseInt(br.readLine());

        // 방문 여부
        visited = new boolean[MAX][MAX];    // emoji, clipboard

        Queue<Screen> queue = new LinkedList<>();
        // 초기값 : emoji
        Screen s = new Screen();
        queue.add(s);
        visited[1][0] = true;

        while(!queue.isEmpty()) {

            Screen now = queue.poll();
            for (Operation o : Operation.values()) {
                if(!o.inCondition(now)) break;
                Screen next = o.calculate(now);
                // 이모지가 음수가 나올 수 없다
                // 현재 기준 최소보다 높다면 알아볼 필요 ㄴ
//                if (next.emoji == 0 || next.time >= MAX) break;

                if(next.emoji == S) {
                    System.out.println(next.time);
                    return;
                } else queue.add(next);
            }
        }

    }
    public static int MAX = 1001;
    public static boolean[][] visited;

    static class Screen {
        int emoji;  // 화면에 입력된 이모티콘
        int clipboard;  // 클립보드에 저장된 이모티콘 개수
        int time;       // 최종적으로 만들어지기까지의 시간

        public Screen() {
            this.emoji = 1;
            this.clipboard = 0;
            this.time = 0;
        }

        public Screen(int emoji, int clipboard, int time) {
            this.emoji = emoji;
            this.clipboard = clipboard;
            this.time = time;
        }

        @Override
        public String toString() {
            return "Screen{" +
                    "emoji=" + emoji +
                    ", clipboard=" + clipboard +
                    ", time=" + time +
                    '}';
        }
    }
    enum Operation {
        COPY {

            @Override
            public Screen calculate(Screen input) {
                Screen result = new Screen();
                visited[input.emoji][input.emoji] = true;

                result.emoji = input.emoji;
                result.clipboard = input.emoji;
                result.time = input.time+1;

                return result;
            }

            @Override
            public boolean inCondition(Screen input) {
                return (input.emoji > 0 && input.time < MAX)
                        && !visited[input.emoji][input.emoji];
            }
        },
        PASTE {
            @Override
            public Screen calculate(Screen input) {
                Screen result = new Screen();
                visited[input.emoji+input.clipboard][input.clipboard] = true;
                result.emoji = input.emoji + input.clipboard;
                result.clipboard = input.clipboard;
                result.time = input.time+1;

                return result;
            }

            @Override
            public boolean inCondition(Screen input) {
                return (input.clipboard > 0 && (input.time +input.clipboard) < MAX)
                        && !visited[input.emoji+input.clipboard][input.clipboard];
            }
        },
        DELETE {
            @Override
            public Screen calculate(Screen input) {
                Screen result = new Screen();

                visited[input.emoji-1][input.emoji] = true;
                result.emoji = input.emoji - 1;
                result.clipboard = input.emoji;
                result.time = input.time+1;

                return result;
            }

            @Override
            public boolean inCondition(Screen input) {
                return (input.emoji > 0 && input.time < MAX)
                        && !visited[input.emoji-1][input.emoji];
            }
        };

        public abstract Screen calculate(Screen input);
        public abstract boolean inCondition(Screen input);

    }

}
```