# Sprint 3: Pseudocode
## How an Elevator Works
### by Roger Mullins, Team DaVinci

---

## Assumptions
- The elevator object is in working order
- There is a steady power supply
- Floor numbers are encoded by the push button so that numbers outside the permitted range cannot be entered
- The elevator can determine its current position by accessing an automatic counter that increments as it ascends and decrements as it goes down
- The elevator is maintained such that it is able to perform the functions below

## Functions
- goUp()
- goDown()
- doorsOpen()
- doorsClose()

## Variables (and Permitted Values)
- floorNumberCall
- floorNumberLocation
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

*** The Elevator is Event-Driven ***

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