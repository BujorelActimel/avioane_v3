# Aircraft Battle Game - Use Case Descriptions

## UC1: Create Game Room

**Actor:** Player

**Description:** A player creates a new game room to host an Aircraft Battle match.

**Preconditions:** Player is connected to the game system.

**Main Success Scenario:**

1. Player selects "Create Room" option from the main menu.
2. System creates a new game room with a unique identifier.
3. System assigns the player as Player 1.
4. System displays the room ID to the player.
5. Player waits for an opponent to join.

**Alternative Scenarios:**

* **A1: Connection Error**
  * At step 2, if there's a server connection error:
    1. System displays an error message.
    2. Player can try again or return to the main menu.

## UC2: Join Game Room

**Actor:** Player

**Description:** A player joins an existing game room using a room ID.

**Preconditions:** Player is connected to the game system, and a valid game room exists.

**Main Success Scenario:**

1. Player selects "Join Room" option from the main menu.
2. System prompts player to enter a room ID.
3. Player enters the room ID.
4. System validates the room ID and adds the player to the room.
5. System assigns the player as Player 2.
6. System notifies both players that the game is starting.
7. System transitions both players to the placement phase.

**Alternative Scenarios:**

* **A1: Invalid Room ID**
  * At step 4, if the room ID is invalid:
    1. System displays "Room not found" error.
    2. Player can enter a different ID or cancel.
* **A2: Room is Full**
  * At step 4, if the room already has two players:
    1. System displays "Room is full" error.
    2. Player returns to the main menu.
* **A3: Connection Error**
  * At step 4, if there's a server connection error:
    1. System displays an error message.
    2. Player can try again or return to the main menu.

## UC3: Place Planes

**Actor:** Player

**Description:** A player positions their aircraft on their grid before the battle begins.

**Preconditions:** Player is in a game room with an opponent, and the game is in the placement phase.

**Main Success Scenario:**

1. System displays player's empty grid and placement controls.
2. Player positions planes on their grid:
   a. Player selects a cell to place plane.
   b. System displays plane preview on the grid.
   c. Player can rotate the plane by pressing 'R'.
   d. Player confirms placement by clicking.
3. Steps 2a-2d are repeated until all 3 planes are placed.
4. Player indicates readiness by clicking "Ready" button.

**Alternative Scenarios:**

* **A1: Invalid Placement**
  * At step 2d, if the placement is invalid (out of bounds or overlapping):
    1. System displays invalid placement preview.
    2. Player must select a different position.
* **A2: Remove Plane**
  * Between steps 2 and 3, player can right-click on a placed plane:
    1. System removes the plane.
    2. Player can place the plane again.
* **A3: Connection Lost**
  * If connection is lost during placement:
    1. System attempts to reconnect.
    2. If reconnection is successful, player continues placement.
    3. If reconnection fails, player returns to main menu.

## UC4: Ready Status

**Actor:** Player

**Description:** A player indicates they have completed plane placement and are ready to start the game.

**Preconditions:** Player has placed all three planes on their grid.

**Main Success Scenario:**

1. Player clicks "Ready" button after placing all planes.
2. System marks the player as ready.
3. System waits for opponent to be ready.
4. When both players are ready, system starts the battle phase.
5. System randomly determines which player goes first.
6. System notifies both players that the battle has begun.

**Alternative Scenarios:**

* **A1: Not All Planes Placed**
  * At step 1, if player hasn't placed all planes:
    1. "Ready" button is disabled.
    2. Player must place remaining planes.
* **A2: Opponent Disconnects**
  * At step 3, if opponent disconnects:
    1. System notifies player that opponent disconnected.
    2. Player returns to main menu.

## UC5: Attack Enemy Grid

**Actor:** Player

**Description:** During their turn, a player attacks a cell on the opponent's grid.

**Preconditions:** Game is in battle phase, and it's the player's turn.

**Main Success Scenario:**

1. System indicates it's the player's turn.
2. Player selects a cell on the opponent's grid to attack.
3. System processes the attack:
   a. Records the attack.
   b. Determines if attack hit or missed.
   c. Determines if attack hit a plane head.
4. System displays the result (hit, head hit, or miss) on both players' screens.
5. System checks if the game is over (3 plane heads hit).
6. If game is not over, system switches turn to the opponent.

**Alternative Scenarios:**

* **A1: Cell Already Attacked**
  * At step 2, if the cell was already attacked:
    1. System ignores the action.
    2. Player must select a different cell.
* **A2: Game Won**
  * At step 5, if player has hit all 3 plane heads:
    1. System declares player as the winner.
    2. Game ends and results are displayed.
* **A3: Connection Lost During Turn**
  * If connection is lost during player's turn:
    1. System attempts to reconnect.
    2. If successful, game continues.
    3. If failed, opponent is notified and game ends.

## UC6: Mark Suspected Planes

**Actor:** Player

**Description:** A player marks cells where they suspect opponent's planes might be located.

**Preconditions:** Game is in battle phase.

**Main Success Scenario:**

1. Player right-clicks on a cell in the opponent's grid.
2. System displays a mark on the cell (visible only to the player).
3. If the cell was already marked, the mark is removed.

**Alternative Scenarios:**

* **A1: Cell Already Attacked**
  * At step 1, if the cell was already attacked:
    1. Mark can still be applied or removed (for player's reference).
