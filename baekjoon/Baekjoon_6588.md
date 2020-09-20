# [BaekJoon#6588] 골드바흐의 추측



> ### Problem
>
> https://www.acmicpc.net/problem/6588



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuffer result = new StringBuffer();

        boolean[] prime = new boolean[1000001];

        isPrimeNum(prime);      // 소수 구분

        int n;                  // 입력 값
        while((n = Integer.parseInt(br.readLine())) != 0){
            result.append(getPartition(prime, n));
        }
        System.out.print(result.toString());
    }

    public static String getPartition(boolean[] prime, int n) {
        int small = 0;
        int large = 0;
        int start = 3;
        while(start<=n/2){
            if(prime[start] && prime[n - start]){
                small = start;
                large = n - start;
                return n+" = "+small+" + "+large+"\n";
            }
            start += 2;
        }
        return "Goldbach's conjecture is wrong.";
    }

    /**
     * 에라토스테네스의 체 공식 -> 소수 판별
     * @param arr 해당 index의 수가 '소수'인지 여부
     */
    public static void isPrimeNum(boolean[] arr){
        Arrays.fill(arr, true);
        int n = arr.length;
        arr[0] = arr[1] = false;    // 0과 1은 소수의 범위에 들지 않는다

        for(int i=2; i<Math.sqrt(n); i++){
            if(arr[i]){     // arr[i]가 소수일 때,
                for( int j=i*i; j< n; j+=i ){
                    arr[j] = false;             // 약수가 존재 -> 소수 X
                }
            }
        }
    }
}

```
