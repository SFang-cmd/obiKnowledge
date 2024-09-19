**javax.swing.* - Java's GUI Library**
(Built on existing library "AWT", so always use the javax.swing.JFoo version vs. java.awt.Foo)

A Comparison to OCaml's gctx:
- Graphics Context (Gctx.gctx vs. Graphics)
- Widget Type (Widget.widget vs. JComponent)
- Basic Widgets
	- button vs. JButton
	- label vs. JLabel
	- checkbox vs. JCheckBox
- Container Widgets
	- hpair vs. JPanel
	- vpair vs. Layouts
- Events
	- event vs. xEvent (i.e., ActionEvent, MouseEvent, KeyEvent)
- Event Listener
	- mouse_listener, mouseclick_listener, (functions of type event -> unit)
	- ActionListener, MouseListener, KeyListener

