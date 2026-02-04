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
#    Question 2: 1823. Find the Winner of the Circular Game
##    LeetCode Submission : https://leetcode.com/problems/find-the-winner-of-the-circular-game/submissions/1903512316
```java
class Solution {
    public int findTheWinner(int n, int k) {

        ArrayList<Integer> arr = new ArrayList<>();

        for (int i = 1; i <= n; i++)
            arr.add(i);

        int idx = 0;

        while (arr.size() > 1) {
            idx = (idx + k - 1) % arr.size();
            arr.remove(idx);
        }

        return arr.get(0);
    }
}
```
#    Question 3: 3191. Minimum Operations to Make Binary Array Elements Equal to One I
##    LeetCode Submission : https://leetcode.com/problems/minimum-operations-to-make-binary-array-elements-equal-to-one-i/submissions/1901804270
```java
class Solution {
    public int minOperations(int[] nums) {
        int c=0;
        for(int i=0;i<nums.length;i++){
            if(nums[i]==0 && i+2>=nums.length){
                return -1;
            }
            else if(nums[i]==0 && i+2<nums.length){
                nums[i]=1;
                nums[i+1]=nums[i+1]==0?1:0;
                nums[i+2]=nums[i+2]==0?1:0;
                c++;
            }
        }
        return c;
    }
}
```
#    Question 4: 3589. Count Prime-Gap Balanced Subarrays
##    LeetCode Submission : https://leetcode.com/problems/count-prime-gap-balanced-subarrays/submissions/1899458514
```java
--Approach 1:
// class Solution {

//     public boolean help(int n) {
//         if (n < 2) return false;

//         for (int i = 2; i * i <= n; i++) {
//             if (n % i == 0) return false;
//         }
//         return true;
//     }

//     public int primeSubarray(int[] nums, int k) {
//         int ans = 0;

//         for (int i = 0; i < nums.length; i++) {

//             int c = 0;
//             int min = Integer.MAX_VALUE;
//             int max = Integer.MIN_VALUE;

//             for (int j = i; j < nums.length; j++) {

//                 if (help(nums[j])) {
//                     c++;
//                     min = Math.min(min, nums[j]);
//                     max = Math.max(max, nums[j]);
//                 }

//                 if (c >= 2 && max - min <= k) {
//                     ans++;
//                 }
//             }
//         }

//         return ans;
//     }
// }  _____HIT TLE_____
--Aproach 2:
class Solution {
    public int primeSubarray(int[] nums, int k) {
        int n = nums.length;
        int st = 0;
        int end = 0;
        int ans = 0;
        int prime = 0;

        int lastPrimePos = -1;
        int secondLastPrimePos = -1;

        Deque<Integer> min = new ArrayDeque<>();
        Deque<Integer> max = new ArrayDeque<>();

        while (st < n) {
            int num = nums[st];

            if (isPrime(num)) {
                prime++;
                secondLastPrimePos = lastPrimePos;
                lastPrimePos = st;

                while (!min.isEmpty() && min.peekLast() > num)
                    min.pollLast();
                min.addLast(num);

                while (!max.isEmpty() && max.peekLast() < num)
                    max.pollLast();
                max.addLast(num);
            }

            while (!min.isEmpty() && !max.isEmpty()
                    && max.peekFirst() - min.peekFirst() > k) {

                if (nums[end] == min.peekFirst()) min.pollFirst();
                if (nums[end] == max.peekFirst()) max.pollFirst();
                if (isPrime(nums[end])) prime--;
                end++;
            }

            if (prime >= 2) {
                ans += Math.max(0, secondLastPrimePos - end + 1);
            }

            st++;
        }
        return ans;
    }

    public boolean isPrime(int el) {
        if (el <= 1) return false;
        for (int i = 2; i * i <= el; i++) {
            if (el % i == 0) return false;
        }
        return true;
    }
}

```
#    Question 5: 950. Reveal Cards In Increasing Order
##    LeetCode Submission : https://leetcode.com/problems/reveal-cards-in-increasing-order/submissions/1898636863
```java
class Solution {
    public int[] deckRevealedIncreasing(int[] deck) {
        Queue<Integer> q = new LinkedList<>();
        Arrays.sort(deck);
        for(int i=0; i<deck.length; i++){
            q.add(i);
        }
        int ans[] = new int[deck.length];
        for(int a : deck){
            int idx=q.poll();
            ans[idx] = a;
            if(!q.isEmpty()){
                q.offer(q.poll());
            }
        }
        return ans;
    }
}
```
#    Question 6: 1696. Jump Game VI
##    Lee
