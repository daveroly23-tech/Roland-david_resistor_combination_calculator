# Resistor Combination Calculator
# This program calculates the equivalent resistance of resistors in series and parallel.

def calculate_resistance(resistor_values):
    """Return the total resistance in series and in parallel."""
    series_resistance = sum(resistor_values)

    # For parallel resistors: 1/R = 1/R1 + 1/R2 + ...
    reciprocal_total = sum(1 / value for value in resistor_values)
    parallel_resistance = 1 / reciprocal_total

    return series_resistance, parallel_resistance


def get_positive_number(message):
    """Get a positive number from the user and reject invalid input."""
    while True:
        try:
            number = float(input(message))
            if number > 0:
                return number
            print("Please enter a value greater than zero.")
        except ValueError:
            print("Invalid input. Please enter a number, such as 10 or 4.7.")


def main():
    print("=" * 48)
    print(" RESISTOR COMBINATION CALCULATOR")
    print("=" * 48)

    # The program can perform more than one calculation.
    while True:
        resistor_values = []

        # Ask how many resistors will be used.
        while True:
            try:
                number_of_resistors = int(input("\nHow many resistors do you have? "))
                if number_of_resistors > 0:
                    break
                print("Please enter at least 1 resistor.")
            except ValueError:
                print("Invalid input. Enter a whole number, such as 3.")

        # Collect each resistor value in ohms.
        for index in range(number_of_resistors):
            value = get_positive_number(
                f"Enter the value of resistor {index + 1} (ohms): "
            )
            resistor_values.append(value)

        # Call the function to calculate both combinations.
        series, parallel = calculate_resistance(resistor_values)

        print("\n---------- RESULTS ----------")
        print("Resistor values:", resistor_values, "ohms")
        print(f"Total resistance in series: {series:.2f} ohms")
        print(f"Total resistance in parallel: {parallel:.2f} ohms")

        # Extra feature: compare the two arrangements.
        difference = series - parallel
        print(f"Difference between the results: {difference:.2f} ohms")
        if series > parallel:
            print("Series combination has the higher resistance.")
        elif parallel > series:
            print("Parallel combination has the higher resistance.")
        else:
            print("Both combinations have the same resistance.")

        # Give the user the option to calculate another set.
        while True:
            again = input("\nWould you like another calculation? (yes/no): ").strip().lower()
            if again in ("yes", "y"):
                break
            elif again in ("no", "n"):
                print("\nThank you for using the Resistor Combination Calculator.")
                return
            else:
                print("Please type yes or no.")


if __name__ == "__main__":
    main()# Resistor Combination Calculator

What it does

This Python program asks the user for the number and values of resistors. It calculates the equivalent resistance when the resistors are connected in series and when they are connected in parallel.


How to run it


Install Python 3.

Save the code as resistor_calculator.py.

Open a terminal in the folder containing the file.

Run:


python resistor_calculator.py

You can also run the file in Pydroid 3 on an Android phone.


Sample output

================================================
       RESISTOR COMBINATION CALCULATOR
================================================

How many resistors do you have? 2
Enter the value of resistor 1 (ohms): 10
Enter the value of resistor 2 (ohms): 20

---------- RESULTS ----------
Resistor values: [10.0, 20.0] ohms
Total resistance in series:   30.00 ohms
Total resistance in parallel: 6.67 ohms
Difference between the results: 23.33 ohms
Series combination has the higher resistance.

Would you like another calculation? (yes/no): no

Thank you for using the Resistor Combination Calculator.

My own twist

I added a comparison feature. After calculating both results, the program displays the difference and tells the user which arrangement has the higher resistance. It also allows the user to perform another calculation without restarting the program.


What I learned

I learned how to use Python functions, lists, loops, conditional statements and input validation. I also practised applying the series and parallel resistance formulas in a simple program.


Author

[Roland david], ND2 Mechatronics Engineering, Yaba College of Technology.

Roland-david_resistor_combination_calculator