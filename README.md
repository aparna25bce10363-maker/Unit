Unit Converter...

A simple, beginner-friendly Python project for converting values between different units. I built this as part of my first semester Python coursework to practice logic, functions, and organizing code clearly.


Overview

This program allows users to convert between units across three major categories:

Temperature Units
Celsius (C)
Fahrenheit (F)
Kelvin (K)


Length Units
Kilometer (km)
Meter (m)
Centimeter (cm)
Millimeter (mm)
Mile
Foot (ft)
Inch


Weight Units
Kilogram (kg)
Gram (g)
Milligram (mg)
Pound (lb)
Ounce (oz)


The code is structured using functions and dictionaries to make unit conversions clean, organized, and easy to extend later.



How to Use the unit converter

1. Run the program using:



python unit_converter.py

2. Choose the category:

1 → Temperature

2 → Length

3 → Weight



3. Enter:

The value you want to convert

The original unit

The target unit



4. The converted result will appear instantly.






Example Output

===== Unit Converter =====
1. Temperature (C, F, K)
2. Length (km, m, cm, mm, mile, ft, inch)
3. Weight (kg, g, mg, lb, oz)

Choose conversion type (1-3): 1
Enter temperature value: 100
From unit (C/F/K): C
To unit (C/F/K): F

100°C = 212.00°F


Complete Python Code (Highly Commented Version)

Below is an improved and fully commented version of your project.
You can copy this into 

# UNIT CONVERTER PROJECT
# Created as a first-semester Python project


# This program converts between units of
# temperature, length, and weight.
# Each conversion category has its own function
# to keep the code clean and organized.



# TEMPERATURE CONVERSION FUNCTION

def convert_temperature(value, from_unit, to_unit):
    from_unit = from_unit.upper()
    to_unit = to_unit.upper()

    # First convert the input into Celsius
    if from_unit == "C":
        celsius = value
    elif from_unit == "F":
        celsius = (value - 32) * 5/9
    elif from_unit == "K":
        celsius = value - 273.15
    else:
        raise ValueError("Invalid temperature unit")

    # Now convert from Celsius to target unit
    if to_unit == "C":
        return celsius
    elif to_unit == "F":
        return (celsius * 9/5) + 32
    elif to_unit == "K":
        return celsius + 273.15
    else:
        raise ValueError("Invalid temperature unit")



# LENGTH CONVERSION FUNCTION
# Using meters as a base unit

length_factors = {
    "km": 1000,
    "m": 1,
    "cm": 0.01,
    "mm": 0.001,
    "mile": 1609.34,
    "ft": 0.3048,
    "inch": 0.0254
}

def convert_length(value, from_unit, to_unit):
    from_unit = from_unit.lower()
    to_unit = to_unit.lower()

    if from_unit not in length_factors or to_unit not in length_factors:
        raise ValueError("Invalid length unit")

    # Convert to meters first
    meters = value * length_factors[from_unit]

    # Convert meters to target unit
    return meters / length_factors[to_unit]



# WEIGHT CONVERSION FUNCTION
# Using grams as a base unit

weight_factors = {
    "kg": 1000,
    "g": 1,
    "mg": 0.001,
    "lb": 453.592,
    "oz": 28.3495
}

def convert_weight(value, from_unit, to_unit):
    from_unit = from_unit.lower()
    to_unit = to_unit.lower()

    if from_unit not in weight_factors or to_unit not in weight_factors:
        raise ValueError("Invalid weight unit")

    # Convert to grams first
    grams = value * weight_factors[from_unit]

    # Convert grams to target unit
    return grams / weight_factors[to_unit]



# MAIN PROGRAM LOOP

def main():
    print("===== Unit Converter =====")
    print("1. Temperature (C, F, K)")
    print("2. Length (km, m, cm, mm, mile, ft, inch)")
    print("3. Weight (kg, g, mg, lb, oz)")

    choice = int(input("Choose conversion type (1-3): "))

    value = float(input("Enter value: "))
    from_unit = input("From unit: ")
    to_unit = input("To unit: ")

    # Run correct converter based on choice
    if choice == 1:
        result = convert_temperature(value, from_unit, to_unit)
    elif choice == 2:
        result = convert_length(value, from_unit, to_unit)
    elif choice == 3:
        result = convert_weight(value, from_unit, to_unit)
    else:
        print("Invalid choice")
        return

    # Show formatted result
    print(f"\n{value} {from_unit} = {result:.2f} {to_unit}\n")


# Run the program
if __name__ == "__main__":
    main()




What I Learned

This project taught me:

How to break code into functions

How dictionaries can simplify conversion formulas

Handling user input and preventing errors

How to structure a Python program properly

The differences between metric and imperial systems

Writing clean, readable, well-commented code



Future Improvements

Planned upgrades:

Let users perform multiple conversions in one run

Add strong input validation

Add more unit categories (volume, time, speed, storage)

Add a conversion history viewer

Build a graphical (GUI) or web version
