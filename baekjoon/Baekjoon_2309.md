# [BaekJoon#2309] 일곱 난쟁이



> ### Problem
>
> https://www.acmicpc.net/problem/2309



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();
        int total = 0;

        List<Integer> realDwarf = new ArrayList<>();
        for(int i=0; i<9; i++){
            realDwarf.add(Integer.parseInt(br.readLine()));
            total += realDwarf.get(i);
        }

        total -= 100;

        for(int i=0; i<realDwarf.size()-1; i++){
            for(int j=i+1; j<realDwarf.size(); j++){
                if(realDwarf.get(i)+realDwarf.get(j) == total){
                    realDwarf.remove(i);
                    realDwarf.remove(j-1);
                    break;
                }
            }
        }

        Collections.sort(realDwarf);

        for(int i : realDwarf){
            result.append(i+"\n");
        }
        System.out.println(result.toString());
    }
}

```
