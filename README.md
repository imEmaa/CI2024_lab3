# CI2024_lab3 - N-puzzle solver

## Summary

- Solvability of the problem
- A* Algorithm
- - Heuristic

## Solvability of the problem
Not all N-puzzle are solvable, so i generate a random state at the beginning which is solvable ( there is a is_solvable function that check the solvability ).  
In the current version, called 1.0, i haven't tried yet with a 5x5 puzzle 'cause it seems the algorithm can't solve in reasonable time, but it gives an instant solution for 3x3 puzzles and some 4x4.   
Generally, a solution for 4x4 is obtained in a few minutes, but sometimes it requires much more time

## A* algorithm
Following professor suggestion i decided to use the A* algorithm, using an heuristic distance, to solve the problem.  
The core of the algorithm is the heuristic, that will be explained later in this report.  
I have two auxiliar functions - to_tuple and to_matrix - because i use the heapq module and i need to work with tuple, but also i prefer to use matrix for actions and other stuffs.  
Maybe with another approach computational time can decrease.

### Heuristic
1. Manhattan distance  
The classical heuristic is the manhattan distance: i will not spend a lot of words since I think it is already known  

2. Linear conflict distance
I found online some report about Manhattan distance and its variants: one of them is this linear conflict.  
"It applies when two tiles are in their goal row or column, but are reversed relative to their goal positions."  
From: AAAI-96 Proceedings - https://cdn.aaai.org/AAAI/1996/AAAI96-178.pdf
- Example with a 3x3 - Initial state: [1, 3, 7], [4, 6, 5], [0, 2, 8]  
Manhattan distance: len(open_list): 172, len(close_list): 275, solved with 23 steps  
Linear conflict distance: len(open_list): 126, len(close_list): 202, solved with 23 steps

## Conclusions
As shown in the linear conflict distance example, a 3x3 requires about 200 states in the close_list. A 4x4 requires about 120k, so the problem size grow very fast.  
Probably with a better heuristic we can also solve a 4x4 problem efficiently and try also to solve a 5x5 in reasonable time
- Example of a 4x4 - Initial state: [[11 14  0  3], [ 4  5  1 10], [13  8 12  2], [15  7  9  6]]  
Linear conflict distance: len(open_list): 102535, len(close_list): 117444, solved with 50 steps