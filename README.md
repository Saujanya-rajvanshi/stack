# stack
- [basic](#basic)
- [ADT](#ADT)
- [stack representation](#stack-representation)
- [arithmetic expression](#arithmetic-expression)
- [recursion](#recursion)
- [tower of hanoi](#tower-of-hanoi)

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


###### recursion 
---

## 🔹 What is Recursion?

* **Recursion** is a programming technique where a **function calls itself**.
* Used to solve a problem by **breaking it into smaller sub-problems**.
* Based on **divide and conquer** approach.

---

## 🔹 Principles of Recursion

1. **Base Case**
   → Condition where recursion **stops** (to avoid infinite calls).
2. **Recursive Case**
   → Function calls itself with a **smaller input**.
3. **Same Pattern**
   → Each sub-problem must follow the **same logic**.
4. **Progress Toward Base Case**
   → Every call moves closer to the base case.
---

## 🔹 Advantages

* Simple and clean code
* Best for problems like factorial, Fibonacci, tree traversal

## 🔹 Disadvantages

* More memory (uses stack)
* Slower than iteration
* Risk of stack overflow

---

## 🔹 Factorial using Non-Recursive (Iterative) Method

```cpp
#include <stdio.h>

int factorial(int n)
{
    int i, fact = 1;
    for(i = 1; i <= n; i++)
    {
        fact = fact * i;
    }
    return fact;
}

int main()
{
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);

    if(n < 0)
        printf("Invalid input");
    else
        printf("Factorial = %d", factorial(n));

    return 0;
}
```

## 🔹 Factorial using **Recursive Method**

```c
#include <stdio.h>

int factorial(int n)
{
    if(n == 0)        // Base case
        return 1;
    else
        return n * factorial(n - 1);   // Recursive call
}

int main()
{
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);

    if(n < 0)
        printf("Invalid input");
    else
        printf("Factorial = %d", factorial(n));

    return 0;
}
```
---

### 🔁 Recursion vs Iteration 

| **Attribute**      | **Recursion**                                                                 | **Iteration**                                                               |
|-------------------|--------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| **Definition**     | Calling a function repeatedly                                                 | Executing a block of code repeatedly                                         |
| **Format**         | A function calls itself until a base case is met                              | A loop runs as long as a condition is true                                   |
| **Speed**          | Slower due to stack usage                                                     | Faster since it avoids stack overhead                                        |
| **Termination**    | Ends when the base condition is satisfied                                     | Ends when the loop condition becomes false                                   |
| **Infinite Loop**  | Can crash the system due to stack overflow                                    | Executes endlessly but doesn’t crash the system                              |
| **Size of Code**   | Typically reduces code size                                                   | Often results in longer code                                                 |
| **Usability**      | Used only with functions (self-calling)                                       | Implemented using loop constructs (for, while, etc.)                         |

---

---

---

## 🔹 Types of Recursion 

### 1️⃣ Based on Function Call

**Direct Recursion**

* Function calls itself directly
* Example: factorial

**Indirect Recursion**

* Function calls another function which calls it back
* Example: A() → B() → A()

---

### 2️⃣ Based on Pending Operations

**Tail Recursion**

* Recursive call is the **last statement**
* Faster, optimizable

**Head Recursion**

* Recursive call happens **first**
* Slower, more stack use

---

### 3️⃣ Based on Structure

**Linear Recursion**

* Only **one recursive call**
* Example: factorial

**Tree Recursion**

* **Multiple recursive calls**
* Example: Fibonacci

---

## 🔹 One-Line Summary

* **Direct / Indirect** → who calls whom
* **Head / Tail** → pending work or not
* **Linear / Tree** → number of recursive calls



##### tower of hanoi
---

## 🔹 Tower of Hanoi (Important Recursion Problem)

### 📌 Definition

Tower of Hanoi is a **mathematical puzzle** with:

* **3 pegs (A, B, C)**
* **N disks** of different sizes
* Smaller disk always placed **above larger disk**

---

## 🎯 Objective

Move **all disks from source peg (A) to destination peg (C)** using auxiliary peg (B)
**without breaking rules**

---

## 📏 Rules

1. Only **one disk** can be moved at a time
2. Only **top disk** can be moved
3. **No larger disk** on smaller disk

---

## 🔁 Recursive Idea

To move **N disks** from A → C using B:

1. Move **N−1 disks** from A → B using C
2. Move **largest disk** from A → C
3. Move **N−1 disks** from B → C using A

---

## ⏱ Time Complexity

* **T(n) = 2ⁿ − 1 moves**
* Time: **O(2ⁿ)**
* Space (recursion stack): **O(n)**

---

## 💡 Base Case

* If **n = 1**, move disk directly from source to destination

---

## 🔹 C Program: Tower of Hanoi (Recursive)

```c
#include <stdio.h>

void towerOfHanoi(int n, char from, char aux, char to) {
    // Base case
    if (n == 1) {
        printf("Move disk 1 from %c to %c\n", from, to);
        return;
    }

    // Step 1: move n-1 disks to auxiliary peg
    towerOfHanoi(n - 1, from, to, aux);

    // Step 2: move largest disk to destination
    printf("Move disk %d from %c to %c\n", n, from, to);

    // Step 3: move n-1 disks to destination peg
    towerOfHanoi(n - 1, aux, from, to);
}

int main() {
    int n;
    printf("Enter number of disks: ");
    scanf("%d", &n);

    towerOfHanoi(n, 'A', 'B', 'C');
    return 0;
}
```

---
