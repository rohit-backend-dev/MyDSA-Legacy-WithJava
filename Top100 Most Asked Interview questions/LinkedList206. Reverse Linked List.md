## **1️⃣ Iterative Approach (Your Code)**

```java
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode current = head;

        while (current != null) {
            ListNode nextNode = current.next; // store next
            current.next = prev;              // reverse pointer
            prev = current;                   // move prev
            current = nextNode;               // move current
        }

        return prev; 
    }
}
```

**Explanation:**

1. Start with `prev = null` and `current = head`.
2. Traverse the list.
3. For each node:

   * Store the next node.
   * Reverse the `next` pointer.
   * Move `prev` and `current` forward.
4. Return `prev` as the new head.

**Time Complexity:**

* **O(n)** — Each node is visited once.

**Space Complexity:**

* **O(1)** — Only a few pointers are used.

---

## **2️⃣ Using a Stack**

```java
import java.util.Stack;

class Solution {
    public ListNode reverseList(ListNode head) {
        if (head == null) return null;

        Stack<ListNode> stack = new Stack<>();
        ListNode current = head;

        // Push all nodes to stack
        while (current != null) {
            stack.push(current);
            current = current.next;
        }

        // Pop nodes from stack to rebuild reversed list
        ListNode newHead = stack.pop();
        current = newHead;

        while (!stack.isEmpty()) {
            current.next = stack.pop();
            current = current.next;
        }

        current.next = null; // last node's next should be null

        return newHead;
    }
}
```

**Explanation:**

1. Push all nodes onto a stack.
2. Pop nodes one by one and rebuild the linked list in reverse order.
3. Set the last node's `next` to `null`.

**Time Complexity:**

* **O(n)** — Each node is pushed and popped once.

**Space Complexity:**

* **O(n)** — Stack stores all nodes.

