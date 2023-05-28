# [Programmers] 숫자 카드 나누기

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/135807



> ### Solution

```java
class Solution {
    public int solution(int[] arrayA, int[] arrayB) {

		// arrayA의 최대 공약수
		int gcdA = arrayA[0];
		for (int a : arrayA) {
			gcdA = gcd(gcdA, a);
		}

		// arrayB의 최대 공약수
		int gcdB = arrayB[0];
		for (int b : arrayB) {
			gcdB = gcd(gcdB, b);
		}

		// arrayB의 최대 공약수로 나누어지는 숫자가 있는지 확인
		for (int a : arrayA) {
			if (a%gcdB == 0) {
				gcdB = 0;
				break;
			}
		
		// arrayA의 최대 공약수로 나누어지는 숫자가 있는지 확인
		for (int b : arrayB) {
			if (b%gcdA == 0) {
				gcdA = 0;
				break;
			}
		}
		
		return Math.max(gcdA, gcdB);
	}

	// 유클리드 호제 : 최대 공약수
	int gcd(int a, int b) {
		while (b != 0) {
			int r = a%b;
			a=b;
			b=r;
		}
		return a;
	}
}
```
