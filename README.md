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

Since this is a backtracking-based algorithm, it tries all possible moves, then backtracks and makes a decision.

● Maximizer goes LEFT: It is now the minimizers turn. The minimizer now has a choice between 3 and 5. Being the minimizer it will definitely choose the least among both, that is 3

● Maximizer goes RIGHT: It is now the minimizers turn. The minimizer now has a choice between 2 and 9. He will choose 2 as it is the least among the two values. Being the maximizer you would choose the larger value that is 3. Hence the optimal move for the maximizer is to go LEFT and the optimal value is 3.

Now the game tree looks like below:

The above tree shows two possible scores when maximizer makes left and right moves. Note: Even though there is a value of 9 on the right subtree, the minimizer will never pick that. We must always assume that our opponent plays optimally.

# 3.1 Properties of Mini-Max algorithm:
● Complete- Min-Max algorithm is Complete. It will definitely find a solution (if exist), in the finite search tree.

● Optimal- Min-Max algorithm is optimal if both opponents are playing optimally.

● Time complexity- As it performs DFS for the game-tree, so the time complexity of Min-Max algorithm is O(bm), where b is branching factor of the game-tree, and m is the maximum depth of the tree.

● Space Complexity- Space complexity of Mini-max algorithm is also similar to DFS which is O(bm).

# 4. Minimax Algorithm in Game Theory (Alpha-Beta Pruning):
Alpha-Beta pruning is not actually a new algorithm, rather an optimization technique for minimax algorithm. It reduces the computation time by a huge factor. This allows us to search much faster and even go into deeper levels in the game tree. It cuts off branches in the game tree which need not be searched because there already exists a better move available. It is called Alpha-Beta pruning because it passes 2 extra parameters in the minimax function, namely alpha and beta. Let’s define the parameters alpha and beta. Alpha is the best value that the maximizer currently can guarantee at that level or above. Beta is the best value that the minimizer currently can guarantee at that level or above

# 4.1 Alpha-cut and Beta-cut:
ALPHA-BETA cutoff is a method for reducing the number of nodes explored in the Minimax strategy. For the nodes it explores it computes, in addition to the score, an alpha value and a beta value. A beta-cutoff occurs in the alpha-beta algorithm, if the score backed up by the search is greater than or equal to beta and fails high. No further moves need to be searched, since one refutation is already sufficient to avoid the move that led to this node or position. Nodes, where a beta-cutoff occurs are then cut-nodes where move ordering was crucial to try the refutation move as early as possible. In max versus min alpha-beta a beta-cutoff can only occur for the max-player, while the min-player cuts if below or equal alpha, called alpha-cutoff.

Example:

● The initial call starts from A. The value of alpha here is -INFINITY and the value of beta is +INFINITY. These values are passed down to subsequent nodes in the tree. At A the maximizer must choose max of B and C, so A calls B first

● At B it the minimizer must choose min of D and E and hence calls D first.

● At D, it looks at its left child which is a leaf node. This node returns a value of 3. Now the value of alpha at D is max( -INF, 3) which is 3.

● To decide whether its worth looking at its right node or not, it checks the condition beta<=alpha. This is false since beta = +INF and alpha = 3. So it continues the search.

● D now looks at its right child which returns a value of 5.At D, alpha = max(3, 5) which is 5. Now the value of node D is 5

● D returns a value of 5 to B. At B, beta = min( +INF, 5) which is 5. The minimizer is now guaranteed a value of 5 or lesser. B now calls E to see if he can get a lower value than 5.

● At E the values of alpha and beta is not -INF and +INF but instead -INF and 5 respectively, because the value of beta was changed at B and that is what B passed down to E

● Now E looks at its left child which is 6. At E, alpha = max(-INF, 6) which is 6. Here the condition becomes true. beta is 5 and alpha is 6. So beta<=alpha is true. Hence it breaks and E returns 6 to B

● Note how it did not matter what the value of E‘s right child is. It could have been +INF or -INF, it still wouldn’t matter, We never even had to look at it because the minimizer was guaranteed a value of 5 or lesser. So as soon as the maximizer saw the 6 he knew the minimizer would never come this way because he can get a 5 on the left side of B. This way we dint have to look at that 9 and hence saved computation time.

● E returns a value of 6 to B. At B, beta = min( 5, 6) which is 5.The value of node B is also 5

So far this is how our game tree looks. The 9 is crossed out because it was never computed.

● B returns 5 to A. At A, alpha = max( -INF, 5) which is 5. Now the maximizer is guaranteed a value of 5 or greater. A now calls C to see if it can get a higher value than 5.

● At C, alpha = 5 and beta = +INF. C calls F

