# [BaekJoon#9093] 단어 뒤집기



> ### Problem
>
> https://www.acmicpc.net/problem/9093



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    StringBuilder result = new StringBuilder();

    int line = Integer.parseInt(br.readLine());
    while (line-- > 0) {
      String input = br.readLine();
      result.append(reverse(input)).append('\n');
    }
    System.out.print(result.toString());
  }

  public static String reverse(String input) {
    StringBuilder wordReverse = new StringBuilder();
    StringTokenizer tokenizer = new StringTokenizer(input, " ");

    while (tokenizer.hasMoreTokens()) {
      char[] split = tokenizer.nextToken().toCharArray();
      for (int i=split.length-1; i>=0; i--) {
        wordReverse.append(split[i]);
      }
      wordReverse.append(' ');
    }
    return wordReverse.toString();
  }
}

```

