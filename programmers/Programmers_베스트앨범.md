# [Programmers] 베스트앨범



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42579



> ### Solution

```java
class Solution {
    public int[] solution(String[] genres, int[] plays) {
        int[] answer = {};

        Map<String, Integer> maps = new HashMap<>();

        for(int i=0; i<genres.length; i++){
            String key = genres[i];
            if(maps.containsKey(key)){
                maps.put(key, maps.get(key)+plays[i]);
            } else {
                maps.put(key, plays[i]);
            }
        }

        Music.Genre[] g = new Music.Genre[maps.size()];
        for(int i=0; i<maps.size(); i++){
//            g[i] = new Music.Genre(maps.)
        }

        Music[] music = new Music[genres.length];
        for(int i=0; i<genres.length; i++){
//            music[i] = new Music(i, )
        }


        return answer;
    }
    class Music implements Comparable<Music>{
        int num;
        Genre genre;
        int each;

        public Music(int num, Genre genre, int each) {
            this.num = num;
            this.genre = genre;
            this.each = each;
        }


        @Override
        public int compareTo(Music o) {
            return 0;
        }
        class Genre implements Comparable<Genre>{
            String name;
            int count;

            public Genre(String name, int count) {
                this.name = name;
                this.count = count;
            }

            @Override
            public int compareTo(Genre o) {
                return count - o.count;
            }
        }
    }
}
```

