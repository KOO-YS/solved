# [Programmers] 신규 아이디 추천

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/72410



> ### Solution

```java
public String solution(String new_id) {
    String answer = "";
    StringBuilder result = new StringBuilder();

    int validLength = 0;
    char[] arr = new_id.toCharArray();
    if(arr[0] != '.'){
        validLength++;
        result.append(arr[0]);
    }
    for(int i=1; i<arr.length; i++){
        if(isValidChar(arr[i])){

        }else{
            if(changeCapitalLetter(arr[i]) != arr[i]){
                arr[i] = changeCapitalLetter(arr[i]);
                i--;
            }
        }

    }

    if(new_id.charAt(new_id.length()-1) != '.'){
        validLength++;
        result.append(new_id.charAt(new_id.length()-1));
    }

    // end
    if(validLength == 0) return "aaa";

    // 길이 확인
    if(validLength <= 2){

    }
    return answer;
}
public boolean isValidChar(char ch){
    if((ch == '-') || (ch == '_') || (ch == '.')) return true;
    else if(ch >= 'a' && ch <= 'z') return true;
    return false;
}

public char changeCapitalLetter(char ch){
    if(ch >= 'A' && ch <= 'Z'){
        return (char)(ch+32);
    }
    return ch;
}
```

