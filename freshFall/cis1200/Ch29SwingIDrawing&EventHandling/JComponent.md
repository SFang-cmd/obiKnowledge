**OCaml widget == JComponent**
Big Notes:
- Subclasses should have *overridden* **methods** of JComponent
	- paintComponent (like OCaml repaint, displays the component)
	- getPreferredSize (like OCaml size, calculates the size of the component)
- Events are handled by listeners (no overriding for handling)
- Richer functionality
	- minimum/maximum size
	- font
	- foreground/background color
	- borders
	- what is visible
	- ...
