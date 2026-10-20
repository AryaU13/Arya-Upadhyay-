import random

words = ["APPLE", "MANGO", "TIGER", "HOUSE"]
word = random.choice(words)

guessed = []
attempts = 6

stages = [
    """
     -----
     |   |
     O   |
    /|\\  |
    / \\  |
         |
    """,
    """
     -----
     |   |
     O   |
    /|\\  |
    /    |
         |
    """,
    """
     -----
     |   |
     O   |
    /|\\  |
         |
         |
    """,
    """
     -----
     |   |
     O   |
    /|   |
         |
         |
    """,
    """
     -----
     |   |
     O   |
     |   |
         |
         |
    """,
    """
     -----
     |   |
     O   |
         |
         |
         |
    """,
    """
     -----
     |   |
         |
         |
         |
         |
    """
]

while attempts > 0:
    display = ""

    for letter in word:
        if letter in guessed:
            display += letter + " "
        else:
            display += "_ "

    print("\nWord:", display)
    print("Attempts left:", attempts)
    print(stages[6 - attempts])

    if "_" not in display:
        print("Congratulations! You won!")
        break

    guess = input("Guess a letter: ").upper()

    if len(guess) != 1 or not guess.isalpha():
        print("Please enter one letter.")
        continue

    if guess in guessed:
        print("You already guessed this letter.")
        continue

    guessed.append(guess)

    if guess not in word:
        attempts -= 1
        print("Wrong guess!")

if attempts == 0:
    print(stages[0])
    print("Game over! The word was:", word)
    #Question 2
    import csv

name = input("Enter stock name: ")
buy = float(input("Enter buy price: "))
qty = int(input("Enter quantity: "))
current = float(input("Enter current price: "))

investment = buy * qty
value = current * qty
profit = value - investment

print("Stock Name:", name)
print("Total Investment:", investment)
print("Current Value:", value)
print("Profit/Loss:", profit)

with open("portfolio_summary.csv", "w", newline="") as f:
    w = csv.writer(f)
    w.writerow(["Stock", "Investment", "Current Value", "Profit/Loss"])
    w.writerow([name, investment, value, profit])

print("Data saved successfully!")
