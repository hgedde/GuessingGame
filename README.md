print("Welcome to the Guessing Game!!")
print("How to play: A four digit random number will be generated. It is your job to guess this number. Enter a number with 4 digits.")
print("If any of your digits match the random number's digits, you will be told. Additionally, you will be told if the digit is in the same place as in the random number.")
print("You have 10 tries!")

import random
from operator import itemgetter
# This creates the random number for the player to guess
randomNum = random.randint(1000,9999)

print(randomNum)
list1 = [int(x) for x in str(randomNum)]



guesses = 10

while guesses !=0:
    UserInput = input("Your Guess: ")
    if len(UserInput) < 4:
        print("Your guess has to be 4 digits long")
        guesses = guesses - 1
    elif len(UserInput) > 4:
        print("Your guess can only be 4 digits long")
        guesses = guesses - 1
    else:
        print("Your guess is the right length")
        list2 = [int(x) for x in str(UserInput)]
        print(list2)
        if int(UserInput) == randomNum:
            print("Nice Job!! Your answer is correct!")
        else:
            usersuccess = ["_","_","_","_"]
            print("This is your progress so far: ")
            print(usersuccess)
            for eachlet in list1: # Take each letter in the first list
                for everylet in list2: # Compare it to every letter in the second list
                    if eachlet == everylet:
                       if list1.index(eachlet) == list2.index(everylet):
                            usersuccess.insert(list2.index(everylet), 1)
                            usersuccess.pop(list2.index(everylet) + 1)
                            print("This is your progress so far:")
                            print(usersuccess)
