#cmp114 assignment

import tkinter as tk
from tkinter import messagebox

class BankApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Bank App")
        
        # Create labels and entry fields
        self.label_balance = tk.Label(root, text="Balance:")
        self.label_balance.grid(row=0, column=0, padx=10, pady=10)
        
        self.entry_balance = tk.Entry(root, width=20)
        self.entry_balance.grid(row=0, column=1, padx=10, pady=10)
        
        self.label_amount = tk.Label(root, text="Amount:")
        self.label_amount.grid(row=1, column=0, padx=10, pady=10)
        
        self.entry_amount = tk.Entry(root, width=20)
        self.entry_amount.grid(row=1, column=1, padx=10, pady=10)
        
        # Create buttons
        self.button_deposit = tk.Button(root, text="Deposit", command=self.deposit)
        self.button_deposit.grid(row=2, column=0, padx=10, pady=10)
        
        self.button_withdraw = tk.Button(root, text="Withdraw", command=self.withdraw)
        self.button_withdraw.grid(row=2, column=1, padx=10, pady=10)
        
    def deposit(self):
        try:
            current_balance = float(self.entry_balance.get())
            amount = float(self.entry_amount.get())
            new_balance = current_balance + amount
            self.entry_balance.delete(0, tk.END)
            self.entry_balance.insert(tk.END, str(new_balance))
        except ValueError:
            messagebox.showerror("Error", "Invalid input")
            
    def withdraw(self):
        try:
            current_balance = float(self.entry_balance.get())
            amount = float(self.entry_amount.get())
            if amount > current_balance:
                messagebox.showerror("Error", "Insufficient balance")
            else:
                new_balance = current_balance - amount
                self.entry_balance.delete(0, tk.END)
                self.entry_balance.insert(tk.END, str(new_balance))
        except ValueError:
            messagebox.showerror("Error", "Invalid input")
   
