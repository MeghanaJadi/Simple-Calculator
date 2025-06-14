import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class CalculatorGUI extends JFrame implements ActionListener {

  JTextField number1Field, number2Field, resultField;
  JButton addButton, subButton, mulButton, divButton;

  public CalculatorGUI() {
      setTitle("Simple Calculator");
      setSize(400, 250);
      setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
      setLayout(new GridLayout(5, 2, 10, 10));

  // Input fields and labels
  add(new JLabel("Enter first number:"));
  number1Field = new JTextField();
  add(number1Field);

  add(new JLabel("Enter second number:"));
  number2Field = new JTextField();
  add(number2Field);

  add(new JLabel("Result:"));
  resultField = new JTextField();
  resultField.setEditable(false);
  add(resultField);

  // Buttons
  addButton = new JButton("Add");
    subButton = new JButton("Subtract");
    mulButton = new JButton("Multiply");
    divButton = new JButton("Divide");

  add(addButton);
  add(subButton);
  add(mulButton);
  add(divButton);

  // Action Listeners
  addButton.addActionListener(this);
  subButton.addActionListener(this);
  mulButton.addActionListener(this);
  divButton.addActionListener(this);
}

public void actionPerformed(ActionEvent e) {
    try {
        double num1 = Double.parseDouble(number1Field.getText());
        double num2 = Double.parseDouble(number2Field.getText());
        double result = 0;

  if (e.getSource() == addButton) {
      result = num1 + num2;
  } else if (e.getSource() == subButton) {
      result = num1 - num2;
  } else if (e.getSource() == mulButton) {
      result = num1 * num2;
  } else if (e.getSource() == divButton) {
      if (num2 != 0) {
          result = num1 / num2;
      } else {
          JOptionPane.showMessageDialog(this, "Cannot divide by zero!");
          return;
      }
      }

  resultField.setText(String.valueOf(result));

  } catch (NumberFormatException ex) {
      JOptionPane.showMessageDialog(this, "Please enter valid numbers!");
  }
}

  public static void main(String[] args) {
      CalculatorGUI calc = new CalculatorGUI();
      calc.setVisible(true);
  }
}

