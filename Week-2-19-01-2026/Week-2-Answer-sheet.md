#  Minimum String Length After Removing Substrings leetcodde no 2696
##  Leetcode Submission : https://leetcode.com/problems/minimum-string-length-after-removing-substrings/submissions/1905097914
```java
--- Approach 1: 
class Solution {
    public int minLength(String s) {
        boolean found = true;

        while (found) {
            found = false;
            for (int i = 0; i + 1 < s.length(); i++) {
                String c = s.substring(i, i + 2);
                if (c.equals("AB") || c.equals("CD")) {
                    s = s.substring(0, i) + s.substring(i + 2);
                    found = true;
                    break; 
                }
            }
        }
        return s.length();
    }
}
----- Approach 2:
class Solution {
    public int minLength(String s) {
        StringBuilder sb = new StringBuilder();
        for(char a : s.toCharArray()){
            sb.append(a);
            int n = sb.length();
            if(n>=2){
                char a1 = sb.charAt(n-2);
                char b = sb.charAt(n-1);

                if((a1=='A' && b =='B') || (a1=='C' && b=='D')){
                    sb.delete(n-2,n);
                }
            }
        }
        return sb.length();
    }
}
```
