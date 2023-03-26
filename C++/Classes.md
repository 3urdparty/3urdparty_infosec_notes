### member initializer list:
```c++
:elem{new double[s]}, sz{s}
```
### Subscript funciton
```c++
double& operator[](int i) { return elem[i]; }
```

```c++
class Vector { 
public:
	Vector(int s) :elem{new double[s]}, sz{s} { } 
	double& operator[](int i) { return elem[i]; } int size() { return sz; }

private:  
double∗ elem; // pointer to the elements int sz; // the number of elements

// construct a Vector  
// element access: subscripting

};
```