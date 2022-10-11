## [BaekJoon#1303] 전쟁 - 전투



> ### Problem
>
> https://www.acmicpc.net/problem/1303



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

    /*
    [WHITE]
    9 * 9 (81)
    7 * 7 (49)
    += 130

    [BLUE]
    1 * 1 (1)
    8 * 8 (64)
    += 65
    * */

    static final char WHITE = 'W';

    static final char BLUE = 'B';

    static int N;
    static int M;

    static int[] dx = {-1, 0, 1, 0};
    static int[] dy = {0, -1, 0, 1};

    static char[][] field;
    static boolean[][] visited;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        // get parameters
        N = Integer.parseInt(tokenizer.nextToken());
        M = Integer.parseInt(tokenizer.nextToken());

        field = new char[M][N];
        visited = new boolean[M][N];

        for (int i=0; i<M; i++) {
            field[i] = br.readLine().toCharArray();
        }

        // solve
        String power = calculatePower();

        // print answer
        System.out.println(power);
    }

    private static String calculatePower() {
        int sumW = 0;
        int sumB = 0;

        for (int i=0; i<M; i++) {           // 세로
            for (int j=0; j<N; j++) {       // 가로
                if (!visited[i][j]) {
                    int crowd = dfs(i, j, field[i][j]);
                    if (field[i][j] == WHITE)
                        sumW += crowd * crowd;
                    else
                        sumB += crowd * crowd;
                }
            }
        }
        return sumW + " " + sumB;
    }

    private static int dfs(int x, int y, char ch) {
        int count = 1;
        visited[x][y] = true;

        for (int i=0; i<4; i++) {
            for (int j=0; j<4; j++) {
                int nowX = x + dx[i];
                int nowY = y + dy[j];

                if (nowX < 0 || nowX > N || nowY < 0 || nowY > M)
                    continue;

                if (!visited[nowY][nowX] && field[nowY][nowX] == ch) {
                    count += dfs(nowX, nowY, ch);
                }
            }
        }
        return count;
    }
}
```
