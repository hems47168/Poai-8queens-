# Poai-8queens-
def solve_queens(n):
    def can_place(board, row, col):
        for i in range(row):
            if board[i] == col or \
                board[i] - i == col - row or \
                board[i] + i == col + row:
                return False
        return True

   def place_queens(n, row, board):
        if row == n:
            result.append(board[:])
            return
        for col in range(n):
            if can_place(board, row, col):
                board[row] = col
                place_queens(n, row + 1, board)

   result = []
    place_queens(n, 0, [-1]*n)
    return result

def print_board(n, solution):
    for i in range(n):
        row = ''
        for j in range(n):
            if solution[i] == j:
                row += 'Q '
            else:
                row += '. '
        print(row)
    print()

n = 8
solutions = solve_queens(n)
for i, solution in enumerate(solutions):
    print(f"Solution {i+1}:")
    print_board(n, solution)
