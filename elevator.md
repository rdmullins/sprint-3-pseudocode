# Sprint 3: Pseudocode
## How an Elevator Works
### by Roger Mullins, Team DaVinci

---

## Assumptions
- The elevator object is in working order
- There is a steady power supply
- Floor numbers are encoded by the push buttons so that numbers outside the permitted range cannot be entered
- The elevator can determine its current position by accessing an automatic counter that increments as it ascends and decrements as it goes down
- The elevator is maintained such that it is able to perform the functions below

## Inputs
- Call
    - Up
    - Down
- Floor Selection (from panel inside elevator car)

## Functions
- goUp()
- goDown()
- doorsOpen()
- doorsClose()

## Variables (and Permitted Values)
- floorNumberCall (value range established by system)
- floorNumberLocation (value range established by system)
- travel

## Properties (and States)
- motor
    - off
    - on-up
    - on-down
- upButton (boolean)
    - pressed = TRUE
    - notPressed = FALSE
- downButton (boolean)
    - pressed = TRUE
    - notPressed = FALSE
- floorButton (boolean)
    - pressed = TRUE
    - notPressed = FALSE
- elevator
    - goingUp (boolean)
    - comingDown (boolean)
    - stopped (boolean)
    - current location (int)
    - tripQueue (array of upcoming stops)

## Event: User Pushes the 'Up' Button 

1. floorNumberCall <- Floor number from which call originated
1. floorNumberLocation <- elevator.currentLocation
1. moving
    - <- TRUE IF elevator.goingUp OR elevator.comingDown
    - <- FALSE IF elevator.stopped
1. travel <- floorNumberCall - floorNumberLocation
1. IF (travel < 0), call came from below the current location
    - (SET travel = absolute value of travel)
    - WHEN elevator.comingDown, add floorNumberCall to elevator.tripQueue
1. IF (travel > 0 and elevator.goingUp), call came from above the current location
    - INSERT floorNumberCall into the elevator.tripQueue
1. IF (travel == 0), STOP the elevator car and elevator.doorsOpen()

## Event: User Pushes the 'Down' Button

1. floorNumberCall <- Floor number from which call originated
1. floorNumberLocation <- elevator.currentLocation
1. moving
    - <- TRUE IF elevator.goingUp OR elevator.comingDown
    - <- FALSE IF elevator.stopped
1. travel <- floorNumberCall - floorNumberLocation
1. IF (travel < 0), call came from below the current location
    - INSERT floorNumberCall into the elevator.tripQueue
1. IF (travel > 0 and elevator.goingUp), call came from above the current location
    - (SET travel = absolute value of travel)
    - WHEN elevator.comingDown, add floorNumberCall to elevator.tripQueue
1. IF (travel == 0), STOP the elevator car and elevator.doorsOpen()

## Event: User Inside the Elevator Car Selects Floor



FUNCTION goUp()
1. IF upButton
2. elevator.motor = off
3. travel = floorNumberLocation - floorNumberCall
4. IF (travel < 0)
    a. GET absolute value of travel
    b. elevator.motor = on-up
    c. CALL FUNCTION elevator.goUp(travel)
    d. CALL FUNCTION elevator.doorsOpen()
5. ELSE IF (travel > 0)
    a. elevator.motor = on-down
    b. CALL FUNCTION elevator.goDown(travel)
    c. CALL FUNCTION elevator.doorsOpen()
6. ELSE
    a. CALL FUNCTION elevator.doorsOpen()