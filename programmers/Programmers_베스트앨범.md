# [Programmers] 베스트앨범



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42579



> ### Solution

```java
import java.util.*;

class Solution {
    public int[] solution(String[] genres, int[] plays) {
        // 장르별 재생횟수
        Map<String, Integer> maps = new HashMap<>();

        for(int i=0; i<genres.length; i++){
            String key = genres[i];
            if(maps.containsKey(key)){
                maps.put(key, maps.get(key)+plays[i]);		// 장르 재생횟수 누적
            } else {
                maps.put(key, plays[i]);					// 새로운 장르 초기화
            }
        }

        // 노래목록
        Music[] music = new Music[genres.length];
        for(int i=0; i<genres.length; i++){
            music[i] = new Music(i, genres[i], plays[i]);
        }

        /*
            정렬 순서
            1. 장르 재생 횟수 내림차순
            2. 노래 재생 횟수 내림차순
            3. 노래 고유 번호 오름차순
        */
        Arrays.sort(music, new Comparator<Music>() {
            @Override
            public int compare(Music o1, Music o2) {
                if(maps.get(o1.genre) < maps.get(o2.genre)) return 1;
                else if(maps.get(o1.genre) > maps.get(o2.genre)) return -1;
                else return o1.compareTo(o2);
            }
        });

        // 장르별 포함횟수
        Map<String, Boolean> includes = new HashMap<>();
        List<Integer> album = new ArrayList<>();
        for(int i=0; i<music.length; i++){
            Music now = music[i];

            if(includes.containsKey(now.genre)){
                if(includes.get(now.genre)) continue;       // 이미 2회 이상 등장한 장르

                includes.put(now.genre, true);              // 장르가 2번째 등장
            } else {
                includes.put(now.genre, false);             // 장르가 처음 등장
            }
            album.add(now.num);
        }
        System.out.println(Arrays.toString(album.toArray()));

        // int[] 배열로 변환
        int[] answer = new int[album.size()];
        for(int i=0; i<answer.length; i++){
            answer[i] = album.get(i);
        }

        return answer;
    }
    class Music implements Comparable<Music>{
        int num;
        String genre;
        int each;

        public Music(int num, String genre, int each) {
            this.num = num;
            this.genre = genre;
            this.each = each;
        }
        @Override
        public int compareTo(Music o) {
            return o.each - each;
        }
    }
}
```

