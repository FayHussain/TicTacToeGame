# TicTacToeGame



# Introduction
The main goal of this tutorial is to explain the main concepts of adversarial search and games to help the reader to learn more about them. Also, how to apply both Minimax and Alpha-Beta pruning Algorithms on the same application (in our tutorial it will be a Tic-Tac-Toe game) and compare between these two algorithms in terms such as time complexity, etc.


# 1. Game trees
In board games, game trees are commonly used to determine the best possible move. As an example, Tic-Tac-Toe will be used.

The idea is to start at the current board position and go through all the possible moves that the computer can make. Then, based on each of those possible moves, consider what moves the opponent might make. Then return your gaze to the computer. The computer should ideally flip back and forth, making moves for both it-self and its opponent, until the game is finished. It will do this for every possible outcome, effectively playing thousands (if not millions) of games. It attempts to determine the outcome that gives it the best chance of success based on the winners and losers of these games This is like how people think during a board game, such as "if I make this move, they could make this one, and I could counter with this," and so on. That is exactly what game trees do. They examine every possible move as well as every opponent’s move and then try to determine if they are winning after as many moves as they can think of.



# 1.1 Game as search
A Game can be defined as a search by specifying each of the following elements:

1.1.1 Initial state: defines the initial configuration of the game and identifies the first player to move.

1.1.2 state space: configurations or collections of states that can be reached via the successor function from the starting state

1.1.3 Goal test: which checks whether a given state is a goal state or not. States where the game ends are called terminal states (leaf nodes).

1.1.4 Successor function: identifies which are the possible states that can be achieved from the current state. This function returns a list of (move, state) pairs, each indicating a legal move and the resulting state.


# 1.2 Evaluation function
An evaluation function returns an estimate of the expected utility of the game from a given position. This gives a numeric value for the terminal states, for example in Tic-Tac-Toe the outcome is win, lose, or tie, with values +50 for win, -50 for lose, or 0 tie. Some games have a wider range of possible outcomes

# 1.3 Performance measure
The performance measure is the unit to define the success of an agent. Performance varies with agents based on their different precepts. It can be different from game to game but for example, in Tic-Tac-Toe one of the performance measures is making the best moves.

# 1.4 Game Applications
Game theory has vast applications in different fields. Some of the important ones are mentioned below.

1.4.1 Entertainment: Game theory is used to define different strategies of different games.

1.4.2 Economics: Each factor in the market, such as seasonal preferences, buyer choice, changes in supply and material costs, and other such market factors can be used to describe strategies to maximize the outcome and thus the profit.

1.4.3 Military: Game theory can be useful in the Military also. Military strategists have turned to game theory to play "war games". Usually, such games are not zero-sum games, for losses to one side are not won by the other.

1.4.4 Political science: The properties of n-person non-zero-sum games can be used to study different aspects of political science and social science. Matters such as distribution of power, interactions between nations, the distribution of classes and their effects of government, and many other matters can be easily investigated by breaking the problem down into smaller games, each of whose outcomes affect the final result of a larger game.

# 2. An example X-O game:
Tic-tac-toe is a two-player game (in this program it will be between HUMAN and COMPUTER). One player selects 'O' and the other selects 'X' to mark their specific cells. The game begins with one of the players and ends when one of the players has filled one entire row/column/diagonal with his/her specific character 'O' or 'X', If no one ends up winning, the game is said to be a tie. Tic-Tac-Toe is one of the adversarial games. A competitive environment in which each player's goal is to minimize the enemy's score and thus maximize their own score is referred to as an adversarial environment.

actions: the available positions the player can choose based on the current board state. Also, the player can choose the location according to the position numbers.

Evaluation function: Return +50 if the computer wins, -50 if the player wins, or 0 otherwise (Tie).

cost: 1 per action

# 2.3 PEAS:
2.3.1 Performance measures:
● number of losses, draws and wins

● agent can play the game

● minimum cost

● make the best moves

# 2.3.2 Actuators:
● Human

● the opponent

● the ENTER button on the computer.

# 2.3.3 Sensors:
● Keyboard

● The codes

# 2.3.4 Environment



# 2.4 Game Tree:
We can define the game Tic Tac Toe as a tree with the initial state as the root of the tree. We use the term search tree to describe a tree that is superimposed on the game tree and examines enough nodes to determine what move to make. The following figure shows the game tree.



# 3. Minimax Algorithm in Game Theory| (Introduction):
Minimax is a type of backtracking algorithm used in decision making and game theory to determine the best move for a player, assuming that your opponent also plays optimally. It is commonly used in two-player turn-based games like Tic-Tac-Toe, Backgammon, Mancala, and Chess. The two players in Minimax are known as the maximizer and minimizer in our case X is the maximizer and O is the minimizer. The maximizer tries to get the highest possible score, whereas the minimizer tries to get the lowest possible score. Every board state is associated with a value. If the maximizer has the upper hand in a given state, the board score will tend to be positive. If the minimizer has the upper hand in that board state then it will tend to be some negative value

Example:

Consider a game which has 4 final states and paths to reach final state are from root to 4 leaves of a perfect binary tree as shown below. Assume you are the maximizing player and you get the first chance to move, i.e., you are at the root and your opponent at next level. Which move you would make as a maximizing player considering that your opponent also plays optimally?

