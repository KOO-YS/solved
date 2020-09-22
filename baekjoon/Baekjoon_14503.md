# [BaekJoon#14503] 로봇청소기



> ### Problem
>
> https://www.acmicpc.net/problem/14503



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine(), " ");
        int N = Integer.parseInt(token.nextToken());
        int M = Integer.parseInt(token.nextToken());
        // 방의 크기
        int[][] room = new int[N][M];

        token = new StringTokenizer(br.readLine(), " ");
        // 로봇 청소기 좌표
        int r = Integer.parseInt(token.nextToken());
        int c = Integer.parseInt(token.nextToken());

        // 바라보는 방향
        int f = Integer.parseInt(token.nextToken());

        for(int i=0; i<room.length; i++){
            token = new StringTokenizer(br.readLine(), " ");
            for(int j=0; j<room[0].length; j++){
                room[i][j] = Integer.parseInt(token.nextToken());
            }
        }

//        for(int i=0; i<room.length; i++){
//            for(int j=0; j<room[0].length; j++){
//                System.out.print(room[i][j]);
//            }
//            System.out.println();
//        }

        int answer = cleanRoom(room, r, c);

        System.out.println(answer);
    }
    //                        북 동  남 서
    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};

    public static int cleanRoom(int[][] room, int r, int c) {
        int square = 0;

        return square;
    }
}

```

