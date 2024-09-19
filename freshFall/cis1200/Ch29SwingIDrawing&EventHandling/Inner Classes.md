- Useful in situations where objects require "deep access" to each other's internals
- Replaces tangled workarounds like the "owner object" pattern
	- Solution with inner classes is easier to read
	- No need to allow public access to instance variables of outer class
- Also called "dynamic nested classes"
**Big idea:** Classes can be *members* of other classes!

Ex. 
```java
class Outer {
	private int outerVar;
	public Outer () {
		outerVar = 6;
	}
	//Call this class by using: Outer.Inner
	public class Inner {
		//Big idea: inner classes can have their own fields and methods
		private int innerVar;
		public Inner(int z) {
			innerVar = z;
		}
		public int getSum() {
			//inner class can reference fields bounded in the outer class
			return outerVar + innerVar;
		}
	}
}
```

**Object Creation:**
- Inner classes can refer to the instance variables and methods of the outer class.
- Inner class instances are usually created by the methods/constructors of the outer class
```java
public Outer () {
	//Note: the new here is actually this.new
	Inner b = new Inner ();
}
```
- Inner class instances *cannot* be created independently of a containing class instance (since it may require instance variables/methods from the outer class)
```java
Outer.Inner b = new Outer.Inner(); //Does not work!!

Outer a = new Outer();
Outer.Inner b = a.new Innter(); //This is fine

Outer.Inner b = (new Outer()).new Innter(); //This is fine too
```

Can make [[Anonymous Inner Class]]