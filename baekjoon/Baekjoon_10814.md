# [BaekJoon#10814] 나이순정렬  



> ### Problem
>
> https://www.acmicpc.net/problem/10814



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main{

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());
        StringTokenizer token;

        User[] userList = new User[N];
        int idx = 0;
        while(N-->0){
            token = new StringTokenizer(br.readLine(), " ");
            userList[idx++] = new User(Integer.parseInt(token.nextToken()), token.nextToken());
        }
        Arrays.sort(userList);

        for(User user : userList){
            System.out.println(user.toString());
        }
    }

}
class User implements Comparable<User>{

    private static int autoIncrement = 1;
    int pk;
    int age;
    String name;

    public User(int age, String name) {
        this.pk = autoIncrement++;
        this.age = age;
        this.name = name;
    }

    @Override
    public String toString() {
        return age +" " + name;
    }

    @Override
    public int compareTo(User u) {
        if(this.age > u.age) return 1;
        else if(this.age < u.age) return -1;
        else if(this.age == u.age){
            if(this.pk > u.pk) return 1;
            else if(this.pk < u.pk) return -1;
        }
        return 0;
    }
}
```
