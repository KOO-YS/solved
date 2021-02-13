# [Programmers] 신규 아이디 추천

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/72410





> ### Solution (다른 사람 풀이 참고)

```java
class Solution {
    public String solution(String new_id){
        String answer = "";

        // 대문자 변환
        String temp = new_id.toLowerCase();

        // 사용 불가능한 문자 제거
        /*
         * 정규 표현식을 ^로 시작 :
         * 부정 문자셋(negated character set) 또는 보충 문자셋(complemented character set)
         * 괄호 내부에 등장하지 않는 어떤 문자와도 대응
         */
        temp = temp.replaceAll("[^-_.a-z0-9]", "");     // 포함 가능한 문자 : -_.a-z0-9

        //  .이 연속 등장하는 경우 제거
        temp = temp.replaceAll("[.]{2,}",".");
        // .가 앞뒤 끝에 오는 경우 제거
        temp = temp.replaceAll("^[.]|[.]$","");

        if(temp.equals("")) temp+="a";      // 공백일 때
        if(temp.length() >=16){
            temp = temp.substring(0,15);
            // substring 후 .가 앞뒤 끝에 오는 경우 제거
            temp=temp.replaceAll("^[.]|[.]$","");
        }
        if(temp.length()<=2)
            while(temp.length()<3)
                temp+=temp.charAt(temp.length()-1);

        answer=temp;

        return answer;
    }
}
```

<br>

#### 표현식 Tip

> ##### [^0-9] : 숫자를 제외한 나머지 문자만 허용. 숫자를 허용하지 않음 
>
> <br>
>
> ##### ^[0-9] : 문자열의 시작이 숫자만 허용
>
> ##### 	\* [0-9]$ :  문자열의 종료에 숫자만 허용
>
> <br>
>
> *차이점에 주의 !*



<br>

> ### Solution (성공했지만 정리 안된 코드)

```java
import java.util.Deque;
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public String solution(String new_id) {
        StringBuilder result = new StringBuilder();

        Queue<Character> initial = new LinkedList<>();
        Deque<Character> apply = new LinkedList<>();

        for(char c : new_id.toCharArray()){
            // 유효한 문자만 저장
            if((c = isValidChar(c)) != ' ') {
                initial.add(c);
            }
        }
        if(initial.size() == 0) return "aaa";

        if(initial.size() == 1 && initial.peek() != '.'){
            return ""+initial.peek()+initial.peek()+initial.peek();
        }
        char last = initial.poll();



        while(!initial.isEmpty()){
            if(last == '.' && initial.peek() == '.'){
                initial.poll();
                continue;
            }
            apply.add(last);
            if(initial.size() == 1 && initial.peek() != '.'){
                apply.add(initial.poll());
            } else if(!initial.isEmpty()) {
                last = initial.poll();
            }

        }

        apply = qwerty(apply);

        while(apply.size() > 15){
            apply.pollLast();
        }
        while(apply.size() < 3 && apply.size() > 0){
            apply.addLast(apply.peekLast());
        }

        apply = qwerty(apply);

        if(apply.isEmpty()) return "aaa";
        while(!apply.isEmpty()){
            result.append(apply.poll());
        }

        return result.toString();
    }

    public Deque<Character> qwerty(Deque<Character> apply) {
        boolean checkFirst;
        boolean checkLast;
        while(!apply.isEmpty()){
            checkFirst = false;
            checkLast = false;

            if(apply.peekFirst() == '.'){
                apply.pollFirst();
            } else checkFirst = true;
            if(!apply.isEmpty() && apply.peekLast() == '.'){
                apply.pollLast();
            } else checkLast = true;

            if(checkFirst && checkLast) {
                break;
            }
        }
        return apply;
    }

    public char isValidChar(char ch){
        if((ch == '-') || (ch == '_') || (ch == '.')) return ch;
        else if(ch >= 'a' && ch <= 'z') return ch;
        else if(ch >= '0' && ch <= '9') return ch;
        else if(ch >= 'A' && ch <= 'Z') return (char)(ch+32);
        return ' ';     // 나머지
    }
}
```

