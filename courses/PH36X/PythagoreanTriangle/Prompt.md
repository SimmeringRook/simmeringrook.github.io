## Prompt

You want to build a triangle using squares comprised of tiles. Each tile is identical in size but comes in two colors. You must use the same number of each colored tile when constructing the triangle with the goal of creating a triangle whose perimeter is 1000 tiles.

## Given

### Constraint 1

First, let us consider that equal amounts of colored tiles must be used in the final construction and for simplicity, let each of three squares only consist of one color.

$$\text{# of Color 1} = \text{# of Color 2}$$

There must be at least one square on each side of the equality otherwise the constraint is violated. From there, we can see that the third square is either on the left or right, and that the particular construction doesn't matter.

$$\left(\Box_1 + \Box_2 = \Box_3\right) \leftrightarrow \left(\Box_1 = \Box_2 + \Box_3\right)$$

The simplest representation for the number of tiles used in each square is just each square's area.

$$\Box = (\text{side length})^2 $$

And so the mathematical representation for the first constraint is just the sum of the areas of two squares must equal the area of the third, or more commonly, the Pythagorean Theorem:

$$a^2 + b^2 = c^2$$

### Constraint 2

Since we have chosen the names of $a$, $b$, and $c$, for each square, we can then express the second constraint without much work. The sum of the side lengths from each square must equal the given value of the perimeter:

$$a+b+c=1000$$

### Constraint 3

Since each tile is identical in size and shape (as square tiles), the number of tiles for each color (and in total) must be whole numbers (excluding $0$ for obvious reasons).

$$a,b,c \in \mathbb{N}$$
