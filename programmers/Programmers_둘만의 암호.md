# [Programmers] 둘만의 암호



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/155652



> ### Solution

```java
class Solution {
    public String solution(String s, String skip, int index) {
		StringBuilder answer = new StringBuilder();

		int[] exception = new int[26];
		for (int i=0; i<skip.length(); i++) {
			exception[skip.charAt(i) - 'a']++;
		}

		for (int i=0; i<s.length(); i++) {
			int count = 0;
			int alphabetInt = s.charAt(i) - 'a';

			while (count < index) {
				alphabetInt = (++ alphabetInt)%26;
				if (exception[alphabetInt] == 0) {
					count++;
				}
			}
			answer.append((char) (alphabetInt + 'a'));
		}
		return answer.toString();
	}
}
```

