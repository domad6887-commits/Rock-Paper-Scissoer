# Rock-Paper-Scissoer
This is a Rock Paper Scissors game project in Python using very simple and easy to understand code.

import tkinter as tk
import random

Gamechoices = ["Rock", "Paper", "Scissor"]

# قوانين الفوز
rules = {
    "Rock": "Scissor",
    "Paper": "Rock",
    "Scissor": "Paper"
}


def start_game():
    """إخفاء شاشة الاسم وفتح شاشة اللعبة"""
    player_name.set(name_entry.get().strip())
    if not player_name.get():
        player_name.set("Player")
    name_frame.pack_forget()
    game_frame.pack(pady=20)


def play(choice):

    computer_choice = random.choice(Gamechoices)
    result_text = f"👉 {player_name.get()} chose: {choice}\n🤖 Computer chose: {computer_choice}\n\n"

    if choice == computer_choice:
        result_text += "⚖️ It's a draw!"
    elif rules[choice] == computer_choice:
        result_text += f"🎉 You win, {player_name.get()}!"
    else:
        result_text += "💻 Computer wins!"

    result_label.config(text=result_text)


root = tk.Tk()
root.title("Rock Paper Scissors")
root.geometry("350x350")
root.resizable(False, False)

player_name = tk.StringVar()


name_frame = tk.Frame(root)
name_frame.pack(pady=50)

tk.Label(name_frame, text="Enter your name:", font=("Arial", 12)).pack()
name_entry = tk.Entry(name_frame, font=("Arial", 12))
name_entry.pack(pady=5)

start_btn = tk.Button(name_frame, text="Start Game", font=("Arial", 12, "bold"),
                      command=start_game)
start_btn.pack(pady=10)

game_frame = tk.Frame(root)

title_label = tk.Label(game_frame, text="Rock Paper Scissors", font=("Arial", 16, "bold"))
title_label.pack(pady=10)

buttons_frame = tk.Frame(game_frame)
buttons_frame.pack(pady=10)

for choice in Gamechoices:
    btn = tk.Button(buttons_frame, text=choice, width=10, height=2,
                    command=lambda c=choice: play(c))
    btn.pack(side=tk.LEFT, padx=5)

result_label = tk.Label(game_frame, text="", font=("Arial", 12), wraplength=300, justify="center")
result_label.pack(pady=20)

root.mainloop()
