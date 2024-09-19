- An abstract class provides an *incomplete* implementation:
	- some methods are marked as **abstract**
	- those methods must be overridden to create instances
- Higher level of organization (superclass)
**Ex.**
```java
public abstract class AbstractClass {
	private int x = 0;
	public int m() {
		return frob(frob(x));
	}
	//Marks an incomplete method that needs to be implemented later
	abstract int frob(int x);
}

class ConcreteClass extends AbstractClass {
	//Subclass overrides the abstract method with an implementation
	@Override
	int frob(int x) {
		return x * 120;
	}
}
```

*Note:* Can also create an anonymous inner class with the overridden frob method
```java
public abstract class AbstractClass {
	private int x = 0;
	public int m() {
		return frob(frob(x));
	}
	//Marks an incomplete method that needs to be implemented later
	abstract int frob(int x);
}

// somewhere in main:
AbstractClass ac = new AbstractClass () {
	@Override
	int frob(int x) { return 0; }
}
```