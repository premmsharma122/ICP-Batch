#  Question 1 : Range Minimum Query
```java
class GfG {
    static int st[];

    // Build Segment Tree
    public static int[] constructST(int arr[], int n) {

        st = new int[4 * n];
        build(arr, 0, n - 1, 0);
        return st;
    }

    static void build(int arr[], int start, int end, int idx) {

        // Leaf node
        if (start == end) {
            st[idx] = arr[start];
            return;
        }

        int mid = (start + end) / 2;

        // Left subtree
        build(arr, start, mid, 2 * idx + 1);

        // Right subtree
        build(arr, mid + 1, end, 2 * idx + 2);

        // Store minimum
        st[idx] = Math.min(st[2 * idx + 1], st[2 * idx + 2]);
    }

    // Range Minimum Query
    public static int RMQ(int st[], int n, int l, int r) {

        return query(st, 0, n - 1, l, r, 0);
    }

    static int query(int st[], int start, int end, int l, int r, int idx) {

        // Complete overlap
        if (l <= start && end <= r)
            return st[idx];

        // No overlap
        if (end < l || start > r)
            return Integer.MAX_VALUE;

        // Partial overlap
        int mid = (start + end) / 2;

        return Math.min(
                query(st, start, mid, l, r, 2 * idx + 1),
                query(st, mid + 1, end, l, r, 2 * idx + 2)
        );
    }
}
````
#  Question 2: Sum of Query II
```java
class Solution {
    int st[];
    void buildst(int arr[], int n){
        st = new int[4*n];
        build(arr,0,n-1,0);
    }
    void build(int arr[], int start, int end, int idx){
        if(start==end){
            st[idx]= arr[start];
            return;
        }
        int mid = (start+end)/2;
        build(arr,start,mid,2*idx+1);
        build(arr,mid+1,end,2*idx+2);
        st[idx] = st[2*idx+1] + st[2*idx+2];
    }
    int query(int start, int end, int l, int r, int idx){

        if(l <= start && end <= r)
            return st[idx];
        if(end < l || start > r)
            return 0;
        int mid = (start+end)/2;
        return query(start,mid,l,r,2*idx+1) +
               query(mid+1,end,l,r,2*idx+2);
    }
    List<Integer> querySum(int n, int arr[], int q, int queries[]) {
        buildst(arr,n);
        List<Integer> ans = new ArrayList<>();
        for(int i=0; i<q; i++){
            int l = queries[2*i]-1;
            int r = queries[2*i+1]-1;

            int tmp = query(0,n-1,l,r,0);
            ans.add(tmp);
        }
        return ans;
    }
}
```
