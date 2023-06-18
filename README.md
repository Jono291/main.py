# main.py
import subprocess
import operator
import random as rd
from tkinter import *
from playsound import playsound


window = Tk()
window.title("Calculator")

Label1 = Label(window, text="Numbers here:", width = 35)
Label1.grid(row=0, column=1)

CalculationArea = Entry(window)
CalculationArea.grid(row=1, column=1)
f_num = 0

def button_click(number):
    current = CalculationArea.get()
    CalculationArea.delete(0,END)
    CalculationArea.insert(1, str(current) + str(number))

def button_clear():
    CalculationArea.delete(0, END)

def button_adding():
    first_number = CalculationArea.get()
    global f_num
    global symbol
    f_num = int(first_number)
    CalculationArea.delete(0, END)
    symbol = 2

def button_subtracting():
    first_number = CalculationArea.get()
    global f_num
    global symbol
    f_num = int(first_number)
    CalculationArea.delete(0, END)
    symbol = 3


def button_dividing():
    first_number = CalculationArea.get()
    global f_num
    global symbol
    f_num = int(first_number)
    CalculationArea.delete(0, END)
    symbol = 4
rd.seed(12)
def ThankHashem():
    selection = rd.randint(17,27)
    if selection == 23:
        subprocess.call(["say", "HAKADOSH BARUCH HU IS ONE!", ])
def button_multiplying():
    first_number = CalculationArea.get()
    global f_num
    global symbol
    f_num = int(first_number)
    CalculationArea.delete(0, END)
    symbol = 1

def equation():
    try:
        if symbol == 1:
            CalculationLabel = Label(window, text=f"""Answer:
{operator.mul(f_num, int(CalculationArea.get()))}""", font="Arial, 35", fg = "Gold" )
        if symbol == 2:
            CalculationLabel = Label(window, text=f"""Answer:
        {operator.add(f_num, int(CalculationArea.get()))}""", font="Arial, 35", fg = "Gold")
        if symbol == 3:
            CalculationLabel = Label(window, text=f"""Answer:
        {operator.sub(f_num, int(CalculationArea.get()))}""", font="Arial, 35", fg = "Gold" )
        if symbol == 4:
            CalculationLabel = Label(window, text=f"""Answer:
{operator.truediv(f_num, int(CalculationArea.get()))}""", font="Arial, 35", fg = "Gold" )

    except:
        CalculationLabel = Label(window, text = "Error", font = "Arial, 30", fg = "Red")
        subprocess.call(["say", "Remember, this is what HAKADOSH BARUCH HU WANTED!"])
    finally:
        subprocess.call (["say", "Thank you Hakadosh Baruch Hu!!!"])
        window.title("Jewish Calculator")

    CalculationLabel.selection_clear()
    CalculationLabel.grid ( row=1,column=2)









CalculationButton = Button(window, text = "(Click to) Solve:", command = equation )
CalculationButton.grid(row=2, column=1)





Button7 = Button( text = "7", command=lambda: button_click( 7 ), padx = 60, pady = 40, font = ("Times New Roman", 39) )
Button8 = Button( text = "8", command=lambda: button_click( 8 ), padx = 60, pady = 40, font = ("Times New Roman", 39) )
Button9 = Button( text = "9", command=lambda: button_click( 9 ), padx = 60, pady = 40, font = ("Times New Roman", 39) )
Button4 = Button( text = "4", command=lambda: button_click( 4 ), padx = 60, pady = 40, font = ("Times New Roman", 39) )
Button5 = Button( text = "5", command=lambda: button_click( 5 ), padx = 60, pady = 40, font = ("Times New Roman", 39) )
Button6 = Button( text = "6", command= lambda: button_click( 6 ), padx = 60, pady = 40, font = ("Times New Roman", 39) )
Button1 = Button( text = "1", command= lambda: [button_click( 1 ), ThankHashem()], padx = 60, pady = 40, font = ("Times New Roman", 39) )
Button2 = Button( text = "2", command= lambda: button_click( 2 ), padx = 60, pady = 40, font = ("Times New Roman", 39) )
Button3 = Button( text = "3", command= lambda: button_click( 3 ), padx = 60, pady = 40, font = ("Times New Roman", 39) )
ButtonClear = Button( text = "Clear", padx = 60, pady = 40, font = ("Times New Roman", 39), command = button_clear )
ButtonAdd = Button( text = "+", padx = 60, pady = 40, font = ("Times New Roman", 39), command = button_adding )
Button0 = Button( text = "0", command=lambda: button_click( 0 ), padx = 60, pady = 40, font = ("Times New Roman", 39) )

DivideButton = Button( text = "÷", padx = 70, pady = 50, font = ("Times New Roman", 59), command = button_dividing )
Multiplication = Button( text = "*", padx = 80, pady = 20, font = ("Times New Roman", 59), command = button_multiplying )
SubtractionButton = Button( text = "-", padx = 70, pady = 50, font = ("Times New Roman", 59), command = button_subtracting)

Button7.grid(row = 3, column = 0 ),
Button8.grid (row = 3, column = 1)
Button9.grid(row = 3, column = 2)
Button4.grid(row = 4, column = 0)
Button5.grid(row = 4, column = 1)
Button6.grid(row = 4, column = 2)
Button1.grid(row = 5, column = 0)
Button2.grid(row = 5, column = 1)
Button3.grid(row = 5, column = 2)
ButtonClear.grid(row = 6, column = 1)
ButtonAdd.grid(row = 6, column = 0)
Button0.grid(row = 6, column = 2)
DivideButton.grid(row = 7, column = 0)
Multiplication.grid(row = 7, column = 1)
SubtractionButton.grid(row = 7, column = 2)

window.mainloop()
