# introJava-assignment1
display weekly paychecks
import java.util.Scanner;

public class assignment1
{
  public static void main(String [ ] args)
  {
    // set variables
    int empID, hours = 0, overtime = 0;
    double grossInc = 0, payRate = 15, netInc = 0, taxRate = 0, pay, tax = 0, finalPay = 0;
    char method;
    // empID and method dont need to be initialized as = 0 because we are inputting them
    // payRate set as $15 per hour
    
    Scanner kb = new Scanner(System.in);
    
    System.out.println("Enter Employee ID Number "); // ask for the employee ID number
    empID = kb.nextInt(); 
    
    System.out.println("Enter Employee Payment Method "); // ask for the employee payment method
    method = kb.next().charAt(0); // needs to be char because we are inputing a word
    
    
    /* first if statement - 
     * if the method of payment is salary based (S) 
     * enter the gross income since the salary based payment is the same per week 
     * and calculate pay as the gross income 
     * if the payment method is hours, enter the number of hours and 
     * calculate the pay */
    if (method == 'S') 
    {
      System.out.println("Enter Employee Gross Income ");
      grossInc = kb.nextDouble();
      pay = grossInc;
    } // end if statement 1
    else if (method == 'H') /* */
    {
      System.out.println("Enter Employee Hours ");
      hours = kb.nextInt();
      pay = (hours * payRate);
    } // end else if (1)
    
    
    /* second if statement - 
     * if the payment method is hourly and the hours are 
     * over 40, calculate ovetime and incorporate into the pay equation*/
    if (hours > 40) 
      overtime = hours - 40;
      pay = (hours *payRate) + (1.5 * overtime * payRate);

        
    // third if statement calculates the tax rate using the given table
    if (grossInc <= 500) 
      taxRate = .07;
    else if (grossInc <= 1000)
      taxRate = .10;
    else if (grossInc > 1000)
      taxRate = .17;
    
    // calculate final pay, tax, and net income
    finalPay = pay + grossInc; 
    tax = taxRate * finalPay;
    netInc = finalPay - tax;

    /* display what was asked in the homework: employee ID number, gross income, 
     * income tax, net income */
    System.out.println("Employee ID Number is " + empID);
    System.out.println("Employee Gross Income is " + finalPay);
    System.out.println("Employee Income Tax is " + tax);
    System.out.println("Employree Net Income is " + netInc);
    
    
  }// end main
}// end class
