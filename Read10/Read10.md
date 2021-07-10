# Read: Stacks & Queues


**Stacks and Queues**
* What is a Stack?
  - *Stack* - data structure that consists of Nodes
    * *Nodes* - each Node references the next Node in the stack
  - Stack terminology:
    * *Push* - Nodes or items that are put into the stack are pushed
    * *Pop* - Nodes or items that are removed from the stack are popped
    * *Top* - top of the stack. When you push something to the stack it will go on top.
    * *Peek* - view the value of the top Node in the stack
    * *IsEmpty* - returns true when stack is empty otherwise returns false
    * *top.next* -  when you pop something from the stack, you pop the current top and set the next top
    * *FILO* (First In Last Out) - the first item added in the stack will be the last item popped out of the stack
    * *LIFO* (Last In First Out) - that the last item added to the stack will be the first item popped out of the stack
    * Push O(1) - pushing a Node onto a stack is an O(1) operation. Adding a Node will push it into the stack by assigning it as the new top, with its next property equal to the original top.
    * Pop O(1) - popping a Node off a stack is the action of removing a Node from the top, and the top Node will be re-assigned to the Node that lives below and the top Node is returned to the user
    * Peek O(1) - inspecting the top Node of the stack
    * IsEmpty O(1) - pseudocode for it: 
      ALGORITHM isEmpty()
     // INPUT <-- none
     // OUTPUT <-- boolean

     return top = NULL

  - Queue terminology:
    * *Enqueue* - Nodes or items that are added to the queue
    * *Dequeue* - Nodes or items that are removed from the queue
    * *Front* - the front/first Node of the queue
    * *Rear* - the rear/last Node of the queue
    * *Peak* - view the value of the front Node in the queue
    * *IsEmpty* - returns true when queue is empty otherwise returns false
    * *FIFO* (First In First Out) - the first item in the queue will be the first item out of the queue
    * *LILO* (Last In Last Out) - the last item in the queue will be the last item out of the queue
    * Enqueue O(1) - the enqueue action is when an item is added to a queue
    * Dequeue O(1) - the dequeue action is when an item is removed from a queue
    * Peek O(1) - inspecting the front Node of the queue, and you want to check the isEmpty before hand
    * IsEmpty O(1) - pseudocode for it:
      ALGORITHM isEmpty()
      // INPUT <-- none
      // OUTPUT <-- boolean

      return front = NULL

