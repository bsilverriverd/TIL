# 2021-07-28
1. Ranged-Based for loop  

```
for(element-type element-name : array-name) {
  --snip--
}
```  
2. (Object) Initialization

+ equals // int e = 42 ;
+ braced(uniform) initialization // int f{ 42} ;
+ equals-plus-braces initialization // int g = { 42 } ;
+ parentheses // int h(42) ;  

Almost always use **braced** initialization!  
3. User-Defined Types

+ Enumerations

Scoped enum: enum class  
Unscoped enum: enum(for c compatability, unsafe)
+ Classes

Plain-Old-Data(POD) class  
Fully featured C++ Classes(Methods, Access Control, Constructors, Destructors)
+ Unions

Unsafe, Better not to use it

4. Thoughts

Probably reading the first chapter could fill in a few missing pieces.  
The book said that when initializing PODs, fields can be omitted only from right to left, and further explained that
certain example code won't compile but it did. I think in general it won't compile, it's just that the example code was a weak one.  
Perhaps rephrasing it as "only when fields are omitted from right to left will it be matched to the corresponding field" may be nicer.
