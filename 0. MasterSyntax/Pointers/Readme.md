# Pointers
## Definition:
A `pointer` is a variable that stores the memory address of another variable.
Think of a pointer as a "map" or "arrow" that points to where a value is stored in memory.
## Why Use Pointers?
- **Direct Memory Access**: Work directly with memory locations.
- **Dynamic Memory Allocation**: Create variables at runtime (e.g., using new or malloc).
- **Efficient Function Calls**: Pass large objects by reference instead of value.
- **Data Structures**: Implement structures like linked lists, trees, and graphs.

### Basic Syntax
```cpp
int* ptr; // Declares a pointer to an integer
```
int* means the pointer stores the memory address of an integer.
### How to Use Pointers
- Declare a Pointer:
```cpp
int* ptr;  // A pointer to an integer
```
- Assign a Memory Address: Use the address-of operator (&) to get the memory address of a variable.
```cpp
int x = 10;
int* ptr = &x;  // 'ptr' stores the address of 'x'
```
- Access the Value: Use the dereference operator (*) to get or modify the value at the pointer's address.

```cpp
int x = 10;
int* ptr = &x;  // Pointer to x
cout << *ptr;   // Outputs: 10 (value at address)
```
## Example 1: Basics of Pointers
```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 20;
    int* ptr = &num; // Pointer to 'num'

    cout << "Value of num: " << num << endl;          // 20
    cout << "Address of num: " << &num << endl;       // Memory address
    cout << "Value stored in ptr: " << ptr << endl;   // Address of 'num'
    cout << "Value at ptr: " << *ptr << endl;         // 20
    return 0;
}
```
## How Pointers Work in Memory
Imagine a memory map:

Variable `num` is stored at memory address `0x1000`, with value `20`.
Pointer `ptr` stores `0x1000`, and `*ptr `accesses the value at that address.

## Detailed Topics and Examples
1. ### Pointer Basics
Declaring, assigning, and accessing pointers.
## Example 2: Modifying a Value via a Pointer

```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 50;
    int* ptr = &num;

    cout << "Before: " << num << endl; // 50
    *ptr = 100; // Change the value of num via the pointer
    cout << "After: " << num << endl;  // 100
    return 0;
}
```
2. ## Null Pointers
A pointer that doesn’t point to anything is called a `null pointer`.
Use `nullptr` to initialize it safely.
## Example 3: Using Null Pointers

```cpp
#include <iostream>
using namespace std;

int main() {
    int* ptr = nullptr;  // Initialize as null
    if (ptr == nullptr) {
        cout << "Pointer is null!" << endl;
    }
    return 0;
}
```
3. ### Pointers and Arrays
An array name acts like a pointer to its first element.
## Example 4: Accessing an Array via a Pointer

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {10, 20, 30};
    int* ptr = arr; // Pointer to the first element

    for (int i = 0; i < 3; i++) {
        cout << *(ptr + i) << " "; // Access array elements
    }
    return 0;
}
```
4. ### Pointer Arithmetic
Add or subtract integers to move the pointer.
## Example 5: Pointer Arithmetic

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {10, 20, 30};
    int* ptr = arr;

    cout << *ptr << endl;       // 10
    cout << *(ptr + 1) << endl; // 20
    cout << *(ptr + 2) << endl; // 30
    return 0;
}
```
5. ### Pointers and Functions
Pass pointers to functions to modify variables.
## Example 6: Passing Pointers to Functions

```cpp
#include <iostream>
using namespace std;

void increment(int* ptr) {
    (*ptr)++; // Increment the value
}

int main() {
    int num = 10;
    increment(&num);
    cout << "After increment: " << num << endl; // 11
    return 0;
}
```
6. ### Dynamic Memory Allocation
Allocate memory at runtime using new.
## Example 7: Allocating Memory Dynamically

```cpp
#include <iostream>
using namespace std;

int main() {
    int* ptr = new int; // Dynamically allocate memory
    *ptr = 25;
    cout << "Value: " << *ptr << endl; // 25

    delete ptr; // Free the memory
    return 0;
}
```
7. ### Smart Pointers (Modern C++)
Use smart pointers like `unique_ptr` and `shared_ptr` for safe memory management.
## Example 8: Using Smart Pointers

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    unique_ptr<int> ptr = make_unique<int>(42);
    cout << "Value: " << *ptr << endl; // 42
    return 0;
}
```