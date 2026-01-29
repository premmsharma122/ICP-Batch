#  Question 1:
##  Submission Link :
```java
```
#  Question 2: Find Mirror Score of a String
##  Submission Link : https://leetcode.com/problems/find-mirror-score-of-a-string/submissions/1900608152
```java
import java.util.*;

class Solution {
    public long calculateScore(String s) {
        int n = s.length();
        boolean[] used = new boolean[n];
        Map<Character, Deque<Integer>> map = new HashMap<>();
        long score = 0;

        for (int i = 0; i < n; i++) {
            char c = s.charAt(i);
            char mirror = (char) ('z' - (c - 'a'));

            if (map.containsKey(mirror) && !map.get(mirror).isEmpty()) {
                int j = map.get(mirror).pollLast();
                used[j] = true;
                used[i] = true;
                score += i - j;
            } else {
                map.computeIfAbsent(c, k -> new ArrayDeque<>()).add(i);
            }
        }
        return score;
    }
}

```
#    Question 3:
##    Submission Link :
```java

```
#    Question 4: Shortest Subarray to be Removed to Make Array Sorted
##    Submission Link : https://leetcode.com/problems/shortest-subarray-to-be-removed-to-make-array-sorted/submissions/1900611838
```java
class Solution {
    public int findLengthOfShortestSubarray(int[] arr) {
        int n = arr.length;
        int right = n - 1;

        while (right > 0 && arr[right - 1] <= arr[right]) {
            right--;
        }

        if (right == 0) return 0;

        int ans = right;
        int left = 0;

        while (left < n) {
            if (left > 0 && arr[left] < arr[left - 1]) break;

            while (right < n && arr[left] > arr[right]) {
                right++;
            }

            ans = Math.min(ans, right - left - 1);
            left++;
        }

        return ans;
    }
}

```
#    Question 5: Find the Number of Subarrays Where Boundary Elements Are Maximum
##    Submission Link : https://leetcode.com/problems/find-the-number-of-subarrays-where-boundary-elements-are-maximum/submissions/1900614137
```java
import java.util.*;

class Solution {
    public long numberOfSubarrays(int[] nums) {
        Deque<int[]> stack = new ArrayDeque<>();
        long res = 0;

        for (int x : nums) {
            int cnt = 1;

            while (!stack.isEmpty() && stack.peek()[0] < x) {
                stack.pop();
            }

            if (!stack.isEmpty() && stack.peek()[0] == x) {
                cnt += stack.peek()[1];
                res += stack.peek()[1];
                stack.pop();
            }

            stack.push(new int[]{x, cnt});
            res++;
        }

        return res;
    }
}

```
