# Calculator
calculator  code


import tkinter as tk
from tkinter import messagebox

def on_click(event):
    text = event.widget.cget("text")
    if text == "=":
        try:
            result = eval(str(entry_var.get()))
            entry_var.set(result)
        except Exception as e:
            messagebox.showerror("Error", "Invalid Input")
            entry_var.set("")
    elif text == "C":
        entry_var.set("")
    else:
        entry_var.set(entry_var.get() + text)

root = tk.Tk()
root.title("Attractive Calculator")
root.geometry("350x500")
root.configure(bg="#34495e")

entry_var = tk.StringVar()
entry = tk.Entry(root, textvar=entry_var, font=("Arial", 24), bd=10, relief=tk.FLAT, justify="right", bg="#ecf0f1", fg="#2c3e50")
entry.pack(fill=tk.BOTH, ipadx=8, pady=15, padx=15)

buttons = [
    ["7", "8", "9", "/"],
    ["4", "5", "6", "*"],
    ["1", "2", "3", "-"],
    ["C", "0", "=", "+"]
]

frame = tk.Frame(root, bg="#34495e")
frame.pack()

for row in buttons:
    button_frame = tk.Frame(frame, bg="#34495e")
    button_frame.pack(side=tk.TOP, fill=tk.BOTH, expand=True)
    for btn_text in row:
        btn = tk.Button(button_frame, text=btn_text, font=("Arial", 20, "bold"), width=6, height=2, 
                        bg="#16a085", fg="#ecf0f1", relief=tk.RAISED, activebackground="#1abc9c", activeforeground="#ffffff")
        btn.pack(side=tk.LEFT, expand=True, fill=tk.BOTH, padx=5, pady=5)
        btn.bind("<Button-1>", on_click)

root.mainloop()
