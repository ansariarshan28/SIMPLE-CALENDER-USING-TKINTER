# SIMPLE-CALENDER-USING-TKINTER
import tkinter as tk
import calendar

def show_calendar(event=None):  # event parameter added to work with key binding
    year_text = year_entry.get()
    month_text = month_entry.get()

    if not year_text.isdigit() or not month_text.isdigit():
        output_box.delete("1.0", tk.END)
        output_box.insert(tk.END, "Please enter numeric values for year and month.")
        return

    year = int(year_text)
    month = int(month_text)

    if 1 <= month <= 12:
        cal_text = calendar.month(year, month)
        output_box.delete("1.0", tk.END)
        output_box.insert(tk.END, cal_text)
    else:
        output_box.delete("1.0", tk.END)
        output_box.insert(tk.END, "Month must be between 1 and 12.")

root = tk.Tk()
root.title("Simple Calendar App")
root.geometry("400x400")
root.configure(bg="lightyellow")

title_label = tk.Label(root, text="Simple Calendar", font=("Helvetica", 16, "bold"), bg="lightyellow")
title_label.pack(pady=10)

# Year input
year_label = tk.Label(root, text="Enter Year:", bg="lightyellow")
year_label.pack()
year_entry = tk.Entry(root)
year_entry.pack()

# Month input
month_label = tk.Label(root, text="Enter Month (1-12):", bg="lightyellow")
month_label.pack()
month_entry = tk.Entry(root)
month_entry.pack()

show_btn = tk.Button(root, text="Show Calendar", command=show_calendar)
show_btn.pack(pady=10)

# Output text box
output_box = tk.Text(root, height=10, width=30, font=("Courier", 10))
output_box.pack(pady=10)

# Bind Enter key to show_calendar function
root.bind("<Return>", show_calendar)

root.mainloop()
