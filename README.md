
import random

words = ["python", "computer", "developer", "keyboard", "programming"]
word = random.choice(words)

guessed_letters = []
attempts = 6

print("=== HANGMAN GAME ===")

while attempts > 0:
    display = ""

    for letter in word:
        if letter in guessed_letters:
            display += letter + " "
        else:
            display += "_ "

    print("\nWord:", display)

    if "_" not in display:
        print("Congratulations! You guessed the word:", word)
        break

    guess = input("Enter a letter: ").lower()

    if len(guess) != 1:
        print("Please enter only one letter.")
        continue

    if guess in guessed_letters:
        print("You already guessed this letter.")
        continue

    guessed_letters.append(guess)

    if guess not in word:
        attempts -= 1
        print("Wrong guess!")
        print("Remaining attempts:", attempts)

if attempts == 0:
    print("Game Over!")
    print("The correct word was:", word)