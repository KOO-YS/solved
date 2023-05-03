# [Programmers] 숫자 짝꿍

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/131128



> ### Solution

```java 
class Solution {
    public String solution(String X, String Y) {
		StringBuilder answer = new StringBuilder();
		int[] xNum = new int[10];
		int[] yNum = new int[10];

		for (char num : X.toCharArray()) {
			xNum[num-'0'] ++;
		}
		for (char num : Y.toCharArray()) {
			yNum[num-'0'] ++;
		}
		for (int i=9; i>=0; i--) {
			while (xNum[i]-- > 0 && yNum[i]-- > 0) {
                answer.append(i);
			}
		}
        
		return answer.toString().equals("")? "-1" : (answer.toString().startsWith("0")? "0" : answer.toString());
	}
}
```

<br>

# Wrong

```java
class Solution {
    public String solution(String X, String Y) {
		StringBuilder answer = new StringBuilder();
		long[] xNum = new long[10];
		long[] yNum = new long[10];

		for (char num : X.toCharArray()) {
			xNum[num-'0'] ++;
		}
		for (char num : Y.toCharArray()) {
			yNum[num-'0'] ++;
		}
		for (int i=9; i>=0; i--) {
			if (xNum[i] > 0 && yNum[i] > 0) {
				answer.append(i*Math.min(xNum[i], yNum[i]));
			}
		}
		return answer.toString().equals("")? "-1" : (Integer.parseInt(answer.toString()) == 0? "0" : answer.toString());
	}
}
```

## wrong point 
runtime error
```java
(Integer.parseInt(answer.toString()) == 0? "0" : answer.toString());
```

