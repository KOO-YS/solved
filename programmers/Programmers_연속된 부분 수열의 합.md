# [Programmers] 연속된 부분 수열의 합



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/178870
>



> ### Solution

```java
class Solution {
    public int[] solution(int[] sequence, int k) {
		int[] answer = new int[2];

		int sum = 0;

		int front = 0;	// 부분 수열의 첫 인덱스
		int end = 0;	// 부분 수열의 마지막 인덱스 + 1

		int length = sequence.length;

		while (end < sequence.length) {
			sum += sequence[end];
			end++;

			if (sum > k) {
				while (sum > k) {
					sum -= sequence[front];
					front++;
				}
			}

			if (sum ==  k) {
				if (length > end-front-1) {
					length = end-front-1;
					answer[0] = front;
					answer[1] = end-1;
				}
			}
		}
		return answer;
	}
}
```

---

> ### Wrong
- O(n^2) 가 발생하기 때문 
- 투포인터 또는 누적합 개념 공부해볼 것

```java
class Solution {
    public int[] solution(int[] sequence, int k) {
		int[] answer = new int[2];
		answer[0] = 0;
		answer[1] = 1001;

		for (int i=0; i<sequence.length; i++) {
			int value = 0;
			int index = i;
			while (index < sequence.length && value < k) {
				value += sequence[index];
				if (value == k && (index - i) < (answer[1] - answer[0])) {
					answer[1] = index;
					answer[0] = i;
				}
				index++;
			}
		}
		return answer;
	}
}
```
