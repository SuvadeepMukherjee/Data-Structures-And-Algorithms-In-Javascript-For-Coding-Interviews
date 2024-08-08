## Linked Lists

A Linked List is a data structure which store data in an ordered manner implemented using node objects (we will have a custom class that defined the Node object ) . Each Node will have a next pointer which points to the node representing the next element in the sequence 

![Linked List](../assets/Singly Linked List.png)

Implementation of a Single Linked List ;- 

```js
class ListNode {
    constructor(val) {
        this.val = val;
        this.next = null;
    }
}

(function main() {
    let one = new ListNode(1);
    let two = new ListNode(2);
    let three = new ListNode(3);
    one.next = two;
    two.next = three;
    let head = one;
    

    console.log(head.val);
    console.log(head.next.val);
    console.log(head.next.next.val);

}());
```

Note -> We will want to keep a reference to the head because the head is the only node from where we can reach all elements in the Linked List