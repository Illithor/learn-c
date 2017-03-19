# C Programming language

## Week 1
1. When you are doing some recursion on n and want to keep the origin value of n in somewhere, do not do like below:
 ```c
 int fn(int n, int acc) {
   int num = n;
   // and you do recursion on n here
   // calling fn(n - 1, acc)
   // you think you keep the origin number well in num
 }
 // and call fn(n, acc) somewhere
 
 // The reason it fails is that num changes with n every time when a new fn is called.
 ```
 Instead, make a new parameter that keeps the origin value of n like so:
 ```c
  int fn(int n, int ori, int acc) {
   // and you do recursion on n here
   // calling fn(n - 1, ori, acc)
   // you think you keep the origin number well in num
 }
 
 // and call fn(n, n, acc) instead
 ```
 
2. Mutation is when you change some initialized value. `That is illegal!`    
 The solution is to create a new `int` or something else to keep the number.
 For example:
 ```c
 int seq(int old, int new, int acc) {
  if(new == 0) {
    new = readnat(); // ERROR! You cannot give new a new value!
    return seq(old, new, acc);
  } ...
  }
 ```
 To solve the problem:
 ```c
 int seq(int old, int new, int acc) {
  if(new == 0) {
    int n_new = readnat(); // Pay attention!
    return seq(old, n_new, acc);
  } ...
  }
 ```
 
## Week 2
1. A better way to achieve a cond:
```c
int main(int x) {
  if (x > 0) {
    return true;
  } else {
    return false;
  }
}
```
The code above can be writen as following:
```c
int main(int x) {
  return (x > 0);
}
```
2. What does it print?
```c
int main(void) {
  int x = 0;
  int y = 2;
  printf("%d", printf("%d", y));
  if ((x = y - 1)) {
    printf("%d", x = x + 2);
  }
  if (x) {
    y *= y;
    printf("%d", y);
  }
  printf("\n");
}
```
 => 2134


## Week 8
 1. Don't forget the null terminator!    
  (But this is for strings only. If we are asked to return a array, we don't need to put a null terminator at th end.)
 ```c
char *repeat(const char *s) {
  int len = strlen(s);
  char *re = malloc((2 * len + 1) * sizeof(char));
  
  for (int i = 0; i < len; ++i) {
    re[i] = s[i];
    re[i + len] = s[i];
  }
  re[len * 2] = '\0'; // never forget this line!!!
  return re;
}
 ```
 2. Don't forget to multiply the size!
 ```c
 *re =  realloc(re, new_length * sizeof(int)); // time the size!!!
 ```
