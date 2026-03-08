import java.util.*;

public class question3 {

    static int n;
    static int[] color;
    static List<Integer>[] tree;
    static int maxSize;

    static void dfs(int node, Set<Integer> usedColors) {

        int c = color[node];

        if (usedColors.contains(c)) {
            return;
        }

        usedColors.add(c);

        maxSize = Math.max(maxSize, usedColors.size());

        for (int child : tree[node]) {
            dfs(child, usedColors);
        }

        usedColors.remove(c); // backtrack
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        n = sc.nextInt();

        int[] parent = new int[n + 1];

        for (int i = 1; i <= n; i++) {
            parent[i] = sc.nextInt();
        }

        color = new int[n + 1];

        for (int i = 1; i <= n; i++) {
            color[i] = sc.nextInt();
        }

        tree = new ArrayList[n + 1];

        for (int i = 1; i <= n; i++) {
            tree[i] = new ArrayList<>();
        }

        for (int i = 2; i <= n; i++) {
            tree[parent[i]].add(i);
        }

        int q = sc.nextInt();

        long ans = 0;
        long mod = 1000000007;

        for (int i = 0; i < q; i++) {

            int s = sc.nextInt();

            maxSize = 0;

            dfs(s, new HashSet<>());

            ans = (ans + maxSize) % mod;
        }

        System.out.println("ans"+ ans);
    }
}
