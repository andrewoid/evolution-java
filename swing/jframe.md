# JFrame

``` java

public class CalculatorFrame extends JFrame {
    public CalculatorFrame() {
        setSize(800, 600);
        setTitle("Calculator")
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        
        // setup LayoutManager and Views
        
    }
}
```

``` java
public class Main {
    public static void main(String args[]) {
        CalculatorFrame frame = new CalculatorFrame();
        frame.setVisible(true)
    }
}
```

### Swing Components

https://web.mit.edu/6.005/www/sp14/psets/ps4/java-6-tutorial/components.html

### Layout Managers

https://docs.oracle.com/javase/tutorial/uiswing/layout/visual.html

### Adding Components and LayoutMangers

``` java

public class CalculatorFrame extends JFrame {
    public CalculatorFrame() {
        setSize(80, 400);
        setTitle("Calculator")
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        
        // setup LayoutManager and Views
        JTextField equationField = new JTextField();
        equationField.setPreferredSize(new Dimension(40, 200));
        JButton evaluateButton = new JTextField("Evaluate");
        JLabel resultLabel = new JLabel();
        setLayout(new FlowLayout());
        addComponent(equationField);
        addComponent(evaluateButton);
        addComponent(resultLabel);
        
        // setup actions
        evaluateButton.addActionListener(
            new ActionListener() {
                public void actionPerformed(ActionEvent event) {
                    Calculator calculator = new Calculator();
                    String equation = equationField.getText();
                    String result = calculator.evaluate(equation);
                    resultLabel.setText(result);
                }
            }
        );
    }
}
```