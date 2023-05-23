# [Programmers] 호텔 대실

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/155651



> ### Solution

```java
public int solution(String[][] book_time) {
		int answer = 0;

		List<Booking> bookingList = new ArrayList<>();
		for (String[] book : book_time)
			bookingList.add(new Booking(book[0], book[1]));

		bookingList.sort(Comparator.comparingInt(o -> o.startTime));

		List<Integer> roomList = new ArrayList<>();
		for (Booking booking : bookingList) {
			
		}




		return answer;
	}

	class Booking {
		int startTime;
		int endTime;

		public Booking(String start, String end) {
			this.startTime = Integer.parseInt(start.replace(":", ""));
			this.endTime = Integer.parseInt(end.replace(":", ""));
		}
	}
```
