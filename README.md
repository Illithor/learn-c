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
 
