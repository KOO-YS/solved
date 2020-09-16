

# [Programmers] 전화번호 목록

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42577



> ### Solution

```java
import java.util.Arrays;

class Solution {
    public boolean solution(String[] phone_book) {
        
        Arrays.sort(phone_book, (o1, o2) -> {
            int len1 = o1.length();
            int len2 = o2.length();

            if(len1 > len2) return 1;
            else if(len1 < len2) return -1;
            return 0;
        });

        for(int i=0; i<phone_book.length-1; i++){
            // 전화번호 갯수
            int length = phone_book[i].length();
            // 전화번호 해쉬값
            int hash = phone_book[i].hashCode();

            for(int j=i+1; j<phone_book.length; j++){
                if(hash == phone_book[j].substring(0, length).hashCode()){
                    return false;
                }
            }
        }
        return true;
    }
}
```



---



#### Refactoring 

```java
Arrays.sort(phone_book, new Comparator<String>() {
    @Override
    public int compare(String o1, String o2) {
    	int len1 = o1.length();
        int len2 = o2.length();

		if(len1 > len2) return 1;
        else if(len1 < len2) return -1;
        return 0;
    }
});
```

##### Lambda 식 변환

```java
Arrays.sort(phone_book, (o1, o2) -> {
    int len1 = o1.length();
    int len2 = o2.length();

    if(len1 > len2) return 1;
    else if(len1 < len2) return -1;
    return 0;
});
```