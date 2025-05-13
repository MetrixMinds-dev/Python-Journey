from tkinter import *

root = Tk()
root.title('Calculator')

operation = StringVar()
operation.set('+')


def calculate():
    try:
        num1 = float(entry1.get())
        num2 = float(entry2.get())
        op = operation.get()

        if op == '+':
            ans = num1 + num2
        elif op == '-':
            ans = num1 - num2
        elif op == '*':
            ans = num1 * num2
        elif op == '/':
            if num2 != 0:
                ans = num1 / num2
            else:
                output_label.configure(text="Can't Divide By Zero")
                return
        else:
            output_label.configure(text='Invalid Operation')
            return

        output_label.configure(text=f"The answer is {ans:.2f}")

    except ValueError:
        output_label.configure(text='Enter valid numbers ')

    #entry1.delete(0, END)
    #entry2.delete(0, END)

operation_menu = OptionMenu(root, operation, '+', '-', '*', '/')
operation_menu.config(font=('Poppins', 15))

message_view = Label(text='Enter the numbers:', font=('Poppins', 15))
entry1 = Entry(font=('Poppins', 15), width=5)
entry2 = Entry(font=('Poppins', 15), width=5)
calc_button = Button(text='Calculate', font=('Poppins', 17), command=calculate)
output_label = Label(font=('Arial Black', 17))


message_view.grid(row=0, column=0, columnspan=2, pady=10)
entry1.grid(row=1, column=0, padx=5)
entry2.grid(row=1, column=1, padx=5)
operation_menu.grid(row=2, column=1, pady=10)
calc_button.grid(row=2, column=0, pady=10)
output_label.grid(row=3, column=0, columnspan=2)

mainloop()
