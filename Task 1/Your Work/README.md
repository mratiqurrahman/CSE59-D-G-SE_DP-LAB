# Software Requirements Specification (SRS)

## Tic-Tac-Toe Game

---

# Preface

This document provides the Software Requirements Specification (SRS) for the **Tic-Tac-Toe** application. It defines the system functionalities, user interactions, performance criteria, and design constraints necessary for the development and deployment of the game.

---

# Version History

| Version | Description                                       |
| ------- | ------------------------------------------------- |
| 1.0     | Initial Draft                                     |
| 1.1     | Added non-functional requirements and UI details  |
| 1.2     | Added system models and game logic specifications |

---

# 1. Introduction

## Purpose

The **Tic-Tac-Toe** application is a standalone desktop game implemented in Java using Swing. It allows two players to play the classic Tic-Tac-Toe game, managing turns, determining winners or ties, and resetting the game board. The system is designed for intuitive gameplay and educational purposes.

---

## Document Conventions

This document follows the IEEE SRS standard using:

* **Must** – Indicates mandatory features or requirements.
* **Should** – Indicates recommended enhancements.
* **May** – Indicates optional future improvements.

---

## Intended Audience and Reading Suggestions

| Audience                      | Purpose                                       |
| ----------------------------- | --------------------------------------------- |
| Developers & Project Managers | Guidance on implementing game logic and UI    |
| QA/Testers                    | Validation of game mechanics and GUI behavior |
| Students/Learners             | Understanding object-oriented GUI programming |

---

## Scope

The Tic-Tac-Toe system provides:

* 3x3 grid-based gameplay for two players
* Turn-based player interaction (X and O)
* Winner detection (rows, columns, diagonals)
* Tie detection
* Graphical user interface (GUI) with Java Swing
* Reset functionality to restart the game

---

## References

* Java Swing API Documentation
* Object-Oriented Programming Standards
* IEEE Standard 830-1998 (SRS Standard)

---

# 2. Overall Description

## Product Perspective

The Tic-Tac-Toe application is a standalone Java desktop game with no external dependencies beyond the Java Runtime Environment (JRE). It provides a graphical interface for two players to play the game locally.

---

## Product Functions

* **Game Board:** 3x3 grid with buttons representing cells.
* **Player Turns:** Alternates between X and O automatically.
* **Winner Detection:** Detects rows, columns, and diagonals for a win.
* **Tie Detection:** Detects a tie when all cells are filled without a winner.
* **Reset Functionality:** Resets board and game state for a new game.
* **GUI Feedback:** Updates labels with current player, winner, or tie.

---

## User Classes and Characteristics

| User Type | Description                  |
| --------- | ---------------------------- |
| Player 1  | Plays as "X"                 |
| Player 2  | Plays as "O"                 |
| Observer  | Watches gameplay and results |

---

## Operating Environment

* Java Runtime Environment (JRE 8+)
* Desktop environment (Windows, macOS, Linux)
* Java Swing GUI framework

---

## Design and Implementation Constraints

* 3x3 fixed grid for gameplay
* Single-threaded, turn-based interaction
* GUI must update in real time after each move
* Game logic must prevent invalid moves (cell overwrite)

---

## Assumptions and Dependencies

* Two players play locally on the same device
* The application will run in a GUI-supported environment
* Users are familiar with basic Tic-Tac-Toe rules

---

# 3. System Requirements Specification

## Functional Requirements

### User Interface

* The system **must** display a 3x3 button grid.
* The system **must** display current player status at the top.
* The system **must** provide a "Reset" button to restart the game.

### Player Turns

* The system **must** alternate between "X" and "O" after each valid move.
* The system **must** prevent a player from overwriting an occupied cell.

### Game Logic

* The system **must** detect a winner in rows, columns, and diagonals.
* The system **must** detect a tie if all cells are filled with no winner.
* The system **must** highlight winning cells in green.
* The system **must** indicate a tie with orange highlights.

### Reset Functionality

* The system **must** clear all cell texts and reset colors when the reset button is clicked.
* The system **must** reset the current player to "X" after reset.
* The system **must** reset the turn counter and game-over state.

---

## Non-Functional Requirements

### Performance Requirements

* The system **must** update the GUI immediately after a move.
* The system **must** handle continuous gameplay without lag.

### Usability Requirements

* The interface **should** be intuitive and easy to navigate.
* The system **should** provide clear visual feedback for turns, wins, or ties.

### Reliability and Availability

* The system **must** accurately enforce game rules.
* The system **must** prevent invalid moves and crashes.

### Maintainability and Support

* The code **should** follow object-oriented principles for easy updates.
* The system **should** log errors for debugging purposes.

### Portability

* The application **must** run on any desktop OS supporting Java.
* The system **may** support future enhancements like online multiplayer.

---

# 4. System Models

## Context Diagram

```
[Player X] --> GUI --> [Game Logic] --> GUI --> [Player O]
```

## Activity Diagram

1. Start Game
2. Player X moves → Update GUI → Check Winner/Tie
3. Player O moves → Update GUI → Check Winner/Tie
4. Repeat until Winner or Tie
5. Optionally reset game

## Use Case Diagram

* **Players:** Make moves, view results
* **System:** Update board, check winner, indicate tie, reset game

## Sequence Diagram

1. Player clicks a cell → Event triggers
2. System updates cell → Switch player
3. System checks winner/tie → Update GUI

## Entity-Relationship Diagram

* Entities: Player, Cell, Game
* Attributes: Player {symbol}, Cell {status}, Game {turns, currentPlayer, gameOver}

---

# 5. System Evolution

## Assumptions

* Multiplayer online support may be added in the future.
* AI opponent functionality may be implemented later.
* Enhanced UI themes may be added.

## Expected Changes

* Integration with networked gameplay.
* Integration with scoring or leaderboard systems.
* Adaptive AI player for single-player mode.

---

# 6. Appendices

## Hardware Requirements

* Desktop PC with JRE installed
* Minimum resolution: 600x750 pixels

## Database Requirements

* Not required; game state maintained in memory

## Suggested Technologies

| Layer              | Technology                    |
| ------------------ | ----------------------------- |
| Frontend           | Java Swing                    |
| Backend/Game Logic | Java                          |
| Platform           | Desktop (Windows/macOS/Linux) |

---

