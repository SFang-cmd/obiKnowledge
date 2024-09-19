```java
private static void fractal(Graphics2D gc, int x, int y, 
							double angle, double len) {
	if (len > 1) {
		double af = (angle * Math.PI) / 180.0;
		int nx = x + (int)(len * Math.cos(af));
		int ny = y + (int)(len * Math.sin(af)); 
		gc.setStroke(new BasicStroke(3)); 
		gc.drawLine(x, y, nx, ny); 
		fractal(gc, nx, ny, angle + 20, len - 8); 
		fractal(gc, nx, ny, angle - 10, len - 8); 
	}
}
```
Drawing a fractal

How to call in a widget? Use [[JComponent]]
```java
public class DrawingCanvas extends JComponent { 
	
	// paint the drawing panel on the screen
	public void paintComponent (Graphics gc) {
		super.paintComponent(gc); 
		
		// set the pen color 
		gc.setColor(Color.GREEN);
		
		// draw a fractal tree 
		fractal((Graphics2d)gc, 200, 450, 270, 80); 
	} 
	
	// give the size of the drawing panel 
	public Dimension getPreferredSize() {
		return new Dimension(200,200); 
	}
}
```

This is nifty and all, but how can this component really get put onto the screen?
Use [[JFrame]]!
```java
class DrawingCanvasMain implements Runnable {
	public void run() {
		JFrame frame = new JFrame("Tree");
		
		// set the content of the window to be our drawing
		frame.getContentPane().add(new DrawingCanvase());
		
		// make sure the application exits when the frame closes
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
		// resize the frame based on the size of the panel
		frame.pack();
		
		// show the frame
		frame.setVisible(true);
	}
}
```
*Note: Runnable is a class to run GUI's*

