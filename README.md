# project1
#my first tkinter app in form of a simple game: rock paper scissors

from tkinter import *
from numpy import random

#Initializing my window
window = Tk()
window.geometry("400x400")
window.resizable()
window.title("Clevince creation of rock paper scissors")
window.config(bg="seashell3")

Label(window, text="Rock, Paper, Scissors", font="arial 20 bold")

#choice
user_take = StringVar()
Label(window, text="choose any one: rock, paper, scissors", font="arial 15 bold", bg="seashell").place(x=20, y=70)
Entry(window, font="arial 15", textvariable= user_take, bg="white").place(x=90, y=130)

#Computers choice
comp_pick = random.choice([1, 2, 3, 1, 3, 2, 2, 3, 1, 3])
if comp_pick == 1:
    comp_pick = "rock"

elif comp_pick == 2:
    comp_pick = "paper"

else:
    comp_pick = "scissor"
result = StringVar()

def play():
    user_pick = user_take.get()
    if user_pick == comp_pick:
        result.set("tie")
    elif user_pick == "paper" and comp_pick == "scissor":
        result.set("You loose!: Comp picked scissor")
    elif user_pick == "scissor" and comp_pick == "paper":
        result.set("Clevince you won!: comp picked paper")
    elif user_pick == "rock" and comp_pick == "scissor":
        result.set("Clevince you win!: comp picked scissor")
    elif user_pick == "scissor" and comp_pick == "rock":
        result.set("You loose!: comp picked rock")
    elif user_pick == "rock" and comp_pick == "paper":
        result.set("You loose!: comp picked paper")
    elif user_pick == "paper" and comp_pick == "rock":
        result.set("Clevince You won!: comp picked Rock")
    else:
        result.set(comp_pick)
    initial = comp_pick

# reset function
def Reset():
    result.set("")
    user_take.set("")


def Exit():
    window.destroy()


#definning buttons
Entry(window, font="arial ", textvariable= result, width=50).place(x=25, y=250)
Button(window, text="play", padx= 5, command= play).place(x=150,y=190)
Button(window, text="reset", padx= 5, command= Reset).place(x=70,y=310)
Button(window, text="exit", padx= 5, command= Exit).place(x=280,y=310)
window.mainloop()


