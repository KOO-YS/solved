# [Programmers] 다트 게임 



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/17682



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(String dartResult) {
        int answer = 0;

        char[] ch = dartResult.toCharArray();
        List<Score> scores = new ArrayList<Score>();

        for(int i=0; i<ch.length; i++){

            Score score = new Score();

            // 점수 획득
            if(ch[i] == '1' && ch[i+1] == '0'){
                score.value = 10;
                i += 2;
            } else if(ch[i] >= '0'){
                score.value = ch[i++] - 48;
            }

            // 보너스 제곱 값 획득
            score.getSquared(ch[i]);

            // 옵션이 있을때 옵션값 획득
            if(i <= ch.length -2){
                if(ch[i+1] == '*' || ch[i+1] == '#'){
                    i++;
                    score.getOption(ch[i]);
                    if(ch[i] == '*' && scores.size() >0) {
                        scores.get(scores.size()-1).getOption(ch[i]);
                    }
                }
            }
            scores.add(score);

        }
        for(Score s : scores){
            answer += s.calculate();
        }

        return answer;
    }
}
class Score{
    int value;
    int squared;
    List<Integer> option;

    public Score(){
        option = new ArrayList<>();
    }

    public void getSquared(char ch){
        switch (ch){
            case 'S':
               this.squared = 1; break;
            case 'D':
                this.squared = 2; break;
            case 'T':
                this.squared = 3; break;
        }
    }

    public void getOption(char ch){
        if(ch == '*') {
            this.option.add(2);
        } else if(ch == '#'){
            this.option.add(-1);
        }
    }

    public int calculate(){
        int sum = 0;

        sum = (int)Math.pow(this.value, this.squared);
        for (int op : option){
            sum *= op;
        }
        return sum;
    }
}

```