● At F, alpha = 5 and beta = +INF. F looks at its left child which is a 1. alpha = max( 5, 1) which is still 5.

● F looks at its right child which is a 2. Hence the best value of this node is 2. Alpha still remains 5

● F returns a value of 2 to C. At C, beta = min( +INF, 2). The condition beta <= alpha becomes true as beta = 2 and alpha = 5. So it breaks and it does not even have to compute the entire sub-tree of G.

● The intuition behind this break off is that, at C the minimizer was guaranteed a value of 2 or lesser. But the maximizer was already guaranteed a value of 5 if he choose B. So why would the maximizer ever choose C and get a value less than 2 ? Again you can see that it did not matter what those last 2 values were. We also saved a lot of computation by skipping a whole sub tree.

● C now returns a value of 2 to A. Therefore the best value at A is max( 5, 2) which is a 5.

● Hence the optimal value that the maximizer can get is 5

This is how our final game tree looks like. As you can see G has been crossed out as it was never computed





# 4.2 Move Ordering in Alpha-Beta pruning:
The effectiveness of alpha-beta pruning is highly dependent on the order in which each node is examined. Move order is an important aspect of alpha-beta pruning. It can be of two types: 4.2.1 Worst ordering: In some cases, alpha-beta pruning algorithm does not prune any of the leaves of the tree, and works exactly as minimax algorithm. In this case, it also consumes more time because of alpha-beta factors, such a move of pruning is called worst ordering. In this case, the best move occurs on the right side of the tree. The time complexity for such an order is O(bm). 4.2.2 Ideal ordering: The ideal ordering for alpha-beta pruning occurs when lots of pruning happens in the tree, and best moves occur at the left side of the tree. We apply DFS hence it first search left of the tree and go deep twice as minimax algorithm in the same amount of time. Complexity in ideal ordering is O(bm/2)


# Explanation for minmax code 
End_game(who=’ ‘) in this method we will check who won the game so we will pass the variable who and check if the variable who is empty that means the game ends with a tie and nobody has won If who is equal to X which is the player than the winner is the player And if it is O than the winner is the agent and in this method we will print the size and the maximum depth and we will increase the score of the winner.

Update_board(pos, symbol):In this method the board will start to update by setting 'X'or 'O' in the game board .

HowWon(mark) In this method we will check if there is a win by the positions diagonally or horizontally based on the conditions for example if the X is in position 0,1,2 then it will return true and if there is no win or no position are equal then it will return false.

Check_tie_min() this method will check the game start with empty position .

Minmax(board,depth,inMaximazing ) in this method the min-max algorithm will apply , it will check the method whoWon(mark) and determine the value of each player , in cause the 'O' is won (agent ) the method will return 50 else if the 'X' won (payer) the method will return -50, then the method will check the value of isMaximazing is true bestScore will be initial -50 if isMaximazing is false this score will be initial 800 , the Maximizer is pc and the minimizer is the player .

Pc_pos(): it is the move of the pc while it is true this method will initial with bestScore -50 and with bestMove 0, the depth will increase and print the number of depth and search for an empty position , it will call the method minmax and compeer the score with the bestScore value to decide which position is the best ,so the besScore will update and the best position will be occur in the board.

Cliked() In this method we will take the pos and we will see the possible positions and print it And we will print the depth in each move or position and then we will call method pc_pos() to let the agent play then we will check using method we created before called howWon by passing the symbol X or O If it is X then the winner is the player or user and we will end the game by calling the method end_game() and passing the symbol of the winner And also in this method we will calculate the time it takes for the agent to make a move

Init_score() this method will set the initial state of score equal to 0 

# Explanation for minmax with alpha beta code 
Minmax with alpha beta implantation , it has the same minmax implantation except for two method we have to change it to improve the performance of the code .

Minmax(board,depth,inMaximazing , alpha , beta ) In this method the minmax with alpha beta algorithm will apply after the howwon(mark) method called and return the value in cause the min who won ('player') or if the max who won ('agent'),and will return 0 in cause it is tie .The current score is the current value of method minmax it will set the new bestScore with score value and then compare between the score and alpha current value and update to be the new value of alpha in cause the min(player)turn ,else if it the max(agent) turn to play beta value will update , in both cause once the alpha value is greater than beta value we will discard the branch .

Pc_pos(): it is the move of the pc while it is true this method will initial with bestScore -50 and with bestMove 0,for the initial value for alpha -1000 and for beta 1000 the depth will increase and print the number of depth in each step and search for an empty position , it will call the method minmax and setting in score then compeer the alpha value with scare value ,for the pc move alpha new value will update to be the score value and set the best position to play
