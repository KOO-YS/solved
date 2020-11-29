# [Programmers] 오픈채팅방

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42888

> ### Solution

```java
import java.util.*;

class Solution {
    public String[] solution(String[] record) {
        String[] answer = new String[record.length];
        StringTokenizer token;

        String[][] history = new String[record.length][2];

        // 유저 닉네임 바뀌는것 체크
        HashMap<String, String> account = new HashMap<>();
        int size = 0;
        for(int i=0; i<record.length; i++){
            token = new StringTokenizer(record[i], " ");

            String status = token.nextToken();
            char ch = status.charAt(0);

            String userId =token.nextToken();

            switch (ch){
                case 'L':       // Leave
                    size++;
                    break;
                case 'E':       // Enter
                    account.put(userId, token.nextToken());
                    size++;
                    break;
                case 'C':       // Change
                    account.put(userId, token.nextToken());
                    break;
            }
            history[i][0] = userId;
            history[i][1] = status;
        }
        return translate(account, history, size);
    }
    public String[] translate(HashMap<String, String> account, String[][] history, int size){
        String[] result = new String[size];
        int count = 0;
        for(String[] str : history){
            switch (str[1]){
                case "Enter":
                    result[count++] = account.get(str[0])+"님이 들어왔습니다.";
                    break;
                case "Leave":
                    result[count++] = account.get(str[0])+"님이 나갔습니다.";
                    break;
            }
        }

        return result;
    }
}
```


