# [BaekJoon#1744] 수 묶기



> ### Problem
>
> https://www.acmicpc.net/problem/1744



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws NumberFormatException, IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        int[] arr = new int[N];

        for(int i=0; i<N; i++){
            arr[i] = Integer.parseInt(br.readLine());
        }
        Arrays.sort(arr);
        int answer = bindNum(arr);
        System.out.println(answer);
    }
    public static int bindNum(int[] arr){
        int answer = 0;

        int head = 0;
        int leaf = arr.length-1;

        for(; head<leaf; head++){
            if(arr[head]<1 && arr[head+1]<1){
                answer += arr[head]*arr[++head];
            } else break;
        }
        for(; leaf>head; leaf--){
            if(arr[leaf]>1 && arr[leaf-1]>1){
                answer += arr[leaf]*arr[--leaf];
            } else break;
        }
        for(int i=head; i<=leaf; i++){
            answer += arr[i];
        }
        return answer;
    }
}
```



> ####  반례
>
> ```
> 5
> -1 
> 0 
> 1 
> 2 
> 3
> 답 : 7
> ```
>
> ```
> 4
> -1 
> -1 
> -1 
> 3
> 답 : 3
> ```
>
> ```
> 3
> -6 
> -5 
> -1
> 답 : 29
> ```
>
> ```
> 2
> 1
> 2
> 답 : 3
> ```

