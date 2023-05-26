# [Programmers] 호텔 대실

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/155651



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(String[][] book_time) {
		List<Booking> bookingList = new ArrayList<>();
		for (String[] book : book_time)
			bookingList.add(new Booking(book[0], book[1]));

		bookingList.sort(Comparator.comparingInt(o -> o.startTime));

		List<Integer> roomList = new ArrayList<>();
		for (Booking booking : bookingList) {
			boolean hasRoom = false;

			Collections.sort(roomList);
			for (int i=0; i<roomList.size(); i++) {
				int lastTime = roomList.get(i);
				if (lastTime <= booking.startTime){
					roomList.set(i, booking.endTime+10);
					hasRoom = true;
					break;
				}
			}
			if (!hasRoom)
				roomList.add(booking.endTime+10);
		}
		return roomList.size();
	}

	class Booking {
		int startTime;
		int endTime;

		public Booking(String start, String end) {
			String[] splitStart = start.split(":");
			String[] splitEnd = end.split(":");
			this.startTime = Integer.parseInt(splitStart[0])*60 + Integer.parseInt(splitStart[1]);
			this.endTime = Integer.parseInt(splitEnd[0])*60 + Integer.parseInt(splitEnd[1]);
		}
	}
}
```

---

<br>

> ### Wrong 

```java
import java.util.*;

class Solution {
    public int solution(String[][] book_time) {
		int answer = 0;

		List<Booking> bookingList = new ArrayList<>();
		for (String[] book : book_time)
			bookingList.add(new Booking(book[0], book[1]));

		bookingList.sort(Comparator.comparingInt(o -> o.startTime));

		List<Integer> roomList = new ArrayList<>();
		for (Booking booking : bookingList) {
			boolean hasRoom = false;

			Collections.sort(roomList);
			for (int i=0; i<roomList.size(); i++) {
				int lastTime = roomList.get(i);
				if (lastTime <= booking.startTime){
					roomList.set(i, booking.endTime+10);
					hasRoom = true;
					break;
				}
			}
			if (!hasRoom)
				roomList.add(booking.endTime+10);
		}
		return roomList.size();
	}
    
    class Booking {
		int startTime;
		int endTime;

		public Booking(String start, String end) {
			this.startTime = Integer.parseInt(start.replace(":", ""));
			this.endTime = Integer.parseInt(end.replace(":", ""));
		}
	}
}
```
