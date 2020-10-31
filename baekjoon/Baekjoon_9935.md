# [BaekJoon#9935] 문자열 폭발



> ### Problem
>
> https://www.acmicpc.net/problem/9935



> ### Solution 

```java
import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        String data = br.readLine();
        String bomb = br.readLine();

        String result = explodeStr(data, bomb);
        System.out.println(result);
    }

    public static String explodeStr(String data, String bomb ){
        char[] letters = data.toCharArray();
        int bombLength = bomb.length();
        Stack<Character> search = new Stack<>();

        for(int i=0; i<letters.length; i++){
            search.push(letters[i]);

            if(search.size() < bombLength) continue;

            if(bomb.charAt(bomb.length()-1) == search.peek()){
                // bomb의 길이만큼 stack 앞부분 조회
                boolean same = true;
                for(int j = 0; j<bombLength; j++){
                    if(search.get(search.size()-bombLength+j) != bomb.charAt(j)){
                        same = false;
                        break;
                    }
                }
                if(same){
                    int pop = bombLength;
                    while (pop-->0){
                        search.pop();
                    }
                }
            }
        }
        StringBuilder result = new StringBuilder();
        for(Character s : search){
            result.append(s);
        }

        return (result.length() == 0)? "FRULA" : result.toString();
    }
}
```





> ### Solution (시간 초과)
>

```java
import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        String data = br.readLine();
        String bomb = br.readLine();

        String result = explodeStr(data, bomb);
        System.out.println(result);
    }

    public static String explodeStr(String data, String bomb ){
        char[] letters = data.toCharArray();
        Stack<Character> search = new Stack<>();

        for(int i=0; i<letters.length; i++){
            search.push(letters[i]);

            if(search.size() < bomb.length()) continue;

            if(bomb.charAt(bomb.length()-1) == search.peek()){      // 폭발 문자열의 마지막 인덱스와 같다면?
                // bomb의 길이만큼 stack 앞부분 조회
                int compare = search.size()-bomb.length();
                // bomb와 전체 같은지 확인
                boolean same = true;
                for(int j = 0; j<bomb.length(); j++){
                    if(search.get(compare+j) != bomb.charAt(j)){
                        same = false;
                        break;
                    }
                }
                if(same){
                    int pop = bomb.length();
                    while (pop-->0){
                        search.pop();
                    }
                }
            }
        }
        StringBuilder result = new StringBuilder();
        while(!search.isEmpty()){
            result.insert(0, search.pop());
        }

        return (result.length() == 0)? "FRULA" : result.toString();
    }
}

```



#### 시간 초과가 떠서 변경한 점  

1. bomb.length()로 함수를 매번 호출하는 대신 변수 선언해 사용

2. stack 반환에 향상된 for문 사용