# [Test] 01

> ### Solution

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Scanner;

class Person{
    int idx;
    char name;
    boolean isFast;
    int loseCnt;


    public Person(int idx, char name, boolean isFast, int loseCnt) {
        this.idx = idx;
        this.name = name;
        this.isFast = isFast;
        this.loseCnt = loseCnt;
    }

    @Override
    public String toString() {
        return name+" "+loseCnt;
    }
}
class Main {
    private static void solution(int numOfAllPlayers, int numOfQuickPlayers, char[] namesOfQuickPlayers, int numOfGames, int[] numOfMovesPerGame){
        List<Person> persons = new ArrayList<>();

        Arrays.sort(namesOfQuickPlayers);

        // setting
        int fastIdx = 0;
        for(int i=0; i<numOfAllPlayers; i++){

            char name = (char)('A'+i);
            boolean fast =  false;

            if(fastIdx < numOfQuickPlayers && name == namesOfQuickPlayers[fastIdx]){
                fast = true;
                fastIdx++;
            }
            persons.add(new Person(i, name, fast, 0));
        }

        // play
        peek = persons.remove(0);
        peek.loseCnt++;

        int start = 0;
        for(int i=0; i<numOfMovesPerGame.length; i++){
            start = play(persons, numOfMovesPerGame[i], numOfAllPlayers, start);
        }

        for(int i=0; i<persons.size(); i++){
            System.out.println(persons.get(i).toString());
        }
        System.out.println(peek.toString());

    }
    public static Person peek;
    public static int play(List<Person> persons, int move, int num, int start){
        int go = start + move;
        num--;

        if(go >= 0){        // 양수
            go %= num;
        } else {
            while(go<0){    // 음수
                go += num;
            }
        }

        Person temp = persons.get(go);
        if(temp.isFast) {       // 빠른 친구
            peek.loseCnt++;
        } else {
            persons.add(go, peek);
            persons.remove(go+1);
            peek = temp;
            peek.loseCnt++;
        }

        return go;
    }

    private static class InputData {
        int numOfAllPlayers;
        int numOfQuickPlayers;
        char[] namesOfQuickPlayers;
        int numOfGames;
        int[] numOfMovesPerGame;
    }

    private static InputData processStdin() {
        InputData inputData = new InputData();

        try (Scanner scanner = new Scanner(System.in)) {
            inputData.numOfAllPlayers = Integer.parseInt(scanner.nextLine().replaceAll("\\s+", ""));

            inputData.numOfQuickPlayers = Integer.parseInt(scanner.nextLine().replaceAll("\\s+", ""));
            inputData.namesOfQuickPlayers = new char[inputData.numOfQuickPlayers];
            System.arraycopy(scanner.nextLine().trim().replaceAll("\\s+", "").toCharArray(), 0, inputData.namesOfQuickPlayers, 0, inputData.numOfQuickPlayers);

            inputData.numOfGames = Integer.parseInt(scanner.nextLine().replaceAll("\\s+", ""));
            inputData.numOfMovesPerGame = new int[inputData.numOfGames];
            String[] buf = scanner.nextLine().trim().replaceAll("\\s+", " ").split(" ");
            for(int i = 0; i < inputData.numOfGames ; i++){
                inputData.numOfMovesPerGame[i] = Integer.parseInt(buf[i]);
            }
        } catch (Exception e) {
            throw e;
        }

        return inputData;
    }

    public static void main(String[] args) throws Exception {
        InputData inputData = processStdin();

        solution(inputData.numOfAllPlayers, inputData.numOfQuickPlayers, inputData.namesOfQuickPlayers, inputData.numOfGames, inputData.numOfMovesPerGame);
    }
}
```

