# Lab 9
## Invariants:
### Provided Invariants:
These are invariants that are given to us in the description
1. The alarm begins clanging. After 10 seconds, the barrier lowers.
2. The alarm continues to sound and the barrier remains lowered while a train is present.
3. When no train is present the barrier raises.
4. After 10 seconds the alarm stops.
5. "An approach signal will always precede a depart signal"
6. "The power will never be interrupted"
7. "Trains on each track only run in one direction."


### Our invariants:
8. If a train approaches in one direction and another from the other direction then there are two trains in the system, and the barriers must stay closed until the last train leaves
9. Barriers are only raised if the train count is 0
10. Barriers are lowered otherwise
11. We assume the alarm is enough to warn pedestrians

## Varying Invariants:
- This system does not account for two trains in the system because if one train leaves, then that triggers the raise state even though another train could still be approaching and in the system


## Prove It:
| number | arms_down | alarm_on | northbound_present | southbound_present | north_approach | south_approach | north_depart | south_depart | ringing | safety_hazard |
|--------|-----------|----------|--------------------|--------------------|----------------|----------------|--------------|--------------|---------|---------------|
| 0      | 0         | 0        | 0                  | 0                  | 6              | 5              | 0            | 0            |         |               |
| 1      | 0         | 0        | 0                  | 1                  |                |                |              |              |         | 2             |
| 2      | 0         | 0        | 1                  | 0                  |                |                |              |              |         | 2             |
| 3      | 0         | 0        | 1                  | 1                  |                |                |              |              |         | 2             |
| 4      | 0         | 1        | 0                  | 0                  | 6              | 5              | x            | x            | 10s\0   |               |
| 5      | 0         | 1        | 0                  | 1                  | 7              | 5              | x            | tc=0? 4 : 5  | 10s\13  |               |
| 6      | 0         | 1        | 1                  | 0                  | 6              | 7              | tc=0? 4 : 6  | x            | 10s\14  |               |
| 7      | 0         | 1        | 1                  | 1                  | 7              | 7              | tc>0? 7 : 5  | tc>0? 7 : 6  | 10s\15  |               |
| 8      | 1         | 0        | 0                  | 0                  |                |                |              |              |         | 2             |
| 9      | 1         | 0        | 0                  | 1                  |                |                |              |              |         | 2             |
| 10     | 1         | 0        | 1                  | 0                  |                |                |              |              |         | 2             |
| 11     | 1         | 0        | 1                  | 1                  |                |                |              |              |         | 2             |
| 12     | 1         | 1        | 0                  | 0                  |                |                |              |              |         | 2             |
| 13     | 1         | 1        | 0                  | 1                  |                |                |              |              |         | 2             |
| 14     | 1         | 1        | 1                  | 0                  |                |                |              |              |         | 2             |
| 15     | 1         | 1        | 1                  | 1                  |                |                |              |              |         | 2             |

| number | invariant |
|--------|-----------|
| 16     |           |
