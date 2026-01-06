# stack
- [basic](#basic)
- [ADT](#ADT)
- [stack representation](#stack-representation)
- [arithmetic expression](#arithmetic-expression)


## basic 

* A stack is a linear data structure.
* Elements in the stack can be inserted and deleted from one side only.
* It follows a particular order in which the operations are performed.
* The order may be LIFO(LastIn First Out) or FILO(First In Last Out).
* LIFO implies that the element that is inserted last,comes out first and FILO implies that the element that is inserted first, comes out last.
 

## ADT

- [ADT using array](#ADT-array)
- [ADT using linked list](#ADT-linked-list)

### ADT array

```cpp
#include <iostream>
using namespace std;

#define MAX 5

int stack[MAX];
int top = -1;

// Push operation push(stack, item, top)
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

// Pop operation pop(stack, item, top)
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

### ADT linked list
```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

Node* top = NULL;

// Push operation
void push(int x) {
    Node* newNode = new Node();
    newNode->data = x;
    newNode->next = top;
    top = newNode;
    cout << x << " pushed into stack\n";
}

// Pop operation
void pop() {
    if (top == NULL) {
        cout << "Stack Underflow\n";
        return;
    }
    Node* temp = top;
    cout << temp->data << " popped from stack\n";
    top = top->next;
    delete temp;
}

// Peek operation
void peek() {
    if (top == NULL) {
        cout << "Stack is empty\n";
        return;
    }
    cout << "Top element: " << top->data << endl;
}

// Display operation
void display() {
    if (top == NULL) {
        cout << "Stack is empty\n";
        return;
    }
    cout << "Stack elements: ";
    Node* temp = top;
    while (temp != NULL) {
        cout << temp->data << " ";
        temp = temp->next;
    }
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

---

#### Time Complexity of Stack Operations

| **Operation**         | **Time Complexity** |
| --------------------- | ------------------- |
| `Push()`              | **O(1)**            |
| `Pop()`               | **O(1)**            |
| `Peek()`              | **O(1)**            |
| `Traversal / Display` | **O(N)**            |
| `isEmpty()`           | **O(1)**            |
| `isFull()`            | **O(1)**            |

---

###### stack representation 

## 📊 Stack representation

---

1. **Array Representation**
2. **Linked List Representation**

---

## **Array Representation of Stack**

* **TOP** → stores index of top element
* **N** → maximum size of stack

**Conditions**

* `TOP = -1` or `NULL` → Stack is **empty**
* `TOP = N` → Stack is **full**

**Operations**

* **Push** → increment TOP, insert element
* **Pop** → remove element at TOP, decrement TOP
* **Peek** → return top element

---

## **Linked List Representation of Stack**

* Uses **nodes (data + next)**
* **top pointer** points to first node

**Advantages**

* Dynamic size (no overflow until memory ends)
* Efficient memory use

---

## **Stack Operations (Linked List)**

* **push()**

  * Create new node
  * `new->next = top`
  * `top = new`

* **pop()**

  * Store `top` in temp
  * `top = top->next`
  * delete temp

* **peek()**

  * Display `top->data`

* **display()**

  * Traverse from `top` to `NULL`

* **isEmpty()**

  * `top == NULL`

---

## **Time Complexity**

* Push → **O(1)**
* Pop → **O(1)**
* Peek → **O(1)**
* Display → **O(N)**
* isEmpty → **O(1)**

---

###### arithmetic expression

## 📊 Arithmetic exprsion 
---

## 1️⃣ Infix Expression

**Definition:**
Operator is placed **between operands**.

**Example:**
`(a + b) * c / d`

**Rules:**

* Uses **precedence** and **associativity**
* Needs **parentheses** to control order
* Follows **BODMAS**

**Advantages:**

* Easy to read and understand
* Commonly used in mathematics

**Disadvantages:**

* Hard to evaluate by machine
* Requires parentheses

---

## 2️⃣ Prefix Expression (Polish Notation)

**Definition:**
Operator is placed **before operands**.

**Format:**
`operator operand1 operand2`

**Example:**
Infix: `(a + b) * c`
Prefix: `* + a b c`

**Rules:**

* No parentheses needed
* Evaluated **right to left**

**Advantages:**

* No ambiguity
* Easy for compilers

**Disadvantages:**

* Hard for humans to read

---

## 3️⃣ Postfix Expression (Reverse Polish Notation)

**Definition:**
Operator is placed **after operands**.

**Format:**
`operand1 operand2 operator`

**Example:**
Infix: `(a + b) * c`
Postfix: `a b + c *`

**Rules:**

* No parentheses needed
* Evaluated **left to right**
* Uses **stack**

**Advantages:**

* Easy evaluation using stack
* No precedence rules needed

**Disadvantages:**

* Less readable for humans

---

## Quick Comparison Table

| Expression | Operator Position | Parentheses | Evaluation   |
| ---------- | ----------------- | ----------- | ------------ |
| Infix      | Between operands  | Required    | Complex      |
| Prefix     | Before operands   | Not needed  | Right → Left |
| Postfix    | After operands    | Not needed  | Left → Right |



## RULES 

---

## 🔹 Operator Precedence ( highest → lowest)

`( )  >  ^  >  * / %  >  + −`

**Associativity:**

* `^` → **Right to Left**
* `* / % + −` → **Left to Right**

---

## 🔹 Stack Rules for Expression Evaluation (COMPARE ALL 3)

### 1️⃣ Infix Expression (Stack Evaluation Rule)

**Key idea:** Convert **Infix → Postfix/Prefix**, then evaluate.

**Rules (Conversion using stack):**

1. If **operand** → add to output
2. If **(** → push to stack
3. If **)** → pop until **(** is removed
4. If **operator**:

   * Pop from stack **while precedence(top) ≥ precedence(current)**
     (except `^` which is right associative)
   * Then push operator
5. Pop all remaining operators at end

👉 **Infix itself is NOT directly evaluated using stack**

---

### 2️⃣ Postfix Expression (Stack Evaluation Rule)

**Scan from LEFT → RIGHT**

1. If **operand** → push into stack
2. If **operator**:

   * Pop **operand2**
   * Pop **operand1**
   * Compute → `operand1 operator operand2`
   * Push result back
3. Final stack top = **answer**

📌 **Order matters**
`a b -` → `a − b`

---

### 3️⃣ Prefix Expression (Stack Evaluation Rule)

**Scan from RIGHT → LEFT**

1. If **operand** → push into stack
2. If **operator**:

   * Pop **operand1**
   * Pop **operand2**
   * Compute → `operator operand1 operand2`
   * Push result back
3. Final stack top = **answer**

📌 **Order matters**
`- a b` → `a − b`

---

## 🔹 One-Look Comparison (VERY IMPORTANT)

| Expression | Scan Direction | Uses Stack          | Operand Order    |
| ---------- | -------------- | ------------------- | ---------------- |
| Infix      | Left → Right   | For conversion only | Precedence based |
| Postfix    | Left → Right   | Yes                 | op1 then op2     |
| Prefix     | Right → Left   | Yes                 | op1 then op2     |

---

## 🔹TIP ⭐

* **Infix → always convert first**
* **Postfix → L → R**
* **Prefix → R → L**
* **Operator pops = 2 operands always**

