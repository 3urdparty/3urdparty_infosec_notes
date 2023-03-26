Pointer point to memory adresses.
They can be declared like this:
```c++
char* p;
```
To make the pointer point to an element in an array, we can initialise it to the adress of an element:
```c++
char* p = &v[3];
```
To get the contents of the pointer:
```c++
char x = *p;
```

## Declarations
```c++
T a[n]; //array of n Ts  
T∗ p;   //Pointer to T
T& r;   //Reference to T
T f(A); //function taking an argument of type A returning result of type T
```

## Null point
Pointer always points to an object, when it doesn't the pointer has the value `nullptr`.