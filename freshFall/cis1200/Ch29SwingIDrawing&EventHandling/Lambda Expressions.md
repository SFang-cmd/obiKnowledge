- Java includes *lambda expressions* which can implement classes that define **only** a single method
```java
final LightBulb bulb = new LightBulb();
JButton button = new JButton("On/Off");

button.addActionListener((ActionListener e) -> {
	bulb.flip();
	bulb.repaint();
});
```
- Any interface with exactly one method is a *functional interface*
- Syntax: x -> { Body} // type of x inferred
- or: (T x, W y) -> {Body} // args x and y have type T and W respectively

![[Pasted image 20231128190646.png]]