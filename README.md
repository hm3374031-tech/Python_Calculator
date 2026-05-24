# Python_Calculator
A Graphical Interface Calculator made in Python
from tkinter import *

# Main window
root = Tk()
root.title("My Calculator")
root.geometry("320x500")
root.configure(bg="black")

# Display screen
entry = Entry(
    root,
    font=("Arial", 24),
    bg="white",
    fg="black",
    justify=RIGHT
)

entry.pack(fill=BOTH, padx=10, pady=10, ipady=15)

# ---------------- FUNCTIONS ---------------- #

# Insert numbers/operators
def click(value):
    entry.insert(END, value)

# Clear screen
def clear():
    entry.delete(0, END)

# Calculate answer
def equal():
    try:
        result = eval(entry.get())
        entry.delete(0, END)
        entry.insert(END, result)

    except:
        entry.delete(0, END)
        entry.insert(END, "Error")

# ---------------- BUTTON ROWS ---------------- #

buttons = [
    ['7', '8', '9', '/'],
    ['4', '5', '6', '*'],
    ['1', '2', '3', '-'],
    ['C', '0', '=', '+']
]

for row in buttons:

    frame = Frame(root, bg="black")
    frame.pack(expand=True, fill=BOTH)

    for button in row:

        # Decide action
        if button == "C":
            action = clear

        elif button == "=":
            action = equal

        else:
            action = lambda x=button: click(x)

        # Create button
        Button(
            frame,
            text=button,
            font=("Arial", 20, "bold"),
            bg="#333333",
            fg="white",
            bd=0,
            command=action
        ).pack(side=LEFT, expand=True, fill=BOTH, padx=5, pady=5)

# Run app
root.mainloop()
