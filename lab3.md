#Lab Report 3
##```LinkedListExample.java``` ```append()``` (Original code)
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
##Test That Will Not Induce a Fail
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
##Test That Will Induce a Fail
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


