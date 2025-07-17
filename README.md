import java.util.*;

class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode() {}
    TreeNode(int val) { this.val = val; }
    TreeNode(int val, TreeNode left, TreeNode right) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> list = new ArrayList<>();
        Queue<TreeNode> q = new LinkedList<>();
        if (root == null) return list;
        q.offer(root);
        while (!q.isEmpty()) {
            int n = q.size();
            List<Integer> sublist = new ArrayList<>();
            for (int i = 0; i < n; i++) {
                TreeNode node = q.poll();
                sublist.add(node.val);
                if (node.left != null) q.offer(node.left);
                if (node.right != null) q.offer(node.right);
            }
            list.add(sublist);
        }
        return list;
    }
}

public class Main {
    public static void main(String[] args) {
        // Sample tree:
        //     1
        //    / \
        //   2   3
        //  / \
        // 4   5

        TreeNode root = new TreeNode(1,
                            new TreeNode(2,
                                new TreeNode(4),
                                new TreeNode(5)),
                            new TreeNode(3));

        Solution sol = new Solution();
        List<List<Integer>> res = sol.levelOrder(root);

        for (List<Integer> level : res) {
            System.out.println(level);
        }
    }
}
