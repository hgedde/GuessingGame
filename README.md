print("Welcome to the Guessing Game!!")
print("How to play: A four digit random number will be generated. It is your job to guess this number. Enter a number with 4 digits. Each digit can be between 0 and 9.")
print("If any of your digits match the random number's digits, you will be told. Additionally, you will be told if the digit is in the same place as in the random number.")
print("You have 10 tries! Good luck!!!")
print("    ")

import random
import time
randomNum = random.randint(1000,9999) # This creates the random number for the player to guess

print(randomNum)
list1 = [int(x) for x in str(randomNum)] # This makes a list from the randomnumber that can be used later

guesses = 10 # The number of guesses the player has
usersuccess = ["_","_","_","_"] # Initializes the progress report for the player

while guesses !=0: # While the guesses does not equal 0
    UserInput = input("Your Guess: ") # This creates the spot for users to input a guess
    if len(UserInput) < 4: # This checks to make sure the input is not less than 4 digits
        time.sleep(1)
        print("Your guess has to be 4 digits long")
        print("    ")
        guesses = guesses - 1
    elif len(UserInput) > 4: # This checks to make sure the input is not more than 4 digits
        time.sleep(1)
        print("Your guess can only be 4 digits long")
        print("    ")
        guesses = guesses - 1
    else: # If the number is 4 digits, continue through the rest of the code
        time.sleep(1)
        print("Your guess is the right length")
        print("   ")
        list2 = [int(x) for x in str(UserInput)]
        if int(UserInput) == randomNum: # If the user guesses the right number, tell them and don't do the rest of the code
            time.sleep(1)
            print("Nice Job!! Your answer is correct!")
            print("    ")
            break
        else: # If the guess is not right, start checking the guess for the right digits and in the right places
            for eachlet in list1: # Take each letter in the first list
                for everylet in list2: # Compare it to every letter in the second list
                    if eachlet == everylet: # If they are equal:
                       if list1.index(eachlet) == list2.index(everylet): # And the index of those 2 numbers are the same
                           usersuccess.insert(list2.index(everylet), list2[list1.index(eachlet)]) # Change the UserSuccess to include their right guess
                           usersuccess.pop(list2.index(everylet) + 1)
                       else: # If the indexes don't match but the digit value does, tell them they have the right value but it is not in the right spot
                           time.sleep(1)
                           print("The number in the", list2.index(everylet) + 1, "spot is in the answer but yours is not in the right place.")
            guesses = guesses - 1
            time.sleep(0.5)
            print("Hint: If the statement about correct number in the wrong spot is printed more than once, that digit occurs more than once in the answer.")
            print("    ")
            time.sleep(1)
            print("This is your progress so far:") # Prints the progress of the user
            print(usersuccess)
            print("    ")
            print("    ")
# When the user runs out of guesses, show them the answer
time.sleep(0.5)
print("You ran out of guesses. Oh no...")
time.sleep(0.5)
print("The answer was:", randomNum)
