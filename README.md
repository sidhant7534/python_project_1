

import random

word_list = ['apple', 'banana', 'cherry', 'date', 'elderberry']

word = random.choice(word_list)

guessed_letters = ['_'] * len(word)

incorrect_guesses_limit = 6
incorrect_guesses = 0

print("Welcome to Hangman!")
print("You have", incorrect_guesses_limit, "chances to guess the word.")

while True:
    print(' '.join(guessed_letters))
    guess = input("Guess a letter: ").lower()

    if guess in word:
        for i, letter in enumerate(word):
            if letter == guess:
                guessed_letters[i] = guess
    else:
        incorrect_guesses += 1
        print("Incorrect! You have", incorrect_guesses_limit - incorrect_guesses, "chances left.")

    if '_' not in guessed_letters:
        print("Congratulations! You guessed the word:", word)
        break
    elif incorrect_guesses == incorrect_guesses_limit:
        print("Game over! The word was:", word)
        break
