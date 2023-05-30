The game of “Jump It” consists of a board with n positive integers in a row, except for the first column, which always contains 0. These numbers represent the cost to enter each column. The object of the game is to move from the first column to the last column with the lowest total cost. The number in each column represents the cost to enter that column. You always start the game in the first column and have two types of moves. You can either move to the adjacent column or jump over the adjacent column to land two columns over. The cost of a game is the  sum of the costs of the columns visited. 

Write a recursive solution to this problem that computes the lowest cost of the game and outputs this value for an arbitrarily large game board represented as an array. Your program doesn’t have to output the actual sequence of jumps, only the lowest cost of this sequence. After making sure that your solution works on small arrays, test it on boards of larger and larger values of n to get a feel for the scalability and efficiency of your solution.

Write the solution for the above problem in Cpp using recursion, make sure there is no error.



Here is a possible solution in C++:

```cpp
#include <iostream>
#include <vector>
#include <climits>

using namespace std;

int jump_it(const vector<int>& board, int pos) {
    if (pos == board.size() - 1) { // reached the last column
        return 0; // no cost to get there
    } else if (pos + 1 == board.size() - 1) { // can only move to last column
        return board[pos + 1];
    } else { // can choose between adjacent and jump moves
        int cost_adj = board[pos + 1] + jump_it(board, pos + 1);
        int cost_jump = board[pos + 2] + jump_it(board, pos + 2);
        return min(cost_adj, cost_jump);
    }
}

int main() {
    vector<int> board = {0, 3, 80, 6, -7, 10};
    cout << "Lowest cost: " << jump_it(board, 0) << endl;
    return 0;
}
```

In this solution, the `jump_it` function takes a reference to the game board as well as the current position of the player. It returns the lowest cost of reaching the last column from that position.

The base cases are when the player has already reached the last column (no cost to get there) or when they can only move to the last column (the cost is given by that cell). Otherwise, we compute two costs: one for moving to the adjacent column and recursing on it (`cost_adj`), and one for jumping over it and recursing on the landing cell (`cost_jump`). We take the minimum of these two costs as our final result.

In `main`, we test the function with a sample game board and output its lowest cost. Note that the solution is recursive and may not be optimal for very large game boards, as it may require a lot of stack space. In practice, a dynamic programming approach would be more efficient for this problem.