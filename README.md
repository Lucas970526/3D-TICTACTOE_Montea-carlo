# Monte Carlo Tree Search Implementation for 3D Tic-tac-toe (4x4x4)

## Introduction
This report details the implementation of Monte Carlo Tree Search (MCNT) algorithm for a 3D version of Tic-tac-toe played on a 4x4x4 grid. The implementation aims to create an AI agent capable of learning optimal playing strategies through repeated simulations and value function approximation.

## Game Environment

### Board Structure
- 4x4x4 three-dimensional grid
- Total of 64 possible positions (4 × 4 × 4)
- Two players: P1 (value: 1) and P2 (value: -1)
- Empty cells represented by 0

### Winning Conditions
The game considers the following winning patterns:
- Four consecutive marks in any horizontal row (16 possible)
- Four consecutive marks in any vertical column (16 possible)
- Four consecutive marks in any layer (16 possible)
- Four consecutive marks in any diagonal within a plane
- Four consecutive marks in any 3D diagonal across layers

## MCNT Implementation Methodology

### State Representation
#### Board State
- Represented as a 3D numpy array (4×4×4)
- Each cell contains 1 (P1), -1 (P2), or 0 (empty)
- State hash created by flattening the 3D array to a string

#### Game State Management
- Tracks current player's turn
- Maintains game ending conditions
- Records available positions for moves

### Learning Process

#### Initialization
Two agents (P1 and P2) created with:
- Exploration rate (epsilon = 0.3)
- Learning rate (alpha = 0.2)
- Discount factor (gamma = 0.3)
- Empty state-value dictionary

#### Training Iteration
Each training episode follows these steps:

##### State Selection
- Current player evaluates board state
- Available positions determined
- Action selected based on epsilon-greedy strategy

##### Action Selection
Exploration (Random Action):
- Probability: epsilon
- Randomly select from available positions

Exploitation (Best Action):
- Probability: 1 - epsilon
- Choose position with highest stored state value
- If no stored value, initialized to 0

##### State Update Process
- Selected action applied to board
- New state hash generated
- State added to agent's history
- Player symbol switched

##### Reward Distribution
When game ends:
- Win: Reward = 1
- Loss: Reward
