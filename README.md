# Aircraft Battle Game

A real-time multiplayer aircraft battle game where players strategically place and attack aircraft on a grid.

Overview

Aircraft Battle is a turn-based strategy game inspired by the classic Battleship game but with aircraft instead of ships. Players position their planes on a 10x10 grid and take turns attacking each other's grids, aiming to hit the opponent's plane heads. The first player to hit all three of the opponent's plane heads wins the game.

## Features

* Real-time multiplayer gameplay using WebSockets
* Room-based matchmaking system
* Interactive aircraft placement with rotation
* Turn-based battle system
* Strategic cell marking for tracking suspected plane locations
* Responsive design that works on both desktop and mobile
* Game statistics tracking
* Recent games history

## Technology Stack

* **Frontend** : HTML5, CSS3, JavaScript (ES6+)
* **Backend** : Go (Golang)
* **Communication** : WebSockets

## Installation

### Prerequisites

* Go 1.24 or higher
* Modern web browser (Chrome, Firefox, Safari, Edge)

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/aircraft-battle.git
   cd aircraft-battle
   ```
2. Build the Go server:
   ```bash
   go build -o aircraft-battle main.go
   ```
3. Run the server:
   ```bash
   ./aircraft-battle
   ```
4. Open your browser and navigate to:
   ```
   http://localhost:8080
   ```

## How to Play

### Game Rules

1. **Setup Phase** :

* Each player places 3 aircraft on their 10x10 grid
* Each aircraft occupies 10 cells in the shape of an airplane
* Aircraft cannot overlap or extend beyond the grid boundaries
* Once both players have placed their aircraft and clicked "Ready", the battle begins

1. **Battle Phase** :

* Players take turns attacking cells on the opponent's grid
* If an attack hits a cell occupied by an airplane, it's marked as a hit
* If an attack hits a plane's head, it's marked as a head hit
* The first player to hit all 3 of the opponent's plane heads wins

### Controls

* **Menu Screen** :
* Click "Create Room" to host a new game
* Click "Join Room" to join an existing game with a room ID
* **Placement Phase** :
* Left-click to place an airplane
* Right-click to remove a placed airplane
* Press 'R' key to rotate the airplane before placement
* Click "Ready" when all planes are placed
* **Battle Phase** :
* Left-click on opponent's grid to attack a cell
* Right-click to mark/unmark cells for strategic planning
