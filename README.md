# tic_tac_toe
def print_board(board):
    """
    Print the Tic-Tac-Toe board.
    """
    for row in board:
        print(" | ".join(row))
        print("-" * 9)

def check_winner(board):
    """
    Check if there is a winner.
    """
    for row in board:
        if row[0] == row[1] == row[2] != " ":
            return row[0]

    for col in range(3):
        if board[0][col] == board[1][col] == board[2][col] != " ":
            return board[0][col]

    if board[0][0] == board[1][1] == board[2][2] != " ":
        return board[0][0]

    if board[0][2] == board[1][1] == board[2][0] != " ":
        return board[0][2]

    return None

def is_board_full(board):
    """
    Check if the board is full.
    """
    for row in board:
        if " " in row:
            return False
    return True

def play_game():
    """
    Play a game of Tic-Tac-Toe.
    """
    board = [[" " for _ in range(3)] for _ in range(3)]
    current_player = "X"

    while True:
        print_board(board)
        print(f"Player {current_player}'s turn.")

        # Get the player's move
        row = int(input("Enter the row number (0-2): "))
        col = int(input("Enter the column number (0-2): "))

        # Validate the move
        if row < 0 or row > 2 or col < 0 or col > 2 or board[row][col] != " ":
            print("Invalid move. Try again.")
            continue

        # Make the move
        board[row][col] = current_player

        # Check if there is a winner
        winner = check_winner(board)
        if winner:
            print_board(board)
            print(f"Player {winner} wins!")
            break

        # Check if the board is full
        if is_board_full(board):
            print_board(board)
            print("It's a tie!")
            break

        # Switch to the other player
        current_player = "O" if current_player == "X" else "X"

play_game()
