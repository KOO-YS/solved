# [Programmers] 스킬트리



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/49993



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(String skill, String[] skill_trees) {
        int answer = 0;
        for(String tree : skill_trees){
            if(checkSkill(skill, tree)) answer++;
        }
        return answer;
    }

    public boolean checkSkill(String skill, String tree) {
        Map<Character, Integer> order = new HashMap<>();
        int index = 0;
        for(char t : tree.toCharArray()){
            //  order[key : 스킬이름 value : 스킬의 순서] 저장
            order.put(t, index++);
        }

        int before = 0;
        boolean proper = true;
        int size = 0;
        for(char s : skill.toCharArray()){
            if(order.containsKey(s)){
                if(!proper) return false;                  // 이전의 스킬이 없지만 다음 스킬이 존재? -> 탈출
                if(order.get(s) < before) return false;    // 다음 스킬보다 이전 스킬의 순서가 더 늦다? -> 탈출
                before = order.get(s);
            } else proper = false;      // 해당 스킬(s)이 없다
        }
        return true;
    }
}
```
