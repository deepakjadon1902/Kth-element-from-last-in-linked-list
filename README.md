import java.util.Scanner;

class ListNode {
    int value;
    ListNode next;
    
    ListNode(int value) {
        this.value = value;
        this.next = null;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ListNode head = null, tail = null;
        
        // Read linked list
        while (true) {
            int value = scanner.nextInt();
            if (value == -1) break;
            ListNode newNode = new ListNode(value);
            if (head == null) {
                head = newNode;
                tail = newNode;
            } else {
                tail.next = newNode;
                tail = newNode;
            }
        }
        
        // Read k
        int k = scanner.nextInt();
        
        // Find kth element from last
        ListNode kthNode = findKthFromLast(head, k);
        
        if (kthNode != null) {
            System.out.println(kthNode.value);
        } else {
            System.out.println("Invalid k");
        }
        
        scanner.close();
    }
    
    public static ListNode findKthFromLast(ListNode head, int k) {
        ListNode first = head;
        ListNode second = head;
        
        // Move first k steps ahead
        for (int i = 0; i < k; i++) {
            if (first == null) {
                return null; // k is larger than the length of the list
            }
            first = first.next;
        }
        
        // Move both first and second until first reaches the end
        while (first != null) {
            first = first.next;
            second = second.next;
        }
        
        return second;
    }
}
