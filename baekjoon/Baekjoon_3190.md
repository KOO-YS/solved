# [BaekJoon#3190] 뱀



> ### Problem
>
> https://www.acmicpc.net/problem/3190


> ### Solution 1

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

class Main {
    public static int[][] map;
    public static Deque<Point> snake;               // 뱀의 머리부터 꼬리까지 위치 저장
    public static PriorityQueue<Turn> queue;        // 방향 변환을 시간순으로 나열

    // 방향을 꺾을때마다 이동할 x, y 좌표
    public static int[] dx = {0, 1, 0, -1};
    public static int[] dy = {1, 0, -1, 0};

    public static final int SNAKE_BODY = -1;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;

        int N = Integer.parseInt(br.readLine());
        int K = Integer.parseInt(br.readLine());

        map = new int[N+1][N+1];

        snake = new LinkedList<>();
        snake.add(new Point(1,1));
        map[1][1] = SNAKE_BODY;

        // 사과 채워넣기
        while (K-- >0) {
            tokenizer = new StringTokenizer(br.readLine());
            map[Integer.parseInt(tokenizer.nextToken())][Integer.parseInt(tokenizer.nextToken())] = 1;
        }

        int L = Integer.parseInt(br.readLine());


        queue = new PriorityQueue<>();
        while (L-- >0) {
            tokenizer = new StringTokenizer(br.readLine());
            queue.add(new Turn(Integer.parseInt(tokenizer.nextToken()),
                    (tokenizer.nextToken().charAt(0)=='D'? 1 : -1 )));      // 왼쪽 오른쪽 구분
        }

        System.out.println(checkTime());

    }
    public static int checkTime() {
        int time = 1;       // 총 시간
        int snakeDirect = 0;    // 뱀이 갈 다음 방향

        // start : 다음 좌표
        int x = 1 +dx[snakeDirect];
        int y = 1 +dy[snakeDirect];


        int nextRoute = map[x][y];          // 다음 칸 값
        Turn nextTurn = queue.poll();       // 다음 방향 전환
        Point rm;

        // 벽에 닿으면 & 자기 몸과 부딪히면 OUT
        while(isBoundary(x, y) && (nextRoute = map[x][y]) != SNAKE_BODY) {

            // 먼저 뱀은 몸길이를 늘려 머리를 다음칸에 위치시킨다
            snake.add(new Point(x, y));
            map[x][y] = SNAKE_BODY;

            // 만약 이동한 칸에 사과가 있다면, 그 칸에 있던 사과가 없어지고 꼬리는 움직이지 않는다
            // 사과가 없다면, 몸길이를 줄여서 꼬리가 위치한 칸을 비워준다. 즉, 몸길이는 변하지 않는다.
            if(nextRoute == 0) { // 사과 발견 X
                rm = snake.removeFirst();
                map[rm.x][rm.y] = 0;
            }

            // 방향 바꾸기
            if(time == nextTurn.second) {

                snakeDirect = ((snakeDirect + nextTurn.direct)<0 )? (snakeDirect + nextTurn.direct) + 4 : (snakeDirect + nextTurn.direct) % 4;
                if(!queue.isEmpty()) nextTurn = queue.poll();
            }
            x += dx[snakeDirect];
            y += dy[snakeDirect];
            time++;
        }

        return time;
    }

    public static boolean isBoundary(int x, int y) {
        if(x < 1 || x >= map.length) return false;
        if(y < 1 || y >= map.length) return false;
        return true;
    }
}
class Turn implements Comparable<Turn>{
    int second;
    int direct;

    public Turn(int second, int direct) {
        this.second = second;
        this.direct = direct;
    }

    @Override
    public int compareTo(Turn o) {
        return second - o.second;
    }
}

class Point {
    int x;
    int y;

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```
<br>

> ### Solution 2

```java

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        // 보드의 크기
        int N = Integer.parseInt(br.readLine());
        // 사과의 개수
        int K = Integer.parseInt(br.readLine());

        int[][] board = new int[N+1][N+1];

        StringTokenizer token;
        for( int i = 0; i<K; i++ ){
            token = new StringTokenizer(br.readLine(), " ");
            // 사과의 위치 설정
            board[Integer.parseInt(token.nextToken())][Integer.parseInt(token.nextToken())] = 1;
        }

        // 방향 변환 횟수
        int L = Integer.parseInt(br.readLine());
        // 시간 & 방향 저장
        int[][] direction = new int[L][2];
        for(int i=0; i<L; i++){
            token = new StringTokenizer(br.readLine(), " ");
            int sec = Integer.parseInt(token.nextToken());
            // 오른쪽 : 1  || 왼쪽 : -1
            int side = (token.nextToken().equals("D"))? 1 : -1;
            direction[i][0] = sec;
            direction[i][1] = side;
        }
        int time = getfinishTime(board, direction);

        System.out.println(time);
    }
    public static int[] dx = {0, 1, 0, -1};
    public static int[] dy = {1, 0, -1, 0};

    public static int getfinishTime(int[][] board, int[][] direction){
        int time = 0;
        int idx = 0;        // 방향배열의 인덱스

        int turn = 0;       // (오른쪽 방향을 시작) 뱀 움직임 방향
        int turnX = dx[turn];
        int turnY = dy[turn];


        Queue<int[]> snake = new LinkedList<>();

        // 출발지점 초기화
        int x = 1;
        int y = 1;

        snake.add(new int[]{x, y});
        board[x][y] = 2;

        while(true){
            time++;

            x += turnX;
            y += turnY;

            if (!isBoundary(board, x, y)) break;
            if (crashBody(board, x, y)) break;

            if( board[x][y] == 1 ){             // 사과 자리
                board[x][y] = 2;
                snake.add(new int[]{x, y});
            } else {
                board[x][y] = 2;
                snake.add(new int[]{x, y});         // 사과가 없는 자리
                int[] remove = snake.poll();
                board[remove[0]][remove[1]] = 0;    // 몸통 표시 없애기
            }

            if( idx<direction.length && direction[idx][0] == time){      //방향 변환
                // 오른쪽 회전
                if(direction[idx][1] > 0){
                    turn = (turn+1)%4;
                }
                // 왼쪽 회전
                else {
                    if(turn == 0) {
                        turn = 3;
                    } else {
                        turn--;
                    }
                }
                turnX = dx[turn];
                turnY = dy[turn];

                idx++;
            }
        }
        return time;
    }

    /**
     *  종료 조건
     *  1. 벽에 닿는다
     *  2. 자기 몸에 닿는다
     */

    /**
     *  1. 보드 범위 내 존재하는지 여부
     *  board의 크기는 (N+1)*(N+1)
     *  사용하는 인덱스 범위 : 1 ~ N
     */
    public static boolean isBoundary(int[][] board, int x, int y){

        boolean forX = (x > 0 && x < board.length);
        boolean forY = (y > 0 && y < board.length);
        return forX&&forY;
    }

    // 2. 뱀 자신의 몸과 충돌했는지 여부 반환
    public static boolean crashBody(int[][] board, int x, int y){
        if(board[x][y] == 2) return true;
        return false;
    }
}

```

> ###### **삽질 원인**
>
> 이미 뱀이 접근한 사과 위치를 초기화 안함..