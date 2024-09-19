- Defines a class *and creates an object* from it all at once inside a method
- *Important:* **Static type** of the expression is the Interface/superclass used to create it, but the **Dynamic type** of the created object is anonymous (which means you can't refer to it later/one-instance-use)
- Java ONLY refers to `final` fields or fields of methods that the object is part of.
	- Think about it: If we are still using this new anonymous class, then the closure would include all the objects/methods referred to within the code. However, if the closure contains a mutable object, then the pointer in the closure may end up pointing somewhere different, which would not be the original object on the heap, so Java does not allow this.
- New *expression* form: define a class and create an object from it all at once - 
```java
new InterfaceOrClassName() {
	public void method1(int x) {
		// code for method1
	}
	public void method2(char y) {
		// code for method2
	}
}
```
This will define a class and create methods or other things for it. 
**Special note:** Can use normal class definition, but no constructors are allowed!!
**Another note:** The keyword `new Interface()` does not instantiate an interface but rather makes a new class that implements interface.

\*Java's version of OCaml's first-class function
(i.e. they both are a sort of "delayed computation" that stores a class and methods in a data structure to be run later)
- Code stored by the event / action listener
- Code only runs when the button is pressed
- Could run once, many times, or not at all

Both sorts of computation can refer to variables in the current scope
- OCaml: Any available variable
- Java: Only variables marked `final`
