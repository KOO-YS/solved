# [BaekJoon#6003] Claustrophobic Cows 



> ### Problem
>
> https://www.acmicpc.net/problem/6003



> ### ING 

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.Comparator;
import java.util.StringTokenizer;

public class Main {


    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;

        int N = Integer.parseInt(br.readLine());


        Point[] points = new Point[N];
        for (int i=0; i<N; i++) {
            tokenizer = new StringTokenizer(br.readLine());
            points[i] = new Point(i+1, Integer.parseInt(tokenizer.nextToken()), Integer.parseInt(tokenizer.nextToken()));
        }

        double result = closestPair(points);
        System.out.println("가장 가까운 두 점 사이의 거리: " + result);
    }

    static class Point {
        int index, x, y;
        Point(int index, int x, int y) {
            this.x = x;
            this.y = y;
        }
    }

    public static double closestPair(Point[] points) {
        Point[] px = points.clone();
        Point[] py = points.clone();
        Arrays.sort(px, Comparator.comparingInt(p -> p.x));
        Arrays.sort(py, Comparator.comparingInt(p -> p.y));
        return closestPairRecursive(px, py);
    }

    private static double closestPairRecursive(Point[] px, Point[] py) {
        if (px.length <= 3) {
            return bruteForce(px);
        }

        int mid = px.length / 2;
        Point midPoint = px[mid];

        Point[] pyl = Arrays.stream(py).filter(p -> p.x <= midPoint.x).toArray(Point[]::new);
        Point[] pyr = Arrays.stream(py).filter(p -> p.x > midPoint.x).toArray(Point[]::new);
        Point[] pxl = Arrays.copyOfRange(px, 0, mid);
        Point[] pxr = Arrays.copyOfRange(px, mid, px.length);

        double dl = closestPairRecursive(pxl, pyl);
        double dr = closestPairRecursive(pxr, pyr);
        double d = Math.min(dl, dr);

        return Math.min(d, stripClosest(py, midPoint, d));
    }

    private static double bruteForce(Point[] points) {
        double minDist = Double.MAX_VALUE;
        for (int i = 0; i < points.length - 1; i++) {
            for (int j = i + 1; j < points.length; j++) {
                double dist = distance(points[i], points[j]);
                if (dist < minDist) {
                    minDist = dist;
                }
            }
        }
        return minDist;
    }

    private static double stripClosest(Point[] py, Point midPoint, double d) {
        double minDist = d;
        for (int i = 0; i < py.length; i++) {
            for (int j = i + 1; j < py.length && (py[j].y - py[i].y) < minDist; j++) {
                double dist = distance(py[i], py[j]);
                if (dist < minDist) {
                    minDist = dist;
                }
            }
        }
        return minDist;
    }

    private static double distance(Point p1, Point p2) {
        return Math.sqrt(Math.pow(p1.x - p2.x, 2) + Math.pow(p1.y - p2.y, 2));
    }
}

```

