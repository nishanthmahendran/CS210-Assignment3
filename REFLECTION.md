# cs 210 A3 Reflection

##1. Why does LinkedList::deleteFront() need two delete calls?

This is because the two delete calls free two different objects. delete doomed->data frees the data object that is
stored by the node, while delete doomed frees the node itself. And this shows that leaving either one out would just
cause a memory leak.

##2. Why did pointer storage make an ArrayList destructor necessary?

The Arraylist will now store pointers to objects that are created with new. C++ doesn't automatically delete objects
when the array is deleted, so the destructor has to loop through the pointers and delete each object to prevent memory
leaks.

##3. How do search() and addFront() treat ownership differently?
addFront() receives a pointer and the list takes ownership of it. The list is going to be responsible for deleting it
later. search() only borrows the pointer temporarily to compare values, so it can't store or delete that.

##4. Why can the representation change without changing main.cpp?
Both the ArrayList and LinkedList implement the same List<T> interfact. The default function will decide which
implementation to create, as main.cpp will only use the common list methods.

##5. Which keyword matters most here?
I would say the override keyword will be the most important as it makes the compiler verify that a derived method
will correctly match a virtual method from the List interface. This will help catch mistakes in method names,
return types, and parameters.
