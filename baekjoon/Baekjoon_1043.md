# [BaekJoon#1043] 거짓말



> ### Problem
>
> https://www.acmicpc.net/problem/1043



> ### Solution
>

```java
import java.io.*;
import java.util.*;

public class Main {

    static int N, M, result = 0;
    static int[] parents;
    static ArrayList<Integer>[] list;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine());

        N = Integer.parseInt(token.nextToken());
        M = Integer.parseInt(token.nextToken());

        list = new ArrayList[M];
        parents = new int[N + 1];
        for (int i = 0; i < M; i++) {
            list[i] = new ArrayList<>();
        }
        for (int i = 1; i <= N; i++) {
            parents[i] = -1;
        }

        token = new StringTokenizer(br.readLine());
        int num = Integer.parseInt(token.nextToken());
        for (int i = 0; i < num; i++) {
            int temp = Integer.parseInt(token.nextToken());
            parents[temp] = temp;
        }

        for (int i = 0; i < M; i++) {
            token = new StringTokenizer(br.readLine());
            num = Integer.parseInt(token.nextToken());
            for (int j = 0; j < num; j++) {
                list[i].add(Integer.parseInt(token.nextToken()));
            }
            if (list[i].size() >= 2) {
                disjointSet(i);
            }
        }

        for (int i = 0; i < M; i++) {
            if (!check(i)) {
                result++;
            }
        }
        System.out.println(result);
    }

    public static void disjointSet(int R) {
        int a = list[R].get(0);
        for (int i = 1; i < list[R].size(); i++) {
            unionParent(a, list[R].get(i));
        }
    }

    public static void unionParent(int a, int b) {
        int aRoot = getParent(a);
        int bRoot = getParent(b);
        if (aRoot != bRoot) {
            if (aRoot == parents[aRoot]) {
                parents[bRoot] = aRoot;
            } else {
                parents[aRoot] = bRoot;
            }
        }
    }

    public static int getParent(int a) {
        if (parents[a] < 0 || parents[a] == a) {
            return a;
        }
        return parents[a] = getParent(parents[a]);
    }

    public static boolean check(int R) {
        for (int i = 0; i < list[R].size(); i++) {
            int n = getParent(list[R].get(i));
            if (parents[n] == n) {
                return true;
            }
        }
        return false;
    }

}

```
