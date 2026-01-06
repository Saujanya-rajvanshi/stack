# stack
- [basic](#basic)
- [ADT](#ADT)


## basic 

* A stack is a linear data structure.
* Elements in the stack can be inserted and deleted from one side only.
* It follows a particular order in which the operations are performed.
* The order may be LIFO(LastIn First Out) or FILO(First In Last Out).
* LIFO implies that the element that is inserted last,comes out first and FILO implies that the element that is inserted first, comes out last.
 

## ADT
```cpp
#include <iostream>
using namespace std;

#define MAX 5

int stack[MAX];
int top = -1;

// Push operation
void push(int x) {
    if (top == MAX - 1) {
        cout << "Stack Overflow\n";
        return;
    }
    else{
    top = top +1;
    stack[top] = x;
    cout << x << " pushed into stack\n";
    }
}

// Pop operation
void pop() {
    if (top == -1) {
        cout << "Stack Underflow\n";
        return;
    }
    top = top - 1;
    cout << stack[top] << " popped from stack\n";
}

// Peek operation
void peek() {
    if (top == -1) {
        cout << "Stack is empty\n";
        return;
    }
    cout << "Top element: " << stack[top] << endl;
}

// Display operation
void display() {
    if (top == -1) {
        cout << "Stack is empty\n";
        return;
    }
    cout << "Stack elements: ";
    for (int i = top; i >= 0; i--)
        cout << stack[i] << " ";
    cout << endl;
}

int main() {
    push(10);
    push(20);
    push(30);
    display();
    peek();
    pop();
    display();
    return 0;
}
```
