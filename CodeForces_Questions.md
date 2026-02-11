#  1794B - Not Dividing
##  Submission Link : https://codeforces.com/submissions/premm_122
##  Approach :
Step 1: Remove all 1s

If any element is 1, increase it to 2.

Because every number is divisible by 1, so it will always break the condition.

Step 2: Fix divisibility

Traverse from left to right.

For each i, check:

if arr[i] % arr[i-1] == 0


If divisible, increase arr[i] by 1.

One increment is always enough.
