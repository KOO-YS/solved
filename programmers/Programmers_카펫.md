# [Programmers] 카펫



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42842



> ### Solution

```java
class Solution {
    public int[] solution(int brown, int yellow) {
        int[] answer = {};
        int size = brown + yellow;      // 전체 사이즈
        int width = size;

        while(width >= 3){              // 노란색을 감싸려면 최소 3개 이상이다
            if(size%width == 0){
                int height = size/width;
                if(brown == (width*2 + (height-2)*2)){      // 가로 세로 테두리 합이 갈색 갯수와 같으면?
                    return new int[]{width, height};
                }
            }
            width--;
        }
        return answer;
    }
}
```

