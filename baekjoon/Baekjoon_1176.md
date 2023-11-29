# [BaekJoon#1776] 암기왕



> ### Problem
>
> https://www.acmicpc.net/problem/1776



> ### Solution
>

---

> ### Wrong
>

> ```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;
        StringBuilder result = new StringBuilder();

        int T = Integer.parseInt(br.readLine());

        while (T-- > 0) {
            int N = Integer.parseInt(br.readLine());

            int[] note = new int[N];
            tokenizer = new StringTokenizer(br.readLine(), " ");
            for (int i = 0; i < N; i++) {
                note[i] = Integer.parseInt(tokenizer.nextToken());
            }

            Arrays.sort(note);

            int M = Integer.parseInt(br.readLine());
            tokenizer = new StringTokenizer(br.readLine(), " ");
            for (int i = 0; i < M; i++) {
                result.append(contains(note, Integer.parseInt(tokenizer.nextToken()))).append('\n');
            }

            System.out.println(result);
        }

    }

    static int contains(int[] note, int num) {
        int start = 0;
        int end = note.length - 1;

        while (start <= end) {
            int mid = (start + end)/2;
            if (note[mid] == num)
                return 1;
            else if (note[mid] > num)
                end = mid -1;
            else
                start = mid +1;

        }
        return 0;
    }

}

>    ```
