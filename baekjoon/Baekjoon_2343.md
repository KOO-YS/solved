# [BaekJoon#2343] 기타 레슨



> ### Problem
>
> https://www.acmicpc.net/problem/2343



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine(), " ");

        int N = Integer.parseInt(tokenizer.nextToken());
        int M = Integer.parseInt(tokenizer.nextToken());

        int[] arr = new int[N];

        tokenizer = new StringTokenizer(br.readLine(), " ");

        int min = 0;    // max in array
        int max = 0;    // total sum

        for (int i=0; i<N; i++) {
            arr[i] = Integer.parseInt(tokenizer.nextToken());
            max += arr[i];
            if (min < arr[i])
                min = arr[i];
        }

        int count = 0;
        int mid = 0;
        while (min <= max) {
            mid = (min + max) / 2;
            count = countDisc(arr, mid);
            if (count > M)
                min = mid + 1;
            else
                max = mid - 1;
        }

        System.out.println(min);
    }

    static int countDisc(int[] arr, int size) {
        int disc = 0;
        int count = 0;
        for (int i=0; i<arr.length; i++) {

            if ((disc + arr[i]) > size) {
                count++;
                disc = 0;
            }
            disc += arr[i];
        }
        if (disc != 0)
            count++;
        return count;
    }
}

```
