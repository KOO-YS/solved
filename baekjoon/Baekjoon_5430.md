# [BaekJoon#5430] AC



> ### Problem
>
> https://www.acmicpc.net/problem/5430



> ### Solution

```java
import java.io.*;
import java.util.*;

class Main {

    public static StringBuilder result;
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        result = new StringBuilder();

        int T = Integer.parseInt(br.readLine());

        while(T-- >0) {
            // 수행할 함수
            String command = br.readLine();
            // 배열에 들어있는 수의 개수
            int n = Integer.parseInt(br.readLine());
            // 배열
            int[] p = convertIntArr(br.readLine());

            AC(command, p);
        }
        System.out.print(result);
    }

    public static void AC(String command, int[] p) {
        char[] cmdArr = command.toCharArray();

        int length = p.length;
        // 처음과 끝 인덱스
        int first = 0;
        int last = length-1;
        // 방향 뒤집기를 위한 변수
        int direction = 1;
        int temp;

        for(char cmd : cmdArr){

            // reverse
            if(cmd == 'R'){
                direction *= -1;
                temp = last;
                last = first;
                first = temp;
            }
            // delete
            else if(cmd == 'D' && length > 0) {
                length--;
                first += direction;
            }
            else { // cmd == 'D' && length =< 0
                result.append("error\n");
                return;
            }
        }

        if(length == 0){
            result.append("[]\n");
            return;
        }

        // 연산을 마친 배열 반환
        int[] answer = new int[Math.abs(last-first)+1];
        int index = 0;
        while(first != last + direction){
            answer[index++] = p[first];
            first += direction;
        }

        result.append(convertStr(answer));
    }

    /*
        int[] 값을 출력값으로 변환
    */
    public static String convertStr(int[] arr){
        StringBuilder str = new StringBuilder("[");
        for(int i=0; i<arr.length; i++){
            str.append(arr[i]);
            if(i != arr.length-1){
                str.append(",");
            }
        }
        str.append("]\n");
        return str.toString();
    }

    /*
        입력 문자열을 int[] 형태로 변환 
    */
    public static int[] convertIntArr(String arr){
        String[] strArr = arr.replaceAll("\\[", "").replaceAll("]", "").split(",");

        if(strArr[0].equals("")) return new int[]{};

        int[] intArr = Arrays.stream(strArr).mapToInt(Integer::parseInt).toArray();
        return intArr;
    }

}
```

