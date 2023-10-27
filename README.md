# Hangman-
# M Kalam version of Hangman


from random import choice

list_of_words = ["REDBULL", "WILLIAMS", "MERCEDES", "ALPINE"]
word = choice(list_of_words)
hidden_word = "-" * len(word)

print(f"Hidden word is {hidden_word}")

mistake_count = 6

print('==============================================================')

while mistake_count > 0 and "-" in hidden_word:
    print("Pick a letter and press ENTER!")
    picked_letter = input().upper()

    if picked_letter.isalpha() and len(picked_letter) == 1:
        if picked_letter in word:
            for i in range(len(word)):
                if word[i] == picked_letter:
                    hidden_word = hidden_word[:i] + picked_letter + hidden_word[i + 1:]
            print(f"CORRECT! The word indeed contains the letter '{picked_letter}'.")
        else:
            mistake_count -= 1
            print(f"WRONG! Number of mistakes left: {mistake_count}")
    else:
        print("Invalid input. Please enter a single letter.")

    print(f"Hidden word is {hidden_word}")
    print('==============================================================')

if mistake_count == 0:
    print(f"YOU'RE HANGED BUDDY!! The word was '{word}'.")
else:
    print("CONGRATULATIONS!! You guessed the word!")
