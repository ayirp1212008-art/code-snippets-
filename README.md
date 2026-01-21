# code-snippets-
import tkinter as tk

def press(key):
    current = entry.get()
    entry.delete(0, tk.END)
    entry.insert(0, current + str(key))

def clear():
    entry.delete(0, tk.END)

def calculate():
    try:
        result = eval(entry.get())
        entry.delete(0, tk.END)
        entry.insert(0, result)
    except:
        entry.delete(0, tk.END)
        entry.insert(0, "Error")

# Window
root = tk.Tk()
root.title("Calculator")
root.geometry("300x400")
root.resizable(False, False)

# Entry box
entry = tk.Entry(root, font=("Arial", 20), bd=10, relief=tk.RIDGE, justify="right")
entry.pack(fill="x", padx=10, pady=10)

# Buttons
buttons = [
    ('7', '8', '9', '/'),
    ('4', '5', '6', '*'),
    ('1', '2', '3', '-'),
    ('0', '.', '=', '+')
]

frame = tk.Frame(root)
frame.pack()

for row in buttons:
    row_frame = tk.Frame(frame)
    row_frame.pack()
    for char in row:
        if char == '=':
            btn = tk.Button(row_frame, text=char, width=6, height=2,
                            command=calculate)
        else:
            btn = tk.Button(row_frame, text=char, width=6, height=2,
                            command=lambda c=char: press(c))
        btn.pack(side="left", padx=2, pady=2)

# Clear button
tk.Button(root, text="Clear", width=28, height=2, command=clear).pack(pady=5)

root.mainloop()
