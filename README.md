from random import randint

# 1. Create a variable 'board' with a list of lists to represent the array.

board = []

# Initialize the array including a for-loop and the range() function. Add a list of 5 "O's" for each iteration of the for loop.
for x in range(0,5):
  board.append(["O"] * 5)


# 2. Define a function 'print_board' that takes a 'board_in' as input and prints out each line in 'board_in'.# Printa ut varje rad som "O O O O O" (mellanslag mellan varje 'O').  

def print_board(board):
    for row in board:
       print(" ".join(row))

print_board(board)

# Defines two functions that randomize a row and a column respectively in our game board, and save the result to a variable each to place the ship on.
def random_row(board):
    return randint(0, len(board) - 1)
  
def random_col(board):
    return randint(0, len(board) - 1)
    
ship_row = random_row(board)
ship_col = random_col(board)


# For testing purposes I added a print to see where the ship is hiding

print(ship_row)
print(ship_col)

guess_count = 0

while guess_count < 5:
    guess_row = int(input("Guess row 0-4: "))
    guess_col = int(input("Guess col 0-4: "))
    print_board(board)
    
    if guess_row == ship_row and guess_col == ship_col:
        print("Congratulations, you sank the ship!")
        board[ship_row][ship_col]="S"
        print_board(board)
        break
    else:
        if guess_count == 4:
            print("You have lost the game.")
            break
        elif guess_row > 4 or guess_col > 4:
            print("That is not even in the ocean!")
        elif board[guess_row][guess_col]=="X":
            print("You guessed that already!"
            
        print"Sorry, you missed!")
        board[guess_row][guess_col]="X"
        print_board(board)
        guess_count +=1
        print("You have " + str(5 - guess_count) + " guesses remaining.")
        



    