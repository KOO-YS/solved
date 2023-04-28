# [Programmers] 옹알이 (2)



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/133499

> ### Solution

```java
class Solution {
    public static String[] able = new String[] {"aya", "ye", "woo", "ma"};
	public static String[] disable = new String[] {"ayaaya", "yeye", "woowoo", "mama"};
	public int solution(String[] babbling) {
		int answer = 0;
		int index = 0;
		boolean flag;

		while (index < babbling.length) {
			flag = true;
			String word = babbling[index];
			
			for (String d : disable) {
				if (word.contains(d)) {
					flag = false;
					break;
				}
			}
			if (flag) {
				for (String a : able) {
					word = word.replace(a, " ");
					if (word.trim().length() == 0) {
						answer++;
						break;
					}
				}
			}

			index++;
		}

		return answer;
	}
}
```

