# 2021-07-28
1. References

+ A more safer and convenient version of a pointer(interchangable)
+ Cannot be easily assigned to null and cannot be reseated
+ Use pointers when ypu must change the value what the reference type refers to

2. Object storage duration, lifetime

+ The object’s **storage duration begins**, and storage is allocated.
+ The object’s constructor is called.
+ The object’s **lifetime begins**.
+ You can use the object in your program.
+ The object’s **lifetime ends**.
+ The object’s destructor is called.
+ The object’s **storage duration ends**, and storage is deallocated.

3. Kinds of Storage Duration

+ Automaic storage duration: Allocated at the beginning of an enclosing code block, and it’s deallocated at the end.
+ Static storage duration: Allocated when the program starts and deallocated when the program stops.
+ Thread-local storage duration
+ Dynamic storage duration: Allocated and deallocated on request

4. Exceptions

+ Exceptions inherit std::exception
+ Lets programs run faster when there ae no errors and behave better on failure
+ Treat destrctors as if it is noexcept
+ Resource Aquisition is Initialized(RAII) = Constructor Aquires, Destructor Releases(CADRe) 
