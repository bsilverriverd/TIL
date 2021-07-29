# 2021-07-30
1. Value Categories

+ **lvalue**: Any value with a name
+ **rvalue**: Any value that is not an lvalue
+ use **std::move** in <utility> header cast to rvalue

2. Interfaces
  
+ To achieve runtime polymorphism
+ No interface keyword in cpp
+ use virtual keyword to allow derived class to override function
+ Always declare a default virtual destructor to prevent memory leaks
+ Implementation inheritance is considered anti-pattern

3. Templates
  
+ To achieve compile-time polymorphism
