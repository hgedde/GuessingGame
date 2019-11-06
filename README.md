# GuessingGame

print("Welcome to the Guessing Game!!")
print("How to play: A four digit random number will be generated. It is your job to guess this number. Enter a number with 4 digits.")
print("If any of your digits match the random number's digits, you will be told. Additionally, you will be told if the digit is in the same place as in the random number.")
print("You have unlimited tries!")

import random

# This creates the random number for the player to guess
randomNum = random.randint(1000,9999)

print(randomNum)
list1 = [int(x) for x in str(randomNum)]

UserInput = input("Your guess: ")
# Makes a list with the User Input in it
list2 = [int(x) for x in str(UserInput)]
print(list2)

# This makes sure that the user's input is only 4 digits
#for i in range(0,3):
    #UserInput = input("Your guess: ")
    #if len(UserInput) > 4:
        #print("Sorry, your input is too long. Try again...")
    #elif len(UserInput) < 4:
        #print("Sorry, your input is too short. Try again...")
    #else:
        #print("yay")

for eachlet in list1: # Take each letter in the first list
    for everylet in list2: # Compare it to every letter in the second list
        if eachlet == everylet: # If the letter in the first matches the letter in the second list
            print(list2.index(eachlet)) # Find out where in the second list the first letter shows up
        else:
            print("nope") # If the first latter doesn't match the elements in the second list, print "nope"
# This shows the answer to the player after they have done their maxiumum number of inputs
print("The answer is: ")
print(randomNum)
