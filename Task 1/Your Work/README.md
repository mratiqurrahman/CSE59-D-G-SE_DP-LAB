# Software Requirements Specification (SRS)

# Tic-Tac-Toe Game

------------------------------------------------------------

# Preface

This document provides the Software Requirements Specification (SRS) for the Tic-Tac-Toe application. It defines the system functionalities, user interactions, performance criteria, design constraints, and system models required for the development and deployment of the game.

------------------------------------------------------------

# Version History

| Version | Description |
|---------|-------------|
| 1.0 | Initial Draft |
| 1.1 | Added GUI and non-functional requirements |
| 1.2 | Added system models and game logic |
| 1.3 | Updated ER Diagram and relationships |

------------------------------------------------------------

# 1. Introduction

## 1.1 Purpose

The Tic-Tac-Toe application is a standalone desktop-based game developed using Java and Swing. The application allows two users to play the classic Tic-Tac-Toe game on a 3×3 grid. The system manages player turns, validates moves, detects winners or ties, and provides reset functionality.

The system is designed for educational purposes and to demonstrate object-oriented programming concepts and graphical user interface development using Java Swing.

------------------------------------------------------------

## 1.2 Document Conventions

This document follows the IEEE SRS documentation standard.

| Keyword | Meaning |
|---------|---------|
| Must | Mandatory requirement |
| Should | Recommended requirement |
| May | Optional enhancement |

------------------------------------------------------------

## 1.3 Intended Audience

| Audience | Purpose |
|---------|---------|
| Developers | Implement application features |
| Testers | Validate system behavior |
| Students | Learn Java GUI programming |
| Project Managers | Understand project scope |

------------------------------------------------------------

## 1.4 Scope

The Tic-Tac-Toe application provides:

- 3×3 grid-based gameplay
- Two-player local gameplay
- Turn-based interaction
- Winner detection
- Tie detection
- Graphical User Interface (GUI)
- Game reset functionality
- Visual feedback for game results

------------------------------------------------------------

## 1.5 References

- Java Swing Documentation
- IEEE Standard 830-1998
- Object-Oriented Programming Principles

------------------------------------------------------------

# 2. Overall Description

## 2.1 Product Perspective

The system is a standalone desktop application developed using Java Swing. It does not require internet connectivity or external databases. The application runs locally on desktop operating systems supporting Java Runtime Environment (JRE).

------------------------------------------------------------

## 2.2 Product Functions

The system provides the following functionalities:

- Display a 3×3 game board
- Allow players to place X or O symbols
- Alternate turns automatically
- Detect winning combinations
- Detect tie conditions
- Highlight winning or tied cells
- Reset the game board
- Display game status messages

------------------------------------------------------------

## 2.3 User Classes and Characteristics

| User Type | Description |
|-----------|-------------|
| Player 1 | Uses symbol X |
| Player 2 | Uses symbol O |
| Observer | Watches gameplay |

------------------------------------------------------------

## 2.4 Operating Environment

- Java Runtime Environment (JRE 8 or above)
- Windows, Linux, or macOS
- Java Swing Framework

------------------------------------------------------------

## 2.5 Design and Implementation Constraints

- Fixed 3×3 grid
- Turn-based gameplay
- Single-threaded execution
- GUI updates must occur instantly
- Occupied cells cannot be overwritten

------------------------------------------------------------

## 2.6 Assumptions and Dependencies

- Two users play on the same device
- Users understand Tic-Tac-Toe rules
- Java is installed on the system

------------------------------------------------------------

# 3. System Requirements Specification

## 3.1 Functional Requirements

### 3.1.1 User Interface Requirements

- The system must display a 3×3 button grid.
- The system must display the current player's turn.
- The system must provide a reset button.
- The system must display winner or tie messages.

------------------------------------------------------------

### 3.1.2 Player Turn Requirements

- The system must alternate between X and O.
- The system must prevent invalid moves.
- The system must disable already occupied cells.

------------------------------------------------------------

### 3.1.3 Game Logic Requirements

- The system must detect row victories.
- The system must detect column victories.
- The system must detect diagonal victories.
- The system must detect ties.
- The system must highlight winning cells.
- The system must stop gameplay after game over.

------------------------------------------------------------

