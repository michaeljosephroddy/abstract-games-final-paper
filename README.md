# CM1 Abstract Games for Two Players

## An Analysis of Heuristics in Reversi
### By Michael Roddy, Arran Tyson, & Shane Dowd
#### Project Supervisor: Conn Mulvihill
#### Prepared for CT328 – Final Year Project
#### Date: 16/04/18

---

## Abstract

Game playing in artificial intelligence (AI) has garnered significant attention, with Reversi/Othello emerging as a particularly suitable domain for developing and testing heuristic strategies. This paper explores the interplay of various heuristics in Reversi, aiming to assess their individual contributions and interactions. By examining existing strategies and developing a novel heuristic, the project seeks to enhance our understanding of heuristic effectiveness in this abstract two-player game.

Reversi’s complexity, with a branching factor of 10, provides a balanced environment for tractable yet meaningful exploration of strategies. Our study evaluates heuristics implemented in Python, analyzing their performance through extensive experimentation. This paper also introduces a new heuristic, **getBestMove()**, designed to optimize gameplay by leveraging control over critical board positions.

---

## 1. Introduction

Game playing is a cornerstone of AI research, often serving as a benchmark for machine intelligence. In games like Reversi, AI programs routinely outperform human players due to superior "look-ahead" capabilities and strategic reasoning. Reversi, with its moderate complexity, provides an ideal testbed for heuristic analysis.

The project investigates heuristic strategies inspired by Al Sweigert’s work. These strategies are tested, ranked, and analyzed to understand their relative effectiveness. We also develop a new heuristic that emphasizes control of key board positions, aiming to outperform existing strategies. The paper is structured as follows:

1. Introduction to Reversi and AI game playing.
2. Description of Reversi rules.
3. Implementation of the game and heuristics in Python.
4. Analysis of existing heuristics.
5. Development and testing of a new heuristic.
6. Conclusion and evaluation of findings.

---

## 2. Reversi Rules

Reversi is played on an 8x8 board, starting with a predefined configuration of four pieces. Players alternate turns, aiming to maximize their pieces on the board by flipping opponent pieces through valid moves. The game ends when no valid moves remain, and the player with the most pieces wins.

Key rules:
- **Starting Configuration:** Four pieces form a diagonal in the center of the board.
- **Moves:** Players place pieces to flank and convert opponent’s pieces.
- **Objective:** Maximize the number of pieces owned by the end of the game.
- **End Game:** Occurs when no valid moves remain.

---

## 3. Implementation

The Reversi game was implemented using Python, based on Al Sweigert’s code from *Invent With Python*. Modifications included enabling the computer to play itself (AISim1.py) and simulating multiple games (AISim2.py). Additional functions were developed to implement and test new heuristics (AISim3.py).

Key features:
- **AISim1.py:** Modified for AI vs AI gameplay.
- **AISim2.py:** Enhanced to simulate and analyze multiple games.
- **AISim3.py:** Introduced new heuristic strategies for evaluation.

---

## 4. Analysis of Existing Heuristics

We evaluated Sweigert’s heuristics over 200 simulated games, ranking them based on performance against each other. Key findings include:

1. **getComputerMove():** Most effective baseline strategy, prioritizing corners and high-scoring moves.
2. **getRandomMove():** Performed poorly due to lack of strategy.
3. **getCornerSideBestMove():** Inferior to getComputerMove() due to over-prioritization of side squares.
4. **getWorstMove():** Consistently underperformed by choosing suboptimal moves.
5. **getSideBestMove():** Improved over getCornerSideBestMove but still less effective than getComputerMove().

---

## 5. Development of New Heuristic: **getBestMove()**

### Design Principles
The **getBestMove()** heuristic builds upon the strengths of getComputerMove() while introducing additional strategies:
- Prioritize corners.
- Secure adjacent critical positions (“optimal spots”) that increase the likelihood of gaining corners.
- Avoid “danger spots” adjacent to corners that give opponents positional advantages.

### Implementation
Key features of **getBestMove()**:
- Identify and prioritize optimal spots around corners.
- Force opponents into danger spots, increasing the player’s chances of controlling corners.

### Testing and Results
We tested **getBestMove()** against Sweigert’s heuristics over 200 games. Results demonstrated superior performance:
- **getBestMove() vs. getSideBestMove():** 85.5% win rate.
- **getBestMove() vs. getComputerMove():** Marginal improvement in win rate.

The strategy’s emphasis on corner control and optimal positioning proved highly effective.

---

## 6. Conclusion

Our analysis confirms that heuristics significantly influence Reversi gameplay. The newly developed **getBestMove()** heuristic outperformed existing strategies by leveraging corner control and positional advantages. Future work could explore further refinements, such as adaptive heuristics based on game state or machine learning approaches to optimize gameplay.

This project underscores the potential of heuristic strategies in abstract games and highlights their broader implications for AI research.

---

## Appendix

- **Figures:** Initial board setup, heuristic testing results, and code snippets for AISim1, AISim2, and AISim3.
- **References:** Sweigert, A. (Year). *Invent With Python*. [Chapter 15-16]
- **Acknowledgments:** Thanks to Conn Mulvihill for supervision and guidance.
