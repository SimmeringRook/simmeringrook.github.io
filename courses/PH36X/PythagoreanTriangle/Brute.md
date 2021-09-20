## Brute Force

The simplest construction for a computational answer is to iterate over the possible values of $a$, $b$, and $c$, and check each case against the constraints.

```
Python
solution = False
for c in range(1, 1000):
  for b in range(1, 1000):
    for a in range(1, 1000):
      solution = (a+b+c == 1000) and (pow(a,2) + pow(b,2) == pow(c,2))
      if solution:
        break
if solution:
  print(a,b,c)
else:
  print("No solution")
```

This is by far not an elegant solution to the prompt, but it will work. Without considering other cases of simplifications, we can apply at least some general optimizations. While $c=b=a=1000$ is not a valid solution (the perimeter would be 3 times longer than the constraint), if there does not exist a solution for the given constraints, the program will have checked ${10^3}^3$ combinations of integer values.

## Optimized Brute, Part 1

In general, we just want to avoid running $10^9$ comparisons. Leveraging basic geometric knowledge we know that the hypotenuse of a triangle is the side with the greatest length, therefore we can optimize each loop to stop at or equal to $c$. This still allows perimeter lengths that are greater than $1000$, so instead of just changing the range for $b$ and $a$ from $[1,c)$, we should change the ending interval to be the total goal perimeter minus each chosen side length, that is:

$$b\in[1,1000-c) \qquad a \in [1,1000-c-b+1)$$

```
Python
solution = False
for c in range(1, 1000):
  for b in range(1, 1000-c):
    for a in range(1, 1000-c-b+1):
      solution = (a+b+c == 1000) and (pow(a,2) + pow(b,2) == pow(c,2))
      if solution:
        break
if solution:
  print(a,b,c)
else:
  print("No solution")
```

However, just changing the intervals for each `for` loop doesn't enforce the geometric concept we discussed above. If $c$ is the hypotenuse and is the longest side: $a,b<c$. The above code immediately allows for $b$ to be an integer value greater than $c$. We can fix this with two steps:

1. Reverse the `for` loop direction for $c$.
2. Find the smallest possible value for $c$.

The first step is very easy and ultimately needs a little inspiration from the second step: $c=1000$ would only produce a solution that satisfies the perimeter constraint if $a=b=0$, but that's not a triangle. At most (worst?), $c=997$, such that $a$ and $b$ are at least $1$, producing a geometric shape that *satisfies* the prompt.

```
Python
for c in range(998, 1, -1):
```

The second step then is a logical continuation from above: what is the smallest value of $c$ with $a$ and $b$ such that we're able to create a triangle with a $1000$ tile long perimeter? $c=334$ Recalling that $a,b,c$ must be integer values, dividing $1000$ by $3$ gives $333\ 1/3$. If $a=b=c=333$, we have a total length of $999$, so choose our hypotenuse to be 1 tile longer.

$$c\in(333,998]$$

```
Python
for c in range(998, 333, -1):
  for b in range(1, 1000-c):
    for a in range(1, 1000-c-b+1):
```

In the worst case scenario, where there is no solution or the final combination checked is the solution $c=334$, $a=b=333$, only $49\times 10^6$ comparisons must be made. That's not too bad: just by leveraging a little geometric intuition, we've cut the number of comparisons in half.

## Simplification

Using some geometric intuition, we can reduce the range of possible values for the hypotenuse to reduce the amount of iterations and comparisons required to find if a solution exists and its value.

### Case 1

First, we can begin by considering the smallest possible value for the side lengths for this triangle. Since $c$ is the hypotenuse, in all triangles other than an equilateral triangle, the hypotenuse is defined as the longest side length; therefore, $c$ is will be at its minimum value if the triangle is equilateral.

Consider that $a=b=c$ and substitute this relation into constraint 2:

$$\begin{aligned}
a+b+c &= 1000 \\
3c &= 1000 \\
c &= \frac{1000}{3}
\end{aligned}$$

From this, we see that there is not solution for an equilateral triangle with integer lengths as $333.\bar{3}\notin\mathbb{N}$.

$$\therefore c \in (333,998]$$

This simplification of the interval can also be approached from the first constraint by noting that there is no non-zero integer value that satisfies the first constraint when $a=b=c$. While useful in determining that an equilateral triangle cannot be a solution to the Pythagorean Theorem, at first glance, it may not lead to the more computationally useful insight on the limiting value of $c$.

### Case 2

The other typical type of triangle that is nice an easy to work with is an isosceles triangle. This type of triangle notes that two side lengths (and their corresponding angles) are equal in value. We can use constraint 1 to see if this type of triangle would satisfy part of the prompt by assuming $a=b$.

$$\begin{aligned}
a^2 + b^2 &= c^2 \\
2b^2 &= c^2\\
b = \frac{c}{\sqrt{2}}, &\quad c = b\sqrt{2}
\end{aligned}$$

From this, we can see that there does not exist an integer solution as $c$ being a multiple of $\sqrt{2}$ makes $c$ irrational and irrational numbers $\notin\mathbb{N}$. We can, again, use the second constraint to reduce the interval of $b$ and improve the computational time for determining a solution. If $a=b$, then with constraint 2:

$$\begin{aligned}
a+b+c &= 1000 \\
2b+c &= 1000 \\
b &= \frac{1000-c}{2}
\end{aligned}$$

Considering the results from both constraints, we arrive that the strict relation is enforced:

$$a < b < c$$

And that to avoid comparing values of $a=b$ that are clearly not solutions, we have that $b$ is bounded above by $1000 - c$ (exclusively) and below by $1/2\times(1000-c)$:

$$0 < a < (\frac{1000-c}{2} < b < 1000 - c) < (333 < c < 998)$$

## Optimized Brute, Part 2

Using the results of the simplifications provided from Case 1 and Case 2, summarized below:

$$0 < a < (\frac{1000-c}{2} < b < 1000 - c) < (333 < c < 998)$$

The `for` loops can be refined to reflect these intervals:

```
Python
for c in range(998, 333, -1):
  bLimit = int((1000-c)/2)
  for b in range(1000-c, bLimit, -1):
    for a in range(1, 1000-c-b+1):
```

And this further reduces the total number of comparisons in the worst case (complete iteration of all loops) by a factor of 4: $12\times 10^6$ (or 82 times from the original $10^9$). Expressed slightly differently: this script, *in its worst case scenario*, now only has to do $1.22%$ of the original $1\ billion$ comparisons.
