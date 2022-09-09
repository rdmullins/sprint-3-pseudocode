# Sprint 3: Pseudocode
## Elevator
### by Roger Mullins, Team DaVinci

---

## Assumptions
- The elevator object is in working order and maintained such that it is able to perform the functions below
- There is a steady power supply
- **Floor numbers** (int values passed to and used by functions and properties) are encoded by the push buttons so that numbers outside the permitted range cannot be entered
- The elevator can determine its current position by accessing an automatic counter that increments as it ascends and decrements as it goes down using sensors

## Elevator Object
### Functions

| Name | Parameter(s) |
| --- | --- |
| handleCall() | **direction** (up or down), **originFloor** (int*) |
| addStop() | **originFloor** (int*) |
| holdCall() | **originFloor** (int*) |
| move()** | **direction** (up or down) |
| floorSelection() | **destinationFloor** (int*) |
| assessQueue() | |
| stop()** | |
| openDoors()** | |
| closeDoors()** | |
| | * *See note in **Assumptions*** |
| | * **Not defined below*
### Properties

| Name | Permissable Values |
| --- | --- |
| goingUp | Boolean |
| goingDown | Boolean |
| stopped | Boolean |
| currentFloor | (int*) |
| | * *See note in **Assumptions*** |

## External Inputs
- Call Button (Up)
- Call Button (Down)
- Floor Selection (int - see note in **Assumptions**)

## Global Variables
- **tripQueue** (ARRAY of permissable floor numbers - see note in **Assumptions**)
- **holdFloors** (ARRAY of calls to handle that are above a descending elevator or below an ascending elevator)

---

## Function *assessQueue()*
1. BEGIN
1. READ elevator.currentFloor
1. COMPARE elevator.currentFloor TO tripQueue
1. IF elevator.currentFloor IN tripQueue
1. CALL function elevator.stop()
1. CALL function elevator.doorsOpen()
1. WAIT for sensor to indicate doorway clear
1. CALL function elevator.doorsClose()
1. REMOVE elevator.currentFloor FROM tripQueue
1. IF tripQueue is empty
1. ADD floors from holdFloors
1. READ next floor from tripQueue
1. IF next floor in tripQueue > elevator.currentFloor
1. CALL function elevator.move(up)
1. ELSE IF next floor in tripQueue < elevator.currentFloor 
1. CALL function elevator.move(down)
1. ELSE 
1. CALL function elevator.stop()
1. CALL function assessQueue()
1. END

## Function *handleCall(direction, originFloor)*
1. BEGIN
1. READ elevator.currentFloor
1. IF ((elevator.currentFloor > originFloor) AND (elevator.goingDown) AND (direction == down)
1. OR
1. IF ((elevator.currentFloor < originFloor) AND (elevator.goingUp) AND (direction == up)
1. CALL function addStop(originFloor)
1. ELSE
1. CALL function holdCall(originFloor)
1. END

## Function *addStop(originFloor)*
1. BEGIN
1. ADD originFloor to **tripQueue**
1. END

## Function *holdCall(originFloor)*
1. BEGIN
1. ADD originFloor to **holdFloors**
1. END

## Function *floorSelection(destinationFloor)*
1. BEGIN
1. READ elevator.currentFloor
1. IF (destinationFloor > elevator.currentFloor) AND (elevator.goingUp)
1. OR
1. IF (destinationFloor < elevator.currentFloor) AND (elevator.goingDown)
1. ADD destinationFloor to **tripQueue**
1. END
