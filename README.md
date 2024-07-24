# python_project_1

import random

# List of words to choose from
word_list = ['apple', 'banana', 'cherry', 'date', 'elderberry']

# Select a random word from the list
word = random.choice(word_list)

# Create a list to store the guessed letters
guessed_letters = ['_'] * len(word)

# Set the limit for incorrect guesses
incorrect_guesses_limit = 6
incorrect_guesses = 0

print("Welcome to Hangman!")
print("You have", incorrect_guesses_limit, "chances to guess the word.")

while True:
    # Print the current state of the word
    print(' '.join(guessed_letters))

    # Ask the player for their guess
    guess = input("Guess a letter: ").lower()

    # Check if the guess is in the word
    if guess in word:
        # Reveal the correct letter
        for i, letter in enumerate(word):
            if letter == guess:
                guessed_letters[i] = guess
    else:
        # Increment the incorrect guesses counter
        incorrect_guesses += 1
        print("Incorrect! You have", incorrect_guesses_limit - incorrect_guesses, "chances left.")

    # Check if the player has won or lost
    if '_' not in guessed_letters:
        print("Congratulations! You guessed the word:", word)
        break
    elif incorrect_guesses == incorrect_guesses_limit:
        print("Game over! The word was:", word)
        break
