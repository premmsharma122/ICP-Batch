#  Question 1: 2073. Time Needed to Buy Tickets
##  Leetcode Submission : https://leetcode.com/problems/time-needed-to-buy-tickets/submissions/1898606046
```java
class Solution {
    public int timeRequiredToBuy(int[] tickets, int k) {
        Deque<int[]> q = new LinkedList<>(); // [idx,val]
        for(int i=0; i<tickets.length; i++){
            q.add(new int[]{i,tickets[i]});
        }
        int c=0;
        while(!q.isEmpty()){
            int idx = q.peek()[0];
            int val = q.peek()[1];
            val--;
            c++;
            q.pollFirst();
            if(idx==k && val ==0){
                return c;
            }
            if(val>0){
                q.addLast(new int[]{idx,val});
            }
        }
        return 0;
      
    }
}
```
