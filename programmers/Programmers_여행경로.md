# [Programmers] 여행경로

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/43164



> ### Solution

```java
import java.util.*;
 
public class Solution {
    ArrayList<String> allRoute;     // 모든 도시를 방문했을 때 경로 
    int allCities;                  // 방문해야하는 도시의 개수
    
    public String[] solution(String[][] tickets) {
        
        allRoute = new ArrayList<>();
        allCities = tickets.length+1;

        HashMap<String, ArrayList<City>> eachCity = new HashMap<>();

        for(String[] t : tickets){
            if(eachCity.containsKey(t[0])){  // 기존에 존재하는 출발지
                eachCity.get(t[0]).add(new City(t[1]));

            } else {    // 새로운 출발지
                ArrayList<City> cities = new ArrayList<>();
                cities.add(new City(t[1]));

                eachCity.put(t[0], cities);
            }
        }
        // DFS start
        getNextRoute(eachCity, "ICN","ICN", 1);

        Collections.sort(allRoute);

        String[] answer = allRoute.get(0).split(" ");

        return answer;
    }
    public void getNextRoute(HashMap<String, ArrayList<City>> tickets, String depart, String route, int index){
        
        if(index == allCities){     // 모든 도시 방문 완료
            allRoute.add(route);
            return;
        }

        ArrayList<City> arrival = tickets.get(depart);      // 이 도시에서 갈 수 있는 도시들

        if(arrival == null) return;                         // 출발지로서 등장한 적이 없는 도시
        
        for(City c : arrival){
            if(!c.isVisited) {    // 아직 가지 않은/도착하지 않은 도시
                c.isVisited = true;
                getNextRoute(tickets, c.name, route+" "+c.name, index+1);
                c.isVisited = false;        // back tracking
            }
        }
    }
}
class City{
    String name;
    boolean isVisited;

    public City(String name) {
        this.name = name;
        this.isVisited = false;
    }
}
```



---



> ### Solution(실패)

```java
import java.util.*;

class Solution {
    public String[] solution(String[][] tickets) {
        // 시작점은 무조건 ICN
        String depart = "ICN";
        String arrival;

        int index = 0;
        String[] answer = new String[tickets.length+1];
        answer[index++] = depart;

        HashMap<String, ArrayList<City>> all = new HashMap<>();

        for(String[] t : tickets){
            
            if(all.containsKey(t[0])){  // 기존에 존재하는 출발지
                all.get(t[0]).add(new City(t[1]));

            } else {    // 새로운 출발지
                ArrayList<City> cities = new ArrayList<>();
                cities.add(new City(t[1]));

                all.put(t[0], cities);
            }
        }

        while(index != answer.length){
            arrival = getNextRoute(all, depart);     // (알파벳 순)으로 가장 빠른 도착지를 구함

            answer[index++] = arrival;

            depart = arrival;                       // 도착지에서 다시 검색

        }

        return answer;
    }

    public String getNextRoute(HashMap<String, ArrayList<City>> tickets, String depart){
        ArrayList<City> arrival = tickets.get(depart);

        Collections.sort(arrival);
        
        for(City c : arrival){
            if(!c.isVisited) {    // 아직 가지 않은/도착하지 않은 도시
                c.isVisited = true;
                return c.name;
            }
        }
        return "";
    }
}
class City implements Comparable<City>{
    String name;
    boolean isVisited;

    public City(String name) {
        this.name = name;
        this.isVisited = false;
    }

    @Override
    public int compareTo(City o) {      // 알파벳 순
        return this.name.compareTo(o.name);
    }
}
```

> ##### 실패 이유 
>
> ```java
> Assert.assertThat(s.solution(new String[][]{{"ICN", "A"}, {"ICN", "B"}, {"B", "ICN"}}), 
>                   is(new String[]{"ICN", "B", "ICN", "A"}));
> ```
>
> 탐색때부터 알파벳순으로 정렬해가다보니, **막힌 경로 발생** -> 백트래킹 방법을 사용해야할 듯 