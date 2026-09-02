def convert_length(value, from_unit, to_unit):
    units = {
        "m": 1,0
        "km": 1000,
        "cm": 0.01,
        "mm": 0.001,
        "mile": 1609.344,
        "ft": 0.3048
    }

    return value * units[from_unit] / units[to_unit]


def convert_weight(value, from_unit, to_unit):
    units = {
        "kg": 1,
        "g": 0.001,
        "lb": 0.453592,
        "oz": 0.0283495
    }

    return value * units[from_unit] / units[to_unit]


def convert_temperature(value, from_unit, to_unit):
    if from_unit == "C":
        if to_unit == "F":
            return (value * 9 / 5) + 32
        if to_unit == "K":
            return value + 273.15

    if from_unit == "F":
        if to_unit == "C":
            return (value - 32) * 5 / 9
        if to_unit == "K":
            return (value - 32) * 5 / 9 + 273.15

    if from_unit == "K":
        if to_unit == "C":
            return value - 273.15
        if to_unit == "F":
            return (value - 273.15) * 9 / 5 + 32

    return value


print("=== Unit Converter ===")
print("1. Length")
print("2. Weight")
print("3. Temperature")

choice = input("\nChoose a category: ")

try:
    value = float(input("Enter value: "))
    from_unit = input("From unit: ")
    to_unit = input("To unit: ")

    if choice == "1":
        result = convert_length(value, from_unit, to_unit)

    elif choice == "2":
        result = convert_weight(value, from_unit, to_unit)

    elif choice == "3":
        result = convert_temperature(value, from_unit, to_unit)

    else:
        print("Invalid category.")
        exit()

    print(f"\nResult: {result:.2f} {to_unit}")

except (ValueError, KeyError):
    print("Invalid input. Please check your values and units.")
