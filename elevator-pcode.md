# Elevator Pseudocode
### by Roger Mullins, Team DaVinci

---

## Assumptions
- The elevator object is in working order and maintained such that it is able to perform the functions below
- There is a steady power supply
- **Floor numbers** (int values passed to and used by functions and properties) are encoded by the push buttons so that numbers outside the permitted range cannot be entered
- The elevator can determine its current position by accessing an automatic counter that increments as it ascends and decrements as it goes down

## Elevator Object
### Functions

| Name | Parameter(s) |
| --- | --- |
| handleCall() | **direction** (up or down), **originFloor** (int*) |
| addStop() | **originFloor** (int*)
| move() | **direction** (up or down) |
| floorSelection() | **destinationFloor** (int*) |
| openDoors() | |
| closeDoors() | |
| | * *See note in **Assumptions*** |

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