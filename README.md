# Calculator

## Detailed Code Explanation

This project is built using Python’s Tkinter library to create a graphical calculator application. Below is a step-by-step explanation of how the code works.

---

### 1. Importing Tkinter

```
import tkinter as tk
```

The Tkinter library is imported and aliased as `tk`.
Tkinter is Python’s standard GUI library used to create windows, buttons, input fields, and other graphical components.

---

### 2. Function to Handle Button Press

```
def press(v):
    entry.insert(tk.END, v)
```

* This function is called whenever a number or operator button is clicked.
* The value of the button (`v`) is inserted at the end of the entry widget.
* `tk.END` ensures that the new value is added after existing text.

---

### 3. Function to Clear the Display

```
def clear():
    entry.delete(0, tk.END)
```

* This function clears all text from the calculator display.
* It deletes characters from index `0` to the end of the entry field.
* It is connected to the **C (Clear)** button.

---

### 4. Function to Calculate the Result

```
def calc():
    try:
        result = eval(entry.get())
        entry.delete(0, tk.END)
        entry.insert(0, result)
    except:
        entry.delete(0, tk.END)
        entry.insert(0, "Error")
```

* This function evaluates the mathematical expression entered by the user.
* `entry.get()` retrieves the current expression as a string.
* `eval()` evaluates the expression and returns the result.
* If the expression is valid, the result replaces the existing input.
* If an error occurs (such as division by zero or invalid syntax), `"Error"` is displayed instead of crashing the program.

---

### 5. Creating the Main Window

```
root = tk.Tk()
root.title("Calculator")
root.configure(bg="#1e1e1e")
root.resizable(False, False)
```

* `tk.Tk()` initializes the main application window.
* The window title is set to `"Calculator"`.
* A dark background color is applied.
* Window resizing is disabled to maintain a fixed layout.

---

### 6. Creating the Entry Widget (Display Screen)

```
entry = tk.Entry(
    root,
    font=("Segoe UI", 20),
    bg="#2d2d2d",
    fg="white",
    bd=0,
    justify="right"
)
```

* This entry widget acts as the calculator display.
* Large font improves readability.
* Text is right-aligned to mimic real calculators.
* Border is removed for a modern UI look.

```
entry.grid(row=0, column=0, columnspan=4, padx=12, pady=12, ipady=10)
```

* The display spans across four columns at the top of the window.

---

### 7. Button Labels Definition

```
buttons = [
    "7", "8", "9", "/",
    "4", "5", "6", "*",
    "1", "2", "3", "-",
    "0", ".", "=", "+"
]
```

* This list defines all calculator buttons.
* The order of elements determines their placement in the grid layout.

---

### 8. Button Creation Logic

```
r = 1
c = 0
```

* `r` represents the current row.
* `c` represents the current column.
* Buttons start from row 1 because row 0 is used by the display.

---

### 9. Loop to Create Buttons

```
for b in buttons:
```

Each button is created dynamically using a loop.

#### Equals Button

```
if b == "=":
    btn = tk.Button(
        root, text=b, width=5, height=2,
        font=("Segoe UI", 14),
        bg="#ff9500", fg="white",
        command=calc
    )
```

* Calls the `calc()` function when clicked.
* Styled differently to highlight its importance.

---

#### Operator Buttons

```
elif b in ("+", "-", "*", "/"):
```

* Operators have a distinct color.
* Clicking them inserts the operator into the display using `press()`.

---

#### Number and Decimal Buttons

```
else:
```

* Number and decimal buttons insert their respective values into the display.
* `lambda x=b: press(x)` ensures the correct button value is passed.

---

### 10. Button Placement Using Grid

```
btn.grid(row=r, column=c, padx=5, pady=5)
```

* Buttons are placed using the grid layout system.
* Columns reset after every 4 buttons, and the row number increases.

---

### 11. Clear Button

```
clear_btn = tk.Button(
    root, text="C", width=22, height=2,
    font=("Segoe UI", 14),
    bg="#ff453a", fg="white",
    command=clear
)
```

* A full-width clear button is added at the bottom.
* Clears the entire display when clicked.

---

### 12. Starting the Application

```
root.mainloop()
```

* Starts the Tkinter event loop.
* Keeps the application running until the user closes the window.

---

## Summary

This calculator demonstrates:

* GUI development using Tkinter
* Event-driven programming
* Dynamic widget creation
* Error handling
* Clean UI layout management

It is a beginner-friendly project suitable for learning Python GUI concepts and showcasing on a resume or GitHub profile.
