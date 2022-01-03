# [Programmers] 거리두기 확인하기

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/81302

<br>

> ### wrong
>
> ```
> 채점 결과
> 정확성: 37.3
> 합계: 37.3 / 100.0

```java
public int[] solution(String[][] places) {
        int[] answer = new int[5];
        int index = 0;

        char[][] room;
        int rmIndex;
        for (String[] row : places) {
            room = new char[5][5];
            rmIndex = 0;
            for (String column : row) {
                room[rmIndex++] = column.toCharArray();
            }
            answer[index++] = keepDistance(room);
        }

        System.out.println(Arrays.toString(answer)+"?");
        return answer;
    }

    public int keepDistance(char[][] room) {
        for (int i=0; i<room.length-2; i++) {
            for (int j=0; j<room[i].length-2; j++) {
                if(room[i][j] == 'P') {     // 응시자 발견
                    if(room[i][j+1] == 'P' || room[i+1][j] == 'P') return 0;
                    if(room[i][j+1] == 'O' && (room[i][j+2] == 'P' || room[i+1][j+1] == 'P')) return 0;
                    if(room[i+1][j] == 'O' && (room[i+1][j+1] == 'P' || room[i+2][j] == 'P')) return 0;
                }
            }
        }

        return 1;
    }
```

