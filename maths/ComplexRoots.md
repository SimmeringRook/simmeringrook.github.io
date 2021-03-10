# Complex Roots

## General Example
### Step 1:
Write the complex number in exponential form:


$$
  z = r\cdot exp^{i (\theta + 2\pi n)}
$$

where $n$ is an integer.

### Step 2:
Take the $m$-th root, $m\neq n$:
$$
\begin{aligned}
  z^{1/m} &= \sqrt[m]{r\cdot exp^{i (\theta + 2\pi n)} } \\
          &= r^{1/m} \cdot exp\left(i \frac{\theta + 2\pi n}{m} \right)
\end{aligned}
$$
Consider all the values for: $n = 0, ..., m-1$

### Sanity check:
"The roots of the product are the product of the roots"

## Example
  Find the cube roots of z when z = 1

### Step 1:]
Write ''z'' in exponential form:

  z = r*exp(i (\theta+2\pi*n) )

Then find the cube roots of z:

  z = 1*exp(i(0+2\pi*n))<br>
  = 1^(1/3)<br>
  = [1*exp(i(0+2\pi*n))]^(1/3)<br>

### Step 2:
For 0 <= n < m; m = 3

#### n=0:

  z^(1/3)<br>
  = exp(i*0/3)<br>
  = 1

#### n=1:

  z^(1/3) <br>
  = exp(i*2\pi/3)<br>
  = cos(2\pi/3)+isin(2\pi/3)<br>
  = -1/2 + i\sqrt(3)/2

#### n=2:
  z^(1/3)<br>
  = exp(i*4\pi/3)<br>
  = cos(4\pi/3)+isin(4\pi/3)<br>
  = -1/2 - i\sqrt(3)/2<br>

### Sanity check:
$$
  z = 1*(-1/2 + i\sqrt(3)/2)*(-1/2 - i\sqrt(3)/2) = 1
$$
