# codsoft2
#CALCULATOR
import tkinter as tk
from tkinter import messagebox

def perform_calculation():
    try:
        num1 = float(entry_num1.get())
        num2 = float(entry_num2.get())
        operation = operation_var.get()

        if operation == "Addition":
            result = num1 + num2
        elif operation == "Subtraction":
            result = num1 - num2
        elif operation == "Multiplication":
            result = num1 * num2
        elif operation == "Division":
            if num2 == 0:
                raise ValueError("Cannot divide by zero")
            result = num1 / num2
        else:
            raise ValueError("Invalid operation selected")

        label_result.config(text=f"Result: {result}")
    except ValueError as e:
        messagebox.showerror("Input Error", str(e))


# GUI Setup
root = tk.Tk()
root.title("Simple Calculator")

# Number inputs
label_num1 = tk.Label(root, text="Number 1")
label_num1.pack(pady=5)
entry_num1 = tk.Entry(root, width=50)
entry_num1.pack(pady=5)

label_num2 = tk.Label(root, text="Number 2")
label_num2.pack(pady=5)
entry_num2 = tk.Entry(root, width=50)
entry_num2.pack(pady=5)

# Operation selection
label_operation = tk.Label(root, text="Operation")
label_operation.pack(pady=5)
operation_var = tk.StringVar(value="Addition")
operations = ["Addition", "Subtraction", "Multiplication", "Division"]
for operation in operations:
    tk.Radiobutton(root, text=operation, variable=operation_var, value=operation).pack(anchor=tk.W)

# Calculate button
button_calculate = tk.Button(root, text="Calculate", command=perform_calculation)
button_calculate.pack(pady=10)

# Result display
label_result = tk.Label(root, text="Result: ")
label_result.pack(pady=10)

root.mainloop()
