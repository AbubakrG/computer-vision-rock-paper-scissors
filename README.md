# Computer Vision RPS

Play rock, paper, scissors against your computer using your webcam. 
Rock-Paper-Scissors is a game in which each player simultaneously shows one of three hand signals representing rock, paper, or scissors.
Rock beats scissors. Scissors beats paper. Paper beats rock.
The player who shows the first option that beats the other player's option wins.
This is an implementation of an interactive Rock-Paper-Scissors game, in which the user can play with the computer using the camera

<img src="https://contexta360.com/wp-content/uploads/2021/07/blog-humans-vs-robots.jpg" alt="Image Alt Text" width="300">

## Overview

This Python program uses computer vision and machine learning to recognize hand signs for rock, paper, and scissors, allowing you to play the game in a interactive way.

## Model and How to Use It

The project uses a Keras model ([teachlabmachine](https://teachablemachine.withgoogle.com/ )) trained to recognize four different hand signs: Rock, Paper, Scissors, and Nothing. The webcam captures the hand sign you make, and the program recognizes it as one of the four categories. This input is then stored in variables, allowing the game to proceed.

## Set Up

1. Create a virtual environment.
2. Install the required packages:
- TensorFlow
- OpenCV-Python
3. Import the Keras model.

## Code Structure

### Importing Libraries and Loading Model

```
import cv2
from keras.models import load_model
import numpy as np
import random
import time

(within class):
self.model = load_model('keras_model.h5')
```

### Game Logic and Winner Determination Function

```
def get_winner(self, choice, computer_choice):
    if choice == "nothing":
        print("Restart, and choose something this time!")

    elif choice == computer_choice:
        print(f"Draw - computer chose {computer_choice}. Same as you!")

    elif (choice == "rock" and computer_choice == "paper") or \
        (choice == "paper" and computer_choice == "scissors") or \
        (choice == "scissors" and computer_choice == "rock"):
            print(f"You lost - computer picked {computer_choice} while you picked {choice}")
            self.computer_wins += 1

    else:
        print(f"You won - computer picked {computer_choice} while you picked {choice}")
        self.user_wins += 1
```

### Main Loop

```
def play_game(choices_list):
    game = RPS()
    while True:
        game.count_countdown()
        user_choice = game.get_prediction()
        computer_choice = game.get_computer_choice()
        game.get_winner(user_choice, computer_choice)
        print(f"Computer wins: {game.computer_wins} ---- User wins: {game.user_wins}")

        if game.user_wins == 3 or game.computer_wins == 3:
            print(f"The game is over, Computer won {game.computer_wins} and you won {game.user_wins}")
            break
```

## How to Play

1. Run the program.
2. Make a hand sign in front of the webcam.
3. The computer will make its choice, and the winner will be announced.

## AiCore
This is the 2nd project of my AiCore Journey.

## What I learned
Create a teachable machine model that recognises different hand signals for the game.
How tools like machine learning can be used to supplement projects such as these and take them to the next level.
How to set up environment, set up necessary packages, troubleshoot problems with python versions not being compaticle with packages etc
