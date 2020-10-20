# [BaekJoon#2437] 저울



> ### Problem
>
> https://www.acmicpc.net/problem/2437

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        StringTokenizer token = new StringTokenizer(br.readLine(), " ");
        int[] scale = new int[N];
        for(int i=0; i<N; i++){
            scale[i] = Integer.parseInt(token.nextToken());
        }
        Arrays.sort(scale);

//        System.out.println(Arrays.toString(scale));

        int answer = setScale(scale);

        System.out.println(answer);
    }
    public static int setScale(int[] scale){
        int max = scale[0];
        if(max != 1) return 1;
        for(int i=1; i<scale.length; i++){
            if(max+1 < scale[i]){
                break;
            }
            max += scale[i];
        }

        return max+1;
    }
}
```



> #### 문제 이해
>
> 저울추가 무제한으로 있지않고 무조건 주어진 개수만큼만 존재한다!
>
> 저울추를 오름차순으로 정렬 후 작은것부터 차례로 더한다
>
> 앞 순서의 저울추들의 합과 다음 저울 추 사이의 매꾸지못할 갭이 있다면? -> 측정 불가
>
> 앞 순서의 저울추에서 1을 더해 측정할 수 없는 최솟값을 만든다