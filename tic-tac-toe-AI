import math

# Tic-Tac-Toe board
board = [
    [' ', ' ', ' '],
    [' ', ' ', ' '],
    [' ', ' ', ' ']
]

# Check for a win
def is_winner(board, player):
    for row in board:
        if all(cell == player for cell in row):
            return True
    for col in range(3):
        if all(board[row][col] == player for row in range(3)):
            return True
    if all(board[i][i] == player for i in range(3)) or all(board[i][2-i] == player for i in range(3)):
        return True
    return False

# Check if board is full
def is_full(board):
    return all(cell != ' ' for row in board for cell in row)

# Minimax algorithm with Alpha-Beta Pruning
def minimax(board, depth, is_maximizing, alpha, beta):
    if is_winner(board, 'X'):
        return -10 + depth
    if is_winner(board, 'O'):
        return 10 - depth
    if is_full(board):
        return 0

    if is_maximizing:
        max_eval = -math.inf
        for r in range(3):
            for c in range(3):
                if board[r][c] == ' ':
                    board[r][c] = 'O'
                    eval = minimax(board, depth + 1, False, alpha, beta)
                    board[r][c] = ' '
                    max_eval = max(max_eval, eval)
                    alpha = max(alpha, eval)
                    if beta <= alpha:
                        break
        return max_eval
    else:
        min_eval = math.inf
        for r in range(3):
            for c in range(3):
                if board[r][c] == ' ':
                    board[r][c] = 'X'
                    eval = minimax(board, depth + 1, True, alpha, beta)
                    board[r][c] = ' '
                    min_eval = min(min_eval, eval)
                    beta = min(beta, eval)
                    if beta <= alpha:
                        break
        return min_eval

# Get best move for AI
def best_move(board):
    best_val = -math.inf
    move = (-1, -1)
    for r in range(3):
        for c in range(3):
            if board[r][c] == ' ':
                board[r][c] = 'O'
                move_val = minimax(board, 0, False, -math.inf, math.inf)
                board[r][c] = ' '
                if move_val > best_val:
                    best_val = move_val
                    move = (r, c)
    return move

# Example usage
board[0][0] = 'X'
best = best_move(board)
print(f"AI should play at: {best}")
