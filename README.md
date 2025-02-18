# Deque
Deque implementation using Array
class Deque {
    private int arr[];
    private int front, rear, size, capacity;

    // Constructor
    public Deque(int capacity) {
        this.capacity = capacity;
        this.arr = new int[capacity];
        this.front = -1;
        this.rear = -1;
        this.size = 0;
    }

    // Check if deque is full
    public boolean isFull() {
        return size == capacity;
    }

    // Check if deque is empty
    public boolean isEmpty() {
        return size == 0;
    }

    // Insert at front
    public void insertFront(int data) {
        if (isFull()) {
            System.out.println("Deque Overflow! Cannot insert " + data);
            return;
        }
        if (isEmpty()) {
            front = rear = 0;
        } else {
            front = (front - 1 + capacity) % capacity;
        }
        arr[front] = data;
        size++;
        System.out.println("Inserted at front: " + data);
    }

    // Insert at rear
    public void insertRear(int data) {
        if (isFull()) {
            System.out.println("Deque Overflow! Cannot insert " + data);
            return;
        }
        if (isEmpty()) {
            front = rear = 0;
        } else {
            rear = (rear + 1) % capacity;
        }
        arr[rear] = data;
        size++;
        System.out.println("Inserted at rear: " + data);
    }

    // Delete from front
    public void deleteFront() {
        if (isEmpty()) {
            System.out.println("Deque Underflow! Cannot delete.");
            return;
        }
        System.out.println("Deleted from front: " + arr[front]);
        front = (front + 1) % capacity;
        size--;
    }

    // Delete from rear
    public void deleteRear() {
        if (isEmpty()) {
            System.out.println("Deque Underflow! Cannot delete.");
            return;
        }
        System.out.println("Deleted from rear: " + arr[rear]);
        rear = (rear - 1 + capacity) % capacity;
        size--;
    }

    // Get front element
    public int getFront() {
        if (isEmpty()) {
            System.out.println("Deque is empty!");
            return -1;
        }
        return arr[front];
    }

    // Get rear element
    public int getRear() {
        if (isEmpty()) {
            System.out.println("Deque is empty!");
            return -1;
        }
        return arr[rear];
    }

    // Display the deque
    public void display() {
        if (isEmpty()) {
            System.out.println("Deque is empty.");
            return;
        }
        System.out.print("Deque Elements: ");
        for (int i = 0; i < size; i++) {
            System.out.print(arr[(front + i) % capacity] + " ");
        }
        System.out.println();
    }
}

// Main class
public class DequeArray {
    public static void main(String[] args) {
        Deque deque = new Deque(5);

        deque.insertRear(10);
        deque.insertRear(20);
        deque.insertFront(5);
        deque.display();

        deque.deleteFront();
        deque.display();

        deque.insertFront(1);
        deque.insertRear(30);
        deque.insertRear(40);
        deque.display();

        deque.deleteRear();
        deque.display();

        System.out.println("Front Element: " + deque.getFront());
        System.out.println("Rear Element: " + deque.getRear());
    }
}