### 3.1.4 Reset Requirements

- The system must clear all cells after reset.
- The system must restore default colors.
- The system must reset the current player to X.
- The system must reset game status variables.

------------------------------------------------------------

## 3.2 Non-Functional Requirements

### Performance Requirements

- GUI response must be immediate.
- The system must support continuous gameplay smoothly.

------------------------------------------------------------

### Usability Requirements

- Interface should be simple and user-friendly.
- Game feedback should be visually clear.

------------------------------------------------------------

### Reliability Requirements

- The system must prevent crashes.
- The system must enforce all game rules correctly.

------------------------------------------------------------

### Maintainability Requirements

- The code should follow object-oriented principles.
- The application should support future feature expansion.

------------------------------------------------------------

### Portability Requirements

- The system must run on all desktop operating systems supporting Java.
- Future versions may support online multiplayer.

------------------------------------------------------------

# 4. System Models

## 4.1 Context Diagram

[Player X] --> GUI --> [Game Logic] --> GUI --> [Player O]

------------------------------------------------------------

## 4.2 Activity Diagram

1. Start Game
2. Player X makes move
3. Update GUI
4. Check winner or tie
5. Switch player
6. Repeat until game ends
7. Reset game if required

------------------------------------------------------------

## 4.3 Use Case Diagram

Actors:
- Player X
- Player O

Use Cases:
- Make move
- View result
- Reset game

------------------------------------------------------------

## 4.4 Sequence Diagram

1. User clicks a cell
2. Event handler processes click
3. Cell updates symbol
4. System checks game state
5. GUI updates display

------------------------------------------------------------

## 4.5 Entity-Relationship Diagram

### Entities

1. Player
2. Game
3. Cell

------------------------------------------------------------

### Player Entity

| Attribute | Description |
|-----------|-------------|
| player_id (PK) | Unique player identifier |
| symbol | X or O |

------------------------------------------------------------

### Game Entity

| Attribute | Description |
|-----------|-------------|
| game_id (PK) | Unique game identifier |
| currentPlayer | Current player's turn |
| turns | Number of moves |
| gameOver | Game status |

------------------------------------------------------------

### Cell Entity

| Attribute | Description |
|-----------|-------------|
| cell_id (PK) | Unique cell identifier |
| row | Cell row |
| column | Cell column |
| status | Empty, X, or O |
| game_id (FK) | Associated game |

------------------------------------------------------------

### ER Diagram

                    +------------------+
                    |      PLAYER      |
                    +------------------+
                    | PK player_id     |
                    | symbol           |
                    +------------------+
                             |
                             | plays
                           (2:1)
                             |
                             v
                    +------------------+
                    |       GAME       |
                    +------------------+
                    | PK game_id       |
                    | currentPlayer    |
                    | turns            |
                    | gameOver         |
                    +------------------+
                             |
                             | contains
                           (1:9)
                             |
                             v
                    +------------------+
                    |       CELL       |
                    +------------------+
                    | PK cell_id       |
                    | row              |
                    | column           |
                    | status           |
                    | FK game_id       |
                    +------------------+

------------------------------------------------------------

### Relationship Description

| Relationship | Cardinality | Description |
|-------------|-------------|-------------|
| Player → Game | 2 : 1 | Two players participate in one game |
| Game → Cell | 1 : 9 | One game contains nine cells |

------------------------------------------------------------

# 5. System Evolution

## 5.1 Future Enhancements

- AI opponent support
- Online multiplayer functionality
- Scoreboard system
- Enhanced UI themes
- Sound effects and animations

------------------------------------------------------------

# 6. Appendices

## 6.1 Hardware Requirements

- Desktop or Laptop Computer
- Minimum resolution: 600×750
- Keyboard and mouse

------------------------------------------------------------

## 6.2 Software Requirements

- Java Runtime Environment (JRE 8+)
- Operating System: Windows/Linux/macOS

------------------------------------------------------------

## 6.3 Database Requirements

- No database required
- Game state maintained in memory

------------------------------------------------------------

## 6.4 Technologies Used

| Layer | Technology |
|-------|------------|
| Frontend | Java Swing |
| Backend/Game Logic | Java |
| Platform | Desktop Application |

------------------------------------------------------------
