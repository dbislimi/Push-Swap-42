# push_swap

Sort a stack of integers using a limited set of operations on two stacks. The goal is to minimize the total number of operations.

## Build

```bash
make
./push_swap 4 67 3 87 23
```

Validate:

```bash
ARG="4 67 3 87 23"
./push_swap $ARG | ./checker $ARG
```

## Algorithm

For 2-3 elements, hardcoded sequences.

For larger inputs, I use a cost-based approach: each element in stack A is evaluated by how many rotations of A and B it would take to insert it at the right position in B. The cheapest element gets moved first. Stack B stays in descending order, then everything is pushed back to A at the end.

Results:

- 100 numbers: < 700 operations
- 500 numbers: < 5500 operations

## Operations

| Op                | What it does                           |
| :---------------- | :------------------------------------- |
| `sa` `sb` `ss`    | Swap top two elements of a, b, or both |
| `pa` `pb`         | Push top of one stack onto the other   |
| `ra` `rb` `rr`    | Rotate up (top goes to bottom)         |
| `rra` `rrb` `rrr` | Rotate down (bottom goes to top)       |

Duplicates, non-integer inputs, and overflow are rejected with an error.

## Structure

```
includes/     - headers
libft/        - libft submodule
srcs/         - stack ops, cost computation, input parsing, utils
```
