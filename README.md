# C++ Notebook

## Contents

- [Preprocessor](#Preprocessor)
- [Main Function](#Main-Function)
- [Namespace](#Namespace)
- [Print in Console](#Print-in-Console)
- [Loop (Iteration)](#Loop)
- [Accept Input](#Accept-Input)
- [String](#String)
- [Array](#Array)
- [Vector](#Vector)
- [Constant](#Constant)
- [Struct](#Struct)
- [Class](#Class)
- [File IO](#File-IO)
- [Display Manipulator](#Display-Manipulator)
- [Recursion](#recursion)
- [Pointers](#pointer)
- [Dynamic Variable](#Dynamic-Variable)
- [Linked List](#Linked-List)

## Preprocessor<a name="Preprocessor"></a>

The preprocessor in C++ will run before the codes go into the compilor. It will remove comments and include dependencies/packages.

### Include dependencies

```
#include <iostream>
#include <string>
```

## Main Function<a name="Main-Function"></a>
- Codes to run when the programme starts.
- Returns 0 if the programme runs successfully.

```
int main() {
    // codes here

    return 0
}
```

## Namespace<a name="Namespace"></a>

To prevent conflict due to same name used in different packages, a namespace is used to distinguish packages.

### Using scope resolution operator

```
std::cout << "Hello World" << std::endl;
```

### Import namespace entirely

```
using namespace std;
cout << "Hello World" << endl;
```

### Import namespace for specific use

```
using namespace std::cout;
using namespace std::endl;

cout << "Hello World" << endl;
```


## Print in Console<a name="Print-in-Console"></a>

`<<` is called the insertation operator.

### Print without starting a new line at the end

```
cout << "Hello World";
```

### Print and start a new line at the end

```
cout << "Hello World" << endl;
```

## Loop (Iteration)<a name="Loop"></a>

### Enhanced `for` loop

Automatically loop over elements in an iterable object:

```
for (double &grade : gradeList) {
    // code here
    // ...
}
```

Note: The current looping element can be passed both by reference or by value. If passed by reference, we can make modification to it. The type need to be specified.

## Accept Input<a name="Accept-Input"></a>

`>>` is called the extraction operator.

### Assign a value to a variable

```
int score {0};
cin >> score;
```

### Accept multiple values at a time

```
int score1 {0};
int score2 {0};

cin >> score1 >> score2;
```

If the user type `100 98` and hit `enter`, `score1` will be `100` and `score2` will be `98` (the keyboard activities will be fed into a buffer, and then extracted character by character).

### Read line as string

```
#include <iostream>
#include <string>

using namespace std;

int main() {
    string strA;
    getline(cin,strA);
}
```

### Command line argument

```
int main(int argc, char *argv[]) {
    ...
}
```

`argc`: length of command line arguments input by the user
`argv`: an array of characters that stores all command line arguments

## String<a name="String"></a>

### C++ string

```
#include <string>
```

Get the length of a string.

```
int len = str.length();
```

Get substring.

```
string sub = str.substr(startIndex, n);
```

Delete a substring.

```
str.erase(startIndex, n);
```

Get the position of first occurrence of a certain substring.

```
int loc = str.find(substr);
int loc2 = str.find(substr,loc+1);
```

Reverse find, get the last occurrence of a substring.

```
int listLoc = str.rfind(substr);
```

Insert a string at the specified location.

```
str.insert(loc, "hello");
```

Replace a substring.

```
str.replace(startIndex, n, "hello");
```

### C string

```
#include <string.h>
```

![cstring](./img/cstring.png)

## Array<a name="Array"></a>

- The size need to be specified for an array.
- There will be no bound checking. If there is only 5 members in an array, `arr[5]` will return garbage data.

### Create an array

```
// set the size to be 40, initialize all values to be 0
int testScores [40] {};

// set the size to be 5, and initialize values accordingly
string grades [5] {"A+","A","A","A+","A"};
```

### Retrieve from array

```
cout << "First grade: " << grades[0] << endl;
```

## Vector<a name="Vector"></a>

### Create vector

```
#include <vector>
#include <string>

using namespace std;

vector<int> testScores {};

// initialize first 5 members to "A+"
vector<string> grades (5,"A+");
```

### Retrieve from vector

```
string firstGrade = grades.at(0)
```

If we use `at()` method, there will be bound checking. If the index is out of bound, an exception will be thrown.

### Add to vector

```
grades.push_back("A");
```

## Get vector size

```
grades.size();
```

### 2-D vector

Create 2-D vector

```
vector<vector<int>> studentScores {
    {98,100,96,90,89},
    {90,92,97,93,86}
};
```

Retrieve from 2-D vector

```
int firstStudentFirstGrade = studentScores.at(0).at(0);
```

## Constant<a name="Constant"></a>

A constant is a variable which the value could not be modified once initialized.

```
const int daysInYear = 365;
```

## Struct<a name="Struct"></a>

A struct is a collection of different variables, they can have the same or different types.

```
struct Account {
    double balance;
    string account_holder;
    string account_number;
};
```

Note: `;` at the ending curly brace of struct declaration is required.

In `C++`, a struct can contain not only member variables, but also member methods:

```
struct Account {
    double balance;
    string account_holder;
    string account_number;
    double interest_rate;

    double getInterest() {
        return balance * interest_rate;
    }
}
```

Additionally, you can use this to declare member method:

To be written inside the struct:

```
double getInterest();
```

To be written outside the struct:

```
double Account::getInterest() {
    return balance * interest_rate;
}
```

`::` is the scope resolution operator.

## Class 

### Class declaration
```
class Point {
    public:
        double getX() { 
            return x;
        }
        double getY() { 
            return y;
        }
        void setCoord(double s, double t) {
            x = s;
            y = t;
        }
        double distance(Point & p);
        void translate(Point & p);

    private:
        double x;
        double y;
}
```

Normally, member methods are made `public` while member variables are made `private` to avoid unexpected manipulation.

### Use classes from separated file

Classes are stored in `account.h` file.

At the beginning of `main.cpp` file, add this line:

```
#include 'account.h'
```

## File IO<a name="FILE-IO"></a>

`fstream` package need to be used.

```
#include <fstream>
```

### Write to file

```
ofstream fout; // create output stream
fout.open("data1.txt");

if(fout.fail()) {
    // if output stream fails, fout.fail() will return true
    cout << "Error in file opening" << endl;
    exit(1);
}
```

```
string outputStr = "Hello World";
fout << outputStr << endl;

fout.close();
```

Append mode:

```
fout.open("data2.txt",ios::app);
```

Use string variable as parameter in `open()` method:

```
fout.open(filename.c_str())
```

That's because `open()` only accepts C-string, not `string` object.

### Read from file

```
ifstream fin;
fin.open("data3.txt");

if(fin.fail()) {
    cout << "Error in file opening!" << endl;
    exit(1);
}
```

```
string x;
while(getline(fin,str)) {
    // keep reading from the file until EOF is reached
    cout << x << endl;
}
```

### Extraction from string

The `sstream` library need to be used.

```
#include <sstream>
```

```
string line = "apple orange banana";
string word;
istringstream line_in(line); // create string input stream

while(line_in >> word) {
    cout << word << endl;
}
```

The output of this program will be:

```
apple
orange
banana
```

## Display Manipulator<a name="Display-Manipulator"></a>

Display manipulators are used to set the format for the output in the screen. It is just for display purpose, the original data/variable will not be changed.

They are under the `std` namespace.

### `showpoint`, `fixed` and `scientific` manipulator

```
double e = 12.0
cout << showpoint << e << endl
```

Output: `12.0000`

```
double f = 0.135;
cout << fixed << f << endl;
cout << scientific << f << endl;
```

Output:

```
0.135000
1.350000e-01
```

Note: once the display manipulator is activated, all `float` and `double` nunbers will be formatted.

To stop the effect:

```
cout.unsetf(ios_base::floatfield);
```

### `setprecision` manipulator

Set decimal places to display.

`iomanip` library need to be imported.

```
#include <iomanip>
```

```
double b = 12.6587452;
cout << fixed << setprecision(2);
cout << b;
```

Note: `setprecision` need to be jointly used with `fixed` or `scientific`.

### `setw` and `setfill` manipulator

`iomanip` library need to be imported.

```
int x = 5;
int a = 3;
cout << setfill('*');
cout << setw(5) << x << setw(8) << a << endl;
```

Output:

```
****5*******3
```

Explaination:

This the width of `5` will be 5 spaces, with `5` aligned to the right (4 spaces padded before `5`). All unused spaces will be set to `*`.

### `left` and `right` manipulator

```
int x = 5;
cout << left;
cout << setfill('-');
cout << setw(5) << x << endl;
```

Output:

```
5----
```

## Recursion<a name="recursion"></a>

Recursion means a problem can be solved by dividing it to a smaller version of itself. 

Sometimes, recursion is easier for the developer to write and understand. However, it usually runs slower and use more memory than an equivalent iteration.

If the chain of recursive calls is excessively long, `stack overflow error` may occer (computation is out of memory).

![Recursion Example](img/recursion_exp.png)

Code:

```
int factorial(int num) {
    if (num == 0) {
        return 1; // base case
    }
    else {
        return num * factorial(num - 1); // general case, reduce to n - 1
    }
}
```

Properties for a recursion:

- Have one or more base case(s)
- The general cases must be able to reduce to base case

Conditions to avoid infinite recursion:

- Recursion called are smaller than the previous one
- There is one or more base case(s) without using recursive calls to terminate the recursion

### Example: Greatest common divisor (Euclidean algorithm)

Reference [Euclidean Algorithm](https://zh.wikipedia.org/zh-tw/%E8%BC%BE%E8%BD%89%E7%9B%B8%E9%99%A4%E6%B3%95)

Code:

```
int gcd(int x, int y) {
    if (y == 0) {
        return x;
    }

    else {
        return gcd(y, x%y);
    }
}
```

### Example: Fibonacci sequence

![Fibonacci Sequence](./img/fibonacci_seq.png)

Code:

```
int fib(int num) {
    if (num < 2) {
        return num; // base cases: 0 and 1
    }
    else {
        return fib(num - 1) + fib(num - 2); // general case
    }
}
```

### Example: Palindrome

Check whether a string is symmetric from the center.

Code:

```
bool is_palin(string s) {
    if (s.length() < 2) {
        return true; // base case, when there is only one or no character in the string
    }
    else {
        return (s[0] == s[s.length()-1]) && is_palin(s.substr(1,s.length()-2)); // check whether the first character equals to the last character. If not, directly return false. Otherwise, continue to work on the substring.
    }
}
```

### Example: Tower of Hanoi

![Tower of Hanoi](./img/tower_of_hanoi.png)

- Move the entire stack of circular disks to another rod. Two rods are empty at the beginning.
- Only one disk may be moved at a time.
- Removed disk must be placed on one of the rods.
- No disk may be placed on top of a smaller disk.
- Question: how many steps do we need if there are `n` disks on the original rod?

Code:

```
void move(int n,char src,char des,char tmp) {
    if (n == 1) {
        cout << "Move disk from " << src << "to " << des << endl;
    }
    else {
        move(n-1,src,tmp,des);
        move(1,src,des,tmp);
        move(n-1,tmp,des,src);
    }
}
```

## Pointers<a name="pointer"></a>

### Get address

The memory address of a variable can be accessed with the `&` sign:

```
int a = 1;
cout << &a;
```

This is also the method of "pass by reference" in functions.

### Declare and use a pointer

In addition to print the memory address, we can store it in a variable, which is called a pointer:

```
int a = 1;
int *addr_for_a;
addr_for_a = &a;

cout << addr_for_a;
```

Note: the `*` sign is used to declare a pointer. The type of the variable to "point to" must be specified. In this case, the pointer is for `int` only.

### Dereference
We can also get the value of the variable from address:

```
int a = 1;
int *addr_for_a;
addr_for_a = &a;

cout << "Address: " << addr_for_a << endl;
cout << "Value: " << *addr_for_a << endl;
```

The notation of `*<memory_addr>` is called dereference, getting the value from an address.

### Arrow notation

To chain the dereference notation with member methods/properties of a struct/class, we will need to use the bracket:

```
(*student_struct_addr).score = 100;
```

We can also use the arrow notation:

```
student_struct_addr -> score = 100;
```

### Initialize pointer to `NULL` address

```
Student *s = NULL;
```

## Dynamic Memory<a name="Dynamic-Variable"></a>

Dynamic memory means the memory is allocated or reallocated during the runtime (unlike static variables, there memories are assigned during the compilation).

### Use the `new` keyboard

```
int *a_addr;
a_addr = new int; // set the pointer to the address of a new int variable
*a_addr = 5;
cout << *a_addr + 3 << endl; // 8
```

### Pass by reference (with pointers)

```
void swap(int *x, int *y) {
    ...
}

int main() {
    int a=2,b=5;
    swap(&a,&b); // the & signs are required, because the pointer is expecting addresses
}
```

### Arrays

```
int a[4] = {1,2,3,4};
int *p = a; // as a is already an address, there is no need to use &

cout << *p << *(p+1) << *(p+2) << *(p+3) << endl;
// the array a will reserve four consecutive memory addresses starting from p, therefore we can just dereference each linked pointer to get the value.

cout << p[0] << p[1] << p[2] << p[3] << endl;
// this notation will have the same effect
```

### `nothrow` for dynamic array

This method of declaring a dynamic array will throw an error if the memory space is not enough:

```
Student *S = new Student[1000];
```

However, we can use this instead:

```
Student *S = (nothrow) new Student[1000];
// in case of insufficient space, all other pointers will point to NULL
```

### Life cycle of dynamic array

1. Insert an element:

```
int size = 4;
Product *temp; // create the pointer
temp = new Product[size];

for (int i=0;i<size;i++) { 
    temp[i]=ProductList[i];
}

delete [] ProductList; // delete the memory spaces taken by the unused array
```

Note: remember the `[]` before the pointer name when deleting the pointer.

2. Remove an element

```
// slotID is the index of the element to be deleted
void delete_product(Product *ProductList,int slotID,int size) {
    for(int i=slotID;i<size;i++) {
        ProductList[i] = ProductList[i+1];
    }
}
```

## Linked List<a name="Linked-List"></a>

Linked list allows insertion and removal of items at any point in the list in constant time (O(1)).

Basic type:

```
struct Product {
    string name;
    double price;
    Product *next; // point to the next item
}
```

Each item will have a pointer which points to the next element.

Head: the pointer variable that points to the first node(struct) in the list.

Initially, the `head` is initialized to `NULL`.

```
Product *head = NULL;
```

### Insertion

1. Create a new node
2. New node's next is the originally first node.
3. Change the `head` to the address of the new node.

```
Product * headInsert(Product *h, string n, double p) {
    Product *pNode = new Product;
    pNode -> name = n;
    pNode -> price = p;
    pNode -> next = h;
    h = pNode;
    return h;
}
```

Parameters: `*h` is the original `head`, `n` and `p` are the properties to be set for the newly-added struct.

The returned `h` is the new head(the address for the newly-added struct).

### Searching

1. Creat a pointer `current`(pointing to the current node which is being checked).
2. Initialize `current` with `head`.
3. Traverse the lined list by: `current = current -> next;`

```
void searchList(Product *head, string n) {
    // declare the current pointer
    Product *current;
    current = head;
    while(current != NULL) {
        if(current -> name == n)
            cout << current -> price << endl;
            
        // move to the next struct
        current = current -> next;
    }
}
```

Parameters: `*head` is the head of the linked list, `n` is the target string.

### Deletion

1. Create 2 pointers: `current` and `previous` (for singly linked list).
2. Search for the node to delete, and update the pointers: `previous -> next = current -> next;`(connect the previous node direcly to the subsequent node).
3. Delete the target node to free up memory space: `delete current`.

```
Product *current, *previous;
// initialize the previous to NULL, because the current should be the head
previous = NULL;
current = head;
string target = "xxxxx";

while(current != NULL) {
    // search first
    if(current -> name == target) {
        previous -> next = current -> next;
        delete current;
        break;
    }
    previous = current;
    current = current -> next;
}
```