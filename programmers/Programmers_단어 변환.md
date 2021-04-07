# [Programmers] 단어 변환



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/43163
>



> ### 참고 블로그
>
> https://tosuccess.tistory.com/29
>
> 깊이 우선 탐색
>
> <br>
>
> ### Solution

```java
class Solution {
    public int answer;
    public boolean[] visited;
    public int solution(String begin, String target, String[] words) {
        answer = 51;        // 변환할 수 없는 경우
        visited = new boolean[words.length];

        dfs(0, begin, target, words);

        return (answer == 51)? 0 : answer;
    }

    public void dfs(int level, String begin, String target, String[] words){
        if(begin.equals(target)) {
            answer = Math.min(answer, level);
            return;
        }
        for(int i=0; i<words.length; i++){
            if(!visited[i] && compareWords(begin, words[i])){   // 방문하지 않았으면서, 변환 가능
                visited[i] = true;
                dfs(level+1, words[i], target, words);
                visited[i] = false;
            }
        }
    }

    /**
     * 단어 변환 가능 여부
     * -> 두 단어의 차이가 알파벳 하나 차이인지 여부
     */
    public boolean compareWords(String begin, String target){
        int count = 0;

        for(int i=0; i<begin.length(); i++){
            if(begin.charAt(i) != target.charAt(i)) count++;
        }
        return count == 1;      // 한 번에 한 개의 알파벳만 바꿀 수 있다
    }
}
```

