# Sprint 3: Pseudocode
### Roger Mullins, Team DaVinci

The file [pseudocode.md](pseudocode.md) contains pseudocode describing an object (an elevator) and its associated properties and functions. Basic operations are also addressed. In general:

- The elevator won't stop for a user call that is in the opposite direction the elevator is currently traveling. Rather, that call is added to a queue for when the elevator changes direction.
- A rider cannot select a floor that is in the opposite direction the elevator is currently traveling.
- A recursive function (assessQueue()) continually monitors the elevator's current position and upcoming stops, if any, and if there are none reverses the elevator and adds in the stops that have been queued.
