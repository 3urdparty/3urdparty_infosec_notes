Declaration:
```c++
struct Vector {
	int size;
	double* elem;
}
```
Initialization:
```c++
Vector v;
```
Function to initialize values `vector`:
```c++
void vector_init(Vector& v, int s) {
	v.elem = new double[s];
	v.sz = s;
}
```
