# tricore-clang
This is tricore clang frontend.
When I learn tricore llvm, I cannot find the matched frontend.
So I just add some patch, it work with tricore-llvm project.
Enjoy yourself.
## Help

```
// main.c
int main()
{
  int a_int;
  a_int = 1;
  char b_char;
  b_char = 'c';
  short c_short;
  c_short = 1;
  long d_long;
  d_long = 2;
  long long e_ll;
  e_ll = 3;
  struct x {
    char x_a;
    char x_b;
  };
  struct x x_struct;
  x_struct.x_a = 3;
#ifdef __TRICORE__
  int pi;
  pi = 2;
#else
  int* p;
  p = &a_int;
#endif
  return 0;
}
```
I just test to produce llvm ir
```
$ clang --target=tricore -c main.c -S -emit-llvm -o main.ll
```
or
```
$ clang --target=tricore-unknown-linux-gnu -c main.c -S -o main.s
```
## Author
Huizhan Yi
