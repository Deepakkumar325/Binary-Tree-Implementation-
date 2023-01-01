# Binary-Tree-Implementation-


import java.util.*;

public class BinaryTreeQ {
    static class Node {
        int data;
        Node left;
        Node right;

        Node(int data) {
            this.data = data;
            this.left = null;
            this.right = null;
        }
    }

    static class BinaryTree {
        static int idx = -1;

        public static Node BulidTree(int nodes[]) { // Take a nodes and return root node
            idx++;
            if (nodes[idx] == -1) {
                return null;
            }
            Node newNode = new Node(nodes[idx]);
            newNode.left = BulidTree(nodes);
            newNode.right = BulidTree(nodes);
            return newNode;
        }
    }

//     // preorder

    public static void preorder(Node root) {
        if (root == null) {
            return;
        }
        System.out.print(root.data + " ");
        preorder(root.left);
        preorder(root.right);
    }

//     // inorder node

    public static void inorder(Node root) {
        if (root == null) {
            return;
        }
        inorder(root.left);
        System.out.print(root.data + " ");
        inorder(root.right);
    }

    // Postorder
    
    public static void postorder(Node root) {
        if (root == null) {
            return;
        }
        postorder(root.left);
        postorder(root.right);
        System.out.println(root.data + " ");
    }

//     // Level order

    public static void levelorder(Node root) {
        if (root == null) {
            return;
        }
        Queue<Node> q = new LinkedList<>();
        q.add(root);
        q.add(null);
        while (!q.isEmpty()) {
            Node currNode = q.remove();
            if (currNode == null) {
                System.out.println();
                if (q.isEmpty()) {
                    break;

                } else {
                    q.add(null);
                }
            } else {
                System.out.print(currNode.data + " ");
                if (currNode.left != null) {
                    q.add(currNode.left);
                }
                if (currNode.right != null) {
                    q.add(currNode.right);
                }
            }
        }
    }


       //count of Node 
       
    public static int countofNode(Node root) {
            if(root == null){
                return 0;
            }
            int leftNodes = countofNode(root.left);
            int rightNode = countofNode(root.right);
            // System.out.print(root.data);
            return leftNodes + rightNode + 1; // 
    }

//     //Sum of Node

    public static int sumofNode(Node root) {
        if(root == null){
            return 0;
        }
        int leftsum = sumofNode(root.left);
        int rightsum = sumofNode(root.right);
        return leftsum + rightsum + root.data;  
    }


//     // height of max root

    public static int heightofRoot(Node root) {
        if(root == null){
            return 0;
        }
        int leftheight = heightofRoot(root.left);
        int rightheight = heightofRoot(root.right);
        int Myheight =Math.max(leftheight, rightheight) + 1;
        return Myheight;
        
    }
    // Diameter 
    
    public static int  Diameter(Node root) {
        if(root == null){
            return 0;
        }
        int dai1 = Diameter(root.left);
        int dai2 = Diameter(root.right);
        int dai3=  heightofRoot(root.left) + heightofRoot(root.right) + 1;
        return Math.max(dai3 ,Math.max(dai2, dai3));

    }

    public static void main(String[]  args ) {
        int nodes[] = { 5,1,5 ,5 5,5};
        BinaryTree tree = new BinaryTree();
        Node root = tree.BulidTree(nodes);
        System.out.println(root.data);
        preorder(root);
        inorder(root);
        postorder(root);
        levelorder(root);

        System.out.println(countofNode(root));
        System.out.println(sumofNode(root));
        System.out.println(heightofRoot(root));
        System.out.println(Diameter(root));

    }
}
