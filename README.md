# COS-202
"""
MATHEMATICAL CALCULATOR (MC)
Simple calculator with basic operations
"""

class Calculator:
    def __init__(self):
        self.history = []
        
    def add(self, x, y):
        result = x + y
        self.history.append(f"{x} + {y} = {result}")
        return result
    
    def subtract(self, x, y):
        result = x - y
        self.history.append(f"{x} - {y} = {result}")
        return result
    
    def multiply(self, x, y):
        result = x * y
        self.history.append(f"{x} * {y} = {result}")
        return result
    
    def divide(self, x, y):
        if y == 0:
            return "Error: Division by zero!"
        result = x / y
        self.history.append(f"{x} / {y} = {result}")
        return result
    
    def power(self, x, y):
        result = x ** y
        self.history.append(f"{x} ^ {y} = {result}")
        return result
    
    def modulus(self, x, y):
        if y == 0:
            return "Error: Modulus by zero!"
        result = x % y
        self.history.append(f"{x} % {y} = {result}")
        return result
    
    def show_history(self):
        if not self.history:
            return "No calculations yet."
        return "\n".join(self.history[-10:])

def display_menu():
    print("\n" + "="*50)
    print("        MATHEMATICAL CALCULATOR")
    print("="*50)
    print("  +   : Addition")
    print("  -   : Subtraction")
    print("  *   : Multiplication")
    print("  /   : Division")
    print("  ^   : Power (Exponentiation)")
    print("  %   : Modulus (Remainder)")
    print("  C   : Clear")
    print("  H   : History")
    print("  OFF : Exit")
    print("="*50)

def get_number(prompt):
    while True:
        try:
            return float(input(prompt))
        except ValueError:
            print("Invalid input! Please enter a number.")

def main():
    calc = Calculator()
    
    print("\n" + "="*50)
    print("    WELCOME TO MATHEMATICAL CALCULATOR")
    print("="*50)
    
    while True:
        display_menu()
        
        operation = input("\nEnter operation (+, -, *, /, ^, %, C, H, OFF): ").strip().upper()
        
        if operation == "OFF":
            print("\nThank you for using the Mathematical Calculator!")
            print("Goodbye!")
            break
        
        elif operation == "C":
            print("\nCalculator cleared!")
            continue
        
        elif operation == "H":
            print("\n--- Calculation History ---")
            print(calc.show_history())
            continue
        
        elif operation in ['+', '-', '*', '/', '^', '%']:
            try:
                num1 = get_number("Enter first number: ")
                num2 = get_number("Enter second number: ")
                
                if operation == '+':
                    result = calc.add(num1, num2)
                elif operation == '-':
                    result = calc.subtract(num1, num2)
                elif operation == '*':
                    result = calc.multiply(num1, num2)
                elif operation == '/':
                    result = calc.divide(num1, num2)
                elif operation == '^':
                    result = calc.power(num1, num2)
                elif operation == '%':
                    result = calc.modulus(num1, num2)
                
                print(f"\nResult: {result}")
                
            except Exception as e:
                print(f"\nError: {e}")
        
        else:
            print("\nInvalid operation! Please try again.")
        
        input("\nPress Enter to continue...")

if __name__ == "__main__":
    main()