# [BaekJoon#14226] 이모티콘



> ### Problem
>
> https://www.acmicpc.net/problem/14226


> ### Solution (yet)

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

// https://www.acmicpc.net/problem/14226
public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int S = Integer.parseInt(tokenizer.nextToken());

        int MIN = Integer.MAX_VALUE;


        
        Stack<Screen> stack = new Stack<>();
        Screen s = new Screen();

        stack.add(s);

        while(!stack.isEmpty()) {

            Screen now = stack.pop();
            // S개의 이모티콘을 완성할 때까지 계속한다
//            while (now.emoji == S) {
//            }
            for (Operation o : Operation.values()) {
                Screen next = o.test(now);
                // 이모지가 음수가 나올 수 없다
                // 현재 기준 최소보다 높다면 알아볼 필요 ㄴ
                if (next.emoji == 0 || next.time > MIN) break;

                if(next.emoji == S) {
                    MIN = next.time;
                } else stack.add(next);
            }
        }
        System.out.println(MIN);

    }
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

    }
    enum Operation {
        COPY {
            @Override
            public int apply(int input) {
                return 0;
            }

            @Override
            public Screen test(Screen input) {
                Screen result = new Screen();

                result.emoji = input.emoji;
                result.clipboard = input.emoji;
                result.time = input.time+1;

                return result;
            }
        },
        PASTE {
            @Override
            public int apply(int input) {
                return 0;
            }
            @Override
            public Screen test(Screen input) {
                Screen result = new Screen();

                result.emoji = input.emoji + input.clipboard;
                result.clipboard = input.clipboard;
                result.time = input.time+1;

                return result;
            }
        },
        DELETE {
            @Override
            public int apply(int input) {
                return 0;
            }
            @Override
            public Screen test(Screen input) {
                Screen result = new Screen();

                result.emoji = input.emoji - 1;
                result.clipboard = input.emoji;
                result.time = input.time+1;

                return result;
            }
        };

        public abstract int apply(int input);
        public abstract Screen test(Screen input);

    }
}
```