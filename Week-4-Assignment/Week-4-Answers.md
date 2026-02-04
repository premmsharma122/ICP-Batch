#  Question 1: 1290. Convert Binary Number in a Linked List to Integer
##  LeetCode Submission : https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/submissions/1907174625
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public int getDecimalValue(ListNode head) {
        int ans=0;
        while(head != null){
            ans= ans*2+head.val;
            head = head.next;
        }
        return ans;
    }
}
```
