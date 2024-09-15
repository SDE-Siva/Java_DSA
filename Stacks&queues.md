# Stacks & Queues Questions :

### 1 . [Implement stack using array](https://www.geeksforgeeks.org/problems/implement-stack-using-array/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=implement-stack-using-array)

Explanation:

push(): Insert the element in the stack.

pop(): Remove and return the topmost element of the stack.

top(): Return the topmost element of the stack

size(): Return the number of remaining elements in the stack.

```java
class MyStack {
    private int[] arr;
    private int top;

    public MyStack() {
        arr = new int[1000];
        top = -1;
    }

    public void push(int x) {
        top++;
        arr[top] = x;
    }

    public int pop() {
        if(top == -1){
            return -1;
        }
       top--;
       return arr[top + 1];
    }
}
```

### 1 . [Implement Queue using array](https://www.geeksforgeeks.org/problems/implement-queue-using-array/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=implement-queue-using-array)

```java
class MyQueue {

    int front, rear;
	int arr[] = new int[100005];

    MyQueue()
	{
		front=0;
		rear=0;
	}

	void push(int x)
	{
	    arr[rear] = x;
	    rear++;
	}

	int pop()
	{
		if(rear == front ){
		    return -1;
		}

		int popElement = arr[front];
		front++;
		return popElement;
	}
}
```

### 3 . [Implement Stack using Linked List](https://www.geeksforgeeks.org/problems/implement-stack-using-linked-list/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=implement-stack-using-linked-list)

```java
class MyStack {
    // class StackNode {
    //     int data;
    //     StackNode next;
    //     StackNode(int a) {
    //         data = a;
    //         next = null;
    //     }
    // }
    StackNode top;

    // Function to push an integer into the stack.
    void push(int a) {
        StackNode newNode = new StackNode(a);
        newNode.next = top;
        top = newNode;
    }

    // Function to remove an item from top of the stack.
    int pop() {
        if(top == null){
            return -1;
        }
        StackNode temp = top;
        top = top.next;
        temp.next = null;
        return temp.data;
    }
}

class stack {
  private class stackNode {
    int data;
    stackNode next;
    stackNode(int d) {
      data = d;
      next = null;
    }
  }
  stackNode top;
  int size;
  stack() {
    this.top = null;
    this.size = 0;
  }
  public void stackPush(int x) {
    stackNode element = new stackNode(x);
    element.next = top;
    top = element;
    System.out.println("Element pushed");
    size++;
  }
  public int stackPop() {
    if (top == null) return -1;
    int topData = top.data;
    stackNode temp = top;
    top = top.next;
    return topData;
  }
  public int stackSize() {
    return size;
  }
  public boolean stackIsEmpty() {
    return top == null;
  }
```

### 4 . [Implement Queue using Linked List](https://www.geeksforgeeks.org/problems/implement-queue-using-linked-list/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=implement-queue-using-linked-list)

```java
class MyQueue
{
    QueueNode front, rear;

    //Function to push an element into the queue.
	void push(int a)
	{
        if(front == null){
            QueueNode newNode = new QueueNode(a);
            newNode.next = null;
            front = newNode;
            rear = newNode;
        }else{
            QueueNode newNode = new QueueNode(a);
            rear.next = newNode;
            rear = newNode;
        }
	}

    //Function to pop front element from the queue.
	int pop()
	{
	    if(front == null ){
	        return -1;
	    }
        QueueNode temp = front;
        front = front.next;
        temp.next = null;
        return temp.data;
	}
}

import java.util.*;

class QueueNode
{
    int val;
    QueueNode next;
    QueueNode(int data)
    {
       val = data;
       next = null;
    }
}


class Queue
{
    QueueNode Front = null, Rear = null;
    int size = 0;

boolean Empty()
{
    return Front == null;
}
int Peek()
{
    if(Empty())
     {  System.out.println("Queue is Empty");
        return -1;
     }
    else
      return Front.val;
}
void Enqueue(int value)
{
    QueueNode Temp;
    Temp = new QueueNode(value);
    if (Temp == null)  //When heap exhausted
        System.out.println("Queue is Full");
    else
    {
        if (Front == null)
        {
            Front = Temp;
            Rear = Temp;
        }
        else
        {
            Rear.next = Temp;
            Rear = Temp;
        }
        System.out.println(value+" Inserted into Queue ");
        size++;
    }
}
void Dequeue()
{
    if (Front == null)
        System.out.println("Queue is Empty");
    else
    {
        System.out.println(Front.val+" Removed From Queue");
        QueueNode Temp = Front;
        Front = Front.next;
        size--;
    }
}
```

### 5 . [Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/description/)

```java
class MyStack {
    Queue<Integer> q;
    public MyStack() {
        q = new LinkedList<>();
    }

    public void push(int x) {
        q.add(x);
        for(int i=1; i< q.size(); i++){
            q.add(q.remove());
        }
    }

    public int pop() {
       return q.remove();
    }

    public int top() {
        return q.peek();
    }

    public boolean empty() {
       return q.isEmpty();
    }
}
```
