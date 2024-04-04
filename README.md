CC 13.1 Doubly Link List

```
# Doubly Linked List Implementation in Java

This Java program implements a doubly linked list data structure. It provides methods to add elements to the start, end, or at a specified position in the list, and to display the contents of the list.

## Node Class:

```java
class Node {
    int data;
    Node prev;
    Node next;

    public Node(int data) {
        this.data = data;
        this.prev = null;
        this.next = null;
    }
}
```

## DoublyLinkedList Class:

```java
class DoublyLinkedList {
    Node head;

    public void addToStart(int data) {
        Node newNode = new Node(data);
        newNode.next = head;
        if (head != null) {
            head.prev = newNode;
        }
        head = newNode;
    }

    public void addToPosition(int position, int data) {
        if (position < 1) {
            System.out.println("Invalid position.");
            return;
        }

        Node newNode = new Node(data);
        if (position == 1) {
            newNode.next = head;
            if (head != null) {
                head.prev = newNode;
            }
            head = newNode;
        } else {
            Node current = head;
            for (int i = 1; i < position - 1 && current != null; i++) {
                current = current.next;
            }
            if (current == null) {
                System.out.println("Invalid position.");
                return;
            }
            newNode.next = current.next;
            newNode.prev = current;
            if (current.next != null) {
                current.next.prev = newNode;
            }
            current.next = newNode;
        }
    }

    public void addToEnd(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
        } else {
            Node current = head;
            while (current.next != null) {
                current = current.next;
            }
            current.next = newNode;
            newNode.prev = current;
        }
    }

    public void display() {
        Node current = head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }
}
```

## Makainode Class (Main):

```java
public class Makainode {
    public static void main(String[] args) {
        DoublyLinkedList list = new DoublyLinkedList();

        list.addToStart(3);
        list.addToStart(2);
        list.addToStart(1);

        list.addToPosition(1, 5);
        list.addToPosition(2, 10);

        list.addToEnd(7);

        list.display();
    }
}
```

## Usage:

1. **Compile and Run:**
   - Compile the `Makainode.java` file using `javac Makainode.java`.
   - Run the compiled program using `java Makainode`.

2. **Add Elements:**
   - Use `addToStart(int data)` to add an element to the start of the list.
   - Use `addToPosition(int position, int data)` to add an element at a specified position.
   - Use `addToEnd(int data)` to add an element to the end of the list.

3. **Display Contents:**
   - Use `display()` method to display the contents of the list.

## Contribution:

Contributions are welcome! Feel free to submit bug reports, feature requests, or pull requests.

## Author:

- Mychal Q. Redoblado 
