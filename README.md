# FiveCardDraw
This C++ project emulates a basic game of Five Card Draw (not quite Casino Royale), employing user interaction via the terminal.

========================================================================
    lab3 Project Overview
	Jesse Huang		jessehuang@wustl.edu
	Danny Weiner		dnweiner@wustl.edu
	Kate Hao		kate.hao@gmail.com
========================================================================


Program Description
===================
This program will simulate a game of Five-Card Draw between at least two players, where the role of the dealer cycles through the players (the dealer begins as position 0, i.e. the first player inputted). Each round begins with giving the players the option to discard as few or as many cards they want from their randomly drawn hand. After discarding, their hand is refilled to 5 cards from the shuffled main deck; then, whoever as the winning hand wins the round. At the end of the round, players have the option to leave (in which case their wins and losses will be outputted to a text file). Additionally, players can join -- whenever players are added, either at the very beginning of the game or between rounds, the program will check for a text file whose title matches their name from which to read in wins and losses. If such a text file is not found, then a default player is created with 0 wins and losses. The game will continue to execute until there are fewer than 2 players, at which point it automatically terminates.


In addition to the functions in the lab instructions, we wrote several additional functions. In Deck, we wrote two new << operators in order to make it easier to transfer cards from the discard deck and player hands to the main deck. In Game, we added a numPlayers() method that returns the number of players that are currently in the game. 
In player.cpp, the isInt method checks if a string can be converted into an integer.


Errors and Warnings
===================
One major error we struggled with was how to deal with the shared_ptr, game_ptr, in the Game.cpp class. In start_game, we initially struggled to figure out how to instantiate it with make_shared, since just forward declaring wouldn't allow that. The solution just turned out to be including FiveCardDraw.h in the Game.cpp class.
Beyond that, before_turn was the most difficult to debug.


Test Cases and Command Line Arguments
=====================================
Not enough arguments:
Command: Lab3.exe FiveCardDraw Kate
Output: “Usage: Lab3.exe experienced error: program should be run with the name of the game followed by two or more player names”
	This is the correct behavior!
When a player without a text file is entered as part of a command,
upon exiting, a text file with their name is created in the directory of the exe file.
 
The game terminates when there are less than two players 
(i.e. if there are currently 2 players and one of them leaves at the end of the round)
If there are only two players, the player who is not dealing will automatically win 
because the dealer does not have a hand to compare to. 

If a player is already in the game, the already_playing exception is thrown. 

If a command such as “Lab3.exe FaveCadDra Danny “ is entered, the unknown game exception is thrown.

