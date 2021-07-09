# [BaekJoon#1929] 소수 구하기



> ### Problem
>
> https://www.acmicpc.net/problem/1929



> ### Solution

```java
    import java.io.*;
    import java.util.*;

    class Main {

        public static void main(String[] args) throws Exception {
            BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
            StringTokenizer tokenizer = new StringTokenizer(br.readLine(), " ");
            StringBuilder result = new StringBuilder();

            int M = Integer.parseInt(tokenizer.nextToken());
            int N = Integer.parseInt(tokenizer.nextToken());

            primes = new boolean[N+1];

            isPrimeNum(primes);

            while(M <= N) {
                if(primes[M]) result.append(M).append('\n');
                M++;
            }

            System.out.print(result.toString());
        }
        public static boolean[] primes;
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

