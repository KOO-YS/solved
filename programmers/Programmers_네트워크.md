# [Programmers] 네트워크



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/43162



> ### Solution

```java
import java.util.*;

class Solution {
    public boolean[] visited;
    public int solution(int n, int[][] computers) {
        int answer = 0;
        // 방문 표시
        visited = new boolean[n];

        for(int i=0; i<computers.length; i++){
            if(visited[i] == false){
                answer ++;
                dfs(i, computers);
            }
        }
        return answer;
    }
    public void dfs(int com, int[][] computers){
        visited[com] = true;
        for(int i=0; i<computers[com].length; i++){
            if( computers[com][i] == 1 ){
                if( !visited[i] ) dfs(i, computers);
            }
        }
    }
}
```



---

#### temp_ 미완

```java

    public int solution(int n, int[][] computers) {
        int answer = 0;

        int[] parent = new int[n];
        // 초기화
        for(int i=0; i<n; i++){
            parent[i] = i;
        }
        List<Integer> networks = new ArrayList<>();
        // 연결에 의해 해당 네트워크 대표 숫자 설정
        for(int i=0; i<computers.length; i++){
            networks = new ArrayList<>();
            for(int j=0; j<computers[i].length; j++){
                if( computers[i][j] == 1 ) networks.add(j);
            }
            if(networks.size()>0) unionParent(networks, parent);
        }
        if(networks.size() > 0){
            int p = parent[0];
            answer++;
            for(int i=0; i<parent.length; i++){
                if( getParent(i, parent) != p ) {
                    p = getParent(i, parent);
                    answer++;
                }
            }
        }
        return answer;
    }

    // 네트워크 부모값(최소값) 찾기
    public int getParent(int com, int[] parent){
        if( com == parent[com] ) return com;
        return parent[com] = getParent(parent[com], parent);
    }

    // 부모값 결합
    public void unionParent(List<Integer> com, int[] parent){
        List<Integer> children = new ArrayList<>();
        // 각 컴퓨터의 부모값 삽입
        for (int i : com) {
            children.add(getParent(i, parent));
        }
        Collections.sort(children);
        int min = children.get(0);
        for (int set : com) {
            parent[set] = min;
        }
    }
```