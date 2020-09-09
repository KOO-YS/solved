# [Programmers] 키패드 누르기 



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/67256



> ### Solution

```java
class Solution {
    public String solution(int[] numbers, String hand) {
        StringBuffer answer = new StringBuffer();

        // 초기화
        int leftHand = 10;
        int rightHand = 12;


        for(int i : numbers){

            if( i == 1 || i == 4 || i == 7 ){
                answer.append('L');
                leftHand = i;

            } else if ( i == 3 || i == 6 || i == 9 ){
                answer.append('R');
                rightHand = i;

            } else {
                int distanceLeft = getDistance(leftHand, i);
                int distanceRight = getDistance(rightHand, i);

                if(distanceLeft > distanceRight){
                    answer.append("R");
                    rightHand = i;

                }else if(distanceLeft < distanceRight){
                    answer.append("L");
                    leftHand = i;

                } else {
                    if(hand.equals("right")) {
                        answer.append('R');
                        rightHand = i;
                    } else {
                        answer.append('L');
                        leftHand = i;
                    }
                }
            }
        }
        return answer.toString();
    }
    public int getDistance(int hand, int number){
        if( number == 0 ){ number = 11; }
        if( hand == 0 ){ hand = 11; }

        int handX = (hand-1)/3;
        int handY = (hand-1)%3;

        int numX = (number-1)/3;
        int numY = (number-1)%3;

        int distanceX = Math.abs(handX - numX);
        int distanceY = Math.abs(handY - numY);
        return distanceX + distanceY;
    }

}
```

