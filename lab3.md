# Lab Report 3
## ```LinkedListExample.java``` ```append()``` (Original code)
```
public void append(int value) {
  if(this.root == null) {
    this.root = new Node(value, null);
    return;
  }
  // If it's just one element, add if after that one
  Node n = this.root;
  if(n.next == null) {
    n.next = new Node(value, null);
    return;
  }
  // Otherwise, loop until the end and add at the end with a null
  while(n.next != null) {
    n = n.next;
    n.next = new Node(value, null);
  }
}
```
## Test That Will Not Induce a Fail
```
@Test
public void testAppendTwoElements(){
  LinkedList list = new LinkedList();
  list.append(1);
  list.append(2);

  assertEquals(1, list.root.value);
  assertEquals(2, list.root.next.value);
}
```
Output:

![IMAGE](testpass.png)
## Test That Will Induce a Fail
```
public void testAppendThreeElements(){
  LinkedList list = new LinkedList();
  list.append(1);
  list.append(2);
  list.append(3);

  assertEquals(1, list.root.value);
  assertEquals(2, list.root.next.value);
  assertEquals(3, list.root.next.next.value);
}
```
Output:

![IMAGE](testfail.png)

Bug: The issue with the ```append()``` method is the while loop for linked lists with more than 1 element. The loop attempts to add a new Node when it reaches a node which has null for its next value. However, it continues to loop and initializes a next value for each iterated node. Therefore, it loops infinitely since a node will always have a next value before it is checked if it is null.

## Fixed Code
```
public void append(int value) {
  if(this.root == null) {
    this.root = new Node(value, null);
    return;
  }
        
  Node n = this.root;
        
  while(n.next != null) {
    n = n.next;
  }
        
  n.next = new Node(value, null);
}
```
This fixes the issue of appending onto linked lists with more than 1 element because the while loop will iterate until it reaches a node without a next, exits the loop, then initializes the new next node at the end of the list.
