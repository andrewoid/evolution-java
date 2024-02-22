``` java

class SimpleDrawingComponent extends JComponent {

    @Override
    public void paintComponent([Graphics g) {
    
        // This method is called by the operating system. 
        // You should never call this method directly!
       
        // draw calls in THIS method ONLY
        g.drawString(...);
        g.drawLine(...);
        g.drawRect(...);
        g.drawOval(...);
        g.fillOval(...);
       
        // the origin is in the upper left hand corner.
        // to move the origin to the lower left hand corner call
        // this only affects draw calls after translate is called.
        g.translate(0, getHeight());
        
        g.setColor(...);   
    }
}
```

You can add your component to a JPanel as you would any other standard Swing component.

``` java
SimpleDrawingComponent component = new SimpleDrawingComponent();
panel.add(component);
```

If you ever want to tell the operating system to call `paintComponent()` if something has changed use

``` java 
component.repaint();
```

### Resources

[Graphics](https://docs.oracle.com/javase/8/docs/api/java/awt/Graphics.html) class

[Graphics2D](https://docs.oracle.com/javase/8/docs/api/java/awt/Graphics2D.html) class