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
