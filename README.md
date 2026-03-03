# push_swap

Sort a stack of integers using the minimum number of operations. Two stacks, eleven operations, and an algorithm that actually has to be good — the checker doesn't lie.

## Quick Start

```bash
make
./push_swap 4 67 3 87 23
```

```bash
# validate with the checker
ARG="4 67 3 87 23"
./push_swap $ARG | ./checker $ARG
```

## How it works

For 2–3 numbers: hardcoded optimal sequences.

For larger inputs: a position-based algorithm. Each element in stack `a` is assigned a cost — how many rotations of `a` and `b` it takes to move it to the right position. The element with the lowest total cost is moved on every round. Stack `b` accumulates elements in descending order; they're pushed back to `a` at the end.

Before any move, the total cost — rotations in both stacks — is computed for every element. The cheapest one goes first. No move is ever spent correcting a bad previous decision.

**Target operation counts:**

- 100 numbers: under 700 operations
- 500 numbers: under 5500 operations

## Operations

| Operation         | Effect                                           |
| :---------------- | :----------------------------------------------- |
| `sa` `sb` `ss`    | Swap the top two elements of stack a, b, or both |
| `pa` `pb`         | Push the top of one stack onto the other         |
| `ra` `rb` `rr`    | Rotate upward (top element goes to bottom)       |
| `rra` `rrb` `rrr` | Rotate downward (bottom element goes to top)     |

## Edge cases

Duplicate values are rejected. Non-integer and out-of-range inputs print an error and exit.

## Project structure

```
├── includes/     — header files
├── libft/        — libft submodule
└── srcs/         — stack operations, cost algorithm, input parsing, utils
```
