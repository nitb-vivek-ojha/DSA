# LINKED LIST

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