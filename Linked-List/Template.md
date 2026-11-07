## WHAT IS A LINKED LIST
> A Linked List is a linear data structure that consists sequence of nodes. Each node consists two parts: Data & Next. The Data is the actual value and Next is a reference to subsequent node in the sequence.

## WHY IS IT USEFUL 
> Linked List data structure has a dynamic size. It can grow or shrink it's size as per requirement. Unlike Array which has a static size.


## REAL WORLD APPLICATIONS OF LINKED LIST
1. `Web Browser`: The forward and backward buttons use a doubly linked list to let you navigate your recent page history.

2. `Image Viewers`: Viewing the next or previous image in an album utilizes sequential node navigation.

3. `OS Memory Management`: Keeping track of free or allocated memory blocks using a free-list representation.

## COMMON OPERATIONS AND THEIR TIME COMPLEXITY
| Operation | Time Complexity |
|----------|-------|
| Access/Search | O(N) |
| Insertion at Head | O(1) |
| Insertion at Tail | O(N) or O(1) (If tail reference is present) |
| Deletion at Head | O(1) |
| Deletion at Tail | O(N) |

## QUESTIONS
| Question | Level |
|----------|-------|
| [Remove Nth Node From End of List (9)](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/) | Medium |
| [Delete a Node (No Head) (237)](https://leetcode.com/problems/delete-node-in-a-linked-list/submissions/2186924949/) | Medium |
| [Delete a Node in doubly LL](https://www.geeksforgeeks.org/problems/delete-node-in-doubly-linked-list/1) | Easy |
| [Reverse Doubly LL](https://www.geeksforgeeks.org/problems/reverse-a-doubly-linked-list/1) | Easy |
| [Reverse Linked List 2 (9)](https://leetcode.com/problems/reverse-linked-list-ii/description/) | Medium |
| [Add two numbers (2)](https://leetcode.com/problems/add-two-numbers/) | Medium |
| [Odd Even Linked List (328)](https://leetcode.com/problems/odd-even-linked-list/description/) | Medium |
| [Sort Linked List of 0s, 1s, 2s](https://www.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/1) | Medium |
| [Palindrome Linked List (234)](https://leetcode.com/problems/palindrome-linked-list/description/) | Easy |
| [Add 1 to Linked List Number](https://www.geeksforgeeks.org/problems/add-1-to-a-number-represented-as-linked-list/1) | Medium |
| [Intersection of Two Linked List (160)](https://leetcode.com/problems/intersection-of-two-linked-lists/description/) | Easy |
| [Middle of Linked List (876)](https://leetcode.com/problems/middle-of-the-linked-list/description/) | Easy |

## PATTERNS
> Insert a Node before Key
```Java
class Solution{
    public static void main(String[] args){

        // Special case: if the key is at the head
        if (head == null) {
            return null;
        }
        if (head.data == key) {
            Node newNode = new Node(newData);
            newNode.next = head;
            return newNode;
        }

        // Initialize current and previous pointers
        Node curr = head;
        Node prev = null;

        // Traverse the list to find the key
        while (curr != null && curr.data != key) {
            prev = curr;
            curr = curr.next;
        }

        // If the key was found
        if (curr != null) {
            Node newNode = new Node(newData);
            prev.next = newNode;
            newNode.next = curr;
        }
    }
}
```