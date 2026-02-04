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
#    Question 2: 2095. Delete the Middle Node of a Linked List
##   LeetCode Submission : https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/submissions/1907188660
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
    public ListNode deleteMiddle(ListNode head) {
        if (head == null || head.next == null) {
            return null;
        }

        int s = 0;
        ListNode d = head;

        while (d != null) {
            s++;
            d = d.next;
        }

        int mid = s / 2;

        ListNode f = head;
        int i = 0;

        while (i < mid - 1) {
            f = f.next;
            i++;
        }

        f.next = f.next.next;

        return head;
    }
}
```
#    Question 3: 3510. Minimum Pair Removal to Sort Array II
##    LeetCode Submission : 
```java
-- Coming Soon..
```
#    Question 4: 2816. Double a Number Represented as a Linked List
##    Submission Link : https://leetcode.com/problems/double-a-number-represented-as-a-linked-list/submissions/1907223441
```java
class Solution {
    public ListNode doubleIt(ListNode head) {
        head = reverse(head);

        int carry = 0;
        ListNode curr = head;

        while (curr != null) {
            int val = curr.val * 2 + carry;
            curr.val = val % 10;
            carry = val / 10;

            if (curr.next == null && carry > 0) {
                curr.next = new ListNode(carry);
                carry = 0;
                break;
            }

            curr = curr.next;
        }

        return reverse(head);
    }

    private ListNode reverse(ListNode head) {
        ListNode prev = null;
        while (head != null) {
            ListNode next = head.next;
            head.next = prev;
            prev = head;
            head = next;
        }
        return prev;
    }
}
```
#    Question 5:  2289. Steps to Make Array Non-decreasing
##    LeetCode Submission : https://leetcode.com/problems/steps-to-make-array-non-decreasing/submissions/1907527480
```java
class Solution {
    public int totalSteps(int[] nums) {
        int ans =0;
        Stack<int[]> st = new Stack<>();
        for(int i=nums.length-1; i>=0; i--){
            int c=0;
            while(!st.isEmpty() && st.peek()[0]<nums[i]){
                c = Math.max(c+1,st.peek()[1]);
                st.pop();
            }
            ans = Math.max(ans,c);
            st.push(new int[]{nums[i],c});
        }
        return ans;
    }
}
```
#    Question 6: 1019. Next Greater Node In Linked List
##    LeetCode Submission : https://leetcode.com/problems/next-greater-node-in-linked-list/submissions/1907552457
```java
class Solution {
    public int[] nextLargerNodes(ListNode head) {
        ArrayList<Integer> arr = new ArrayList<>();
        while(head != null){
            arr.add(head.val);
            head = head.next;
        }
        int[] nxt= new int[arr.size()];

        for(int i =0; i < arr.size(); i++){
            int j = i +1;
            while(j < arr.size() && arr.get(j) <= arr.get(i)){
                j++;
            }

            if(j < arr.size()){
                nxt[i] = arr.get(j);
            } else {
                nxt[i] = 0;
            }
        }

        return nxt;
    }
}
```
