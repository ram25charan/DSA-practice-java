#### **1. Problem Statement:**
You are given the head of a singly linked list.

The linked list may contain a cycle, meaning that at some point, a node’s next pointer points back to a previous node instead of null.

Your task is to find the node where the cycle begins.
If the linked list does not contain a cycle, return null.
You are not allowed to modify the linked list.
The solution must use constant extra space.

#### **2. Algorithm:**

**Step 1: Detect whether a cycle exists**

**Use two pointers:**

1. slow moves one step at a time.
2. fast moves two steps at a time.
3. If there is a cycle, slow and fast will eventually meet inside the cycle.
4. If fast or fast.next becomes null, there is no cycle, and we return null.

**Step 2: Find the starting point of the cycle**

**Once slow and fast meet:**

1. Place one pointer at the head of the linked list.
2. Keep the other pointer at the meeting point.
3. Move both pointers one step at a time.
4. The node where they meet again is the start of the cycle.

#### 

#### **Java code:**

class Solution {

&nbsp;   public ListNode detectCycle(ListNode head) {

&nbsp;       if (head == null || head.next == null) {

&nbsp;           return null;

&nbsp;       }



&nbsp;       ListNode slow = head;

&nbsp;       ListNode fast = head;



&nbsp;       // Step 1: Detect cycle

&nbsp;       while (fast != null \&\& fast.next != null) {

&nbsp;           slow = slow.next;

&nbsp;           fast = fast.next.next;



&nbsp;           if (slow == fast) {

&nbsp;               // Step 2: Find cycle start

&nbsp;               ListNode entry = head;

&nbsp;               while (entry != slow) {

&nbsp;                   entry = entry.next;

&nbsp;                   slow = slow.next;

&nbsp;               }

&nbsp;               return entry;

&nbsp;           }

&nbsp;       }
&nbsp;       // No cycle

&nbsp;       return null;

&nbsp;   }

}







