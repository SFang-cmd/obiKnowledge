Display the Lightbulb:
```java
class LightBulb extends JComponent {
	// Used to save the state of the bulb
	private boolean isOn = false;
	
	public void flip() {
		isOn = !isOn;
	}
	
	// Draw the lightbulb using the gctx
	public void paintComponent(Graphics gc) {
		if(isOn) {
			gc.setColor(Color.YELLOW);
		} else {
			gc.setColor(Color.BLACK);
		}
		gc.fillRect(0,0,100,100)
	}
	
	// Set the size of the window to 100 x 100
	public Dimension getPreferredSize() {
		return new Dimension(100,100);
	}
}
```

Main class that actually displays things:
```java
public class OnOff implements Runnable {
	public void run() {
		// name the frame
		JFrame frame = new JFrame("On/Off Switch");
		//Makes a panel to have multiple JComponents
		JPanel panel = new JPanel();
		frame.getContentPane().add(panel);
		LightBulb bulb = new LightBulb();
		panel.add(bulb);
		JButton button = new JButton("On/Off");
		panel.add(button);
		
		// We will explore how to set up a ButtonListener below (can use an anonymous inner class)
		// instead of: button.addActionListener(new ButtonListener(bulb));
		//ActionListener is Java's method to sense mouse clicks
		button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				bulb.flip();
				bulb.repaint();
			}
		});
		
		
		// Default setup
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.pack();
		frame.setVisible(true);
	}
	public static void main(String[] args) {
		//Start the application in swing
		SwingUtilities.invokeLater(new OnOff());
	}
}
```

Let's look at the [[ActionListener]] method to make the button do something:
```java
class ButtonListener implements ActionListener {
	private LightBulb bulb;
	public ButtonListener (LightBulb b) {
		bulb = b;
	}
	
	//Mouseclick is handled by Java's action listener above
	@Override
	public void actionPerformed(ActionEvent e) {
		bulb.flip();
		//currently, our repaint function doesn't do anything
		//it just lets Swing know that this 
		//button needs to be repainted!
		
		//Repaint automatically takes care of the repainting via LightBulb's paintComponent method
		bulb.repaint();
	}
}
```

However, listeners really only need to call 2 methods - bulb.flip() **and** bulb.repaint()
(See [[Inner Classes]])