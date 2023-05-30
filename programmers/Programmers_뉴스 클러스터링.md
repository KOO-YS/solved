# [Programmers] 뉴스 클러스터링



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/17677



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(String str1, String str2) {

		// 두 글자씩 끊어서 다중집합 만들기
		List<String> splitByTwoLetter1 = new ArrayList<>();
		List<String> splitByTwoLetter2 = new ArrayList<>();

		for (int i=0; i<str1.length()-1; i++) {
			if (Character.isAlphabetic(str1.charAt(i)) && Character.isAlphabetic(str1.charAt(i + 1)))
				splitByTwoLetter1.add(""+ Character.toUpperCase(str1.charAt(i)) + Character.toUpperCase(str1.charAt(i + 1)));
		}
		for (int i=0; i<str2.length()-1; i++) {
			if (Character.isAlphabetic(str2.charAt(i)) && Character.isAlphabetic(str2.charAt(i+1)))
				splitByTwoLetter2.add(""+ Character.toUpperCase(str2.charAt(i)) + Character.toUpperCase(str2.charAt(i+1)));
		}

		// 공집합
		if (splitByTwoLetter1.isEmpty() && splitByTwoLetter2.isEmpty())
			return 65536;

		// 합집합 & 교집합 체크
		int index1 = 0;
		int index2 = 0;

		Collections.sort(splitByTwoLetter1);
		Collections.sort(splitByTwoLetter2);

		long intersection = 0;
		long union = splitByTwoLetter1.size() + splitByTwoLetter2.size();

		while (index1 < splitByTwoLetter1.size() && index2 < splitByTwoLetter2.size()) {
			String word1 = splitByTwoLetter1.get(index1);
			String word2 = splitByTwoLetter2.get(index2);

			if (word1.equals(word2)) {
				intersection ++;
				index1 ++;
				index2 ++;
			} else if (word1.compareTo(word2) > 0) {
				index2 ++;
			} else {
				index1 ++;
			}
		}
		union -= intersection;

		return (int) ((intersection * 65536) / union);
	}
}
```

