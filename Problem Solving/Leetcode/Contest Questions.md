
## Date : 03/08/2024
### Q1. [Find the Number of Winning Players](https://leetcode.com/contest/biweekly-contest-136/problems/find-the-number-of-winning-players/)

```java
class Solution {
    public int winningPlayerCount(int n, int[][] pick) {
        int cnt = 0;

        Map<Integer, Integer>[] res = new HashMap[n];

        for(int i=0; i<n; i++){
            res[i] = new HashMap<>(); 
        }

        for(int[] game: pick){
            int player = game[0];
            int color = game[1];
            res[player].put(color, res[player].getOrDefault(color, 0) + 1);
        }

        for(int i=0; i<n; i++){
            for(int count : res[i].values()){
                if(count > i){
                    cnt++;
                    break;
                }
            }
        }

        return cnt;
    }
}
```