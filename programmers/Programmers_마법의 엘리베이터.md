# [Programmers] 마법의 엘리베이터



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/148653

> ### Solution

```java
class Solution {
    public int solution(int storey) {
		int answer = 0;
		int place;
		while (storey != 0) {
			place = storey % 10;
			
			if (
				(place > 5)
				|| ((place == 5) && (storey/10)%10 >= 5)
			) {
				storey += (10 - place);
				answer += (10 - place);
			} else {
				answer += place;

			}

			storey /= 10;
		}
		return answer;
	}
}
```

---

### Wrong

-> 각 자리의 수에서만 최소값을 체크. 전체의 최소값을 확인해야 한다 (ex) 999 -> ANSWER : 2

> 참고
> https://school.programmers.co.kr/questions/42026

```java
class Solution {
    public int solution(int storey) {
		int answer = 0;
		int place = 1;
		while (storey/place > 0) {
			int nowPlace = (storey % (place*10)) / place;

			if (nowPlace < 5) {
				answer += nowPlace;
			} else {
				answer += (1 + 10 - nowPlace);
			}

			storey -= nowPlace * place;
			place *= 10;
		}
		return answer;
	}
}
```

