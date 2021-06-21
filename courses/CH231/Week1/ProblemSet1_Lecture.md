# Week 1 Day 1: Lecture, Problem Set 1

<br />

# Question 1: Unit Conversions

Do the conversions below. In each case, before beginning the calculation, estimate the size of your expected answer.

## Part A

?> $16.3 km$ to $nm$

Estimate: Bigger, $nm$ is smaller than $km$, so the value in these units will be bigger.

$$\begin{aligned}
1 km = 10^3 m, &\quad 1 m = 10^{9} nm\\
\\
16.3 km &= 16.3\times 10^{12} nm = 1.63 \times 10^{13} nm
\end{aligned}$$

<br />

## Part B

?> $5.3\times 10^5 nm$ to $mm$

Estimate: Smaller, $nm$ is smaller than $mm$, so the value in these units will be smaller.

$$\begin{aligned}
1 nm = 10^{-9} m, &\quad 1 m = 10^{-3} mm\\
\\
5.3\times 10^5 nm &= 5.3\times 10^{-1} mm
\end{aligned}$$

<br />

## Part C

?> $6.94\times 10^{-4} cg$ to $kg$

Estimate: Smaller, $cg$ is smaller than $kg$.

$$\begin{aligned}
1 cg = 10^{-2} g, &\quad 1 kg = 10^{3} g\\
\\
6.94\times 10^{-4} cg &= 6.94\times 10^{-9} kg
\end{aligned}$$

<br />

## Part D

?> $0.56 dg/cm^3$ to $kg/m^3$

Estimate: Bigger, $cm^3\rightarrow m^3$ is much smaller than $dg\rightarrow kg$.

$$\begin{aligned}
1 dg = 10^{-4} kg, &\quad 1 cm^3 = 10^{-6} m^3\\
\\
0.56 \frac{dg}{cm^3} &= 0.56 \frac{dg}{cm^3} \frac{10^{-4} kg}{dg}\frac{1 cm^3}{10^{-6} m^3} \\
&= 0.56 \frac{10^{6} kg}{10^4 m^3}\\
&= 5.6 \times 10 \frac{kg}{m^3}
\end{aligned}$$

<br />

<hr>

# Question 2: Significant Figures in Calculations

Perform the mathematical operations shown below.

## Part A

$$\begin{aligned}
(9.61\times 10^{-3})(2.53\times 10^{-2}) &= (9.61\cdot 2.53)\times 10^{-5}\\
&= 24.3133 \times 10^{-5}\\
&= 2.43 \times 10^{-6}
\end{aligned}$$

<br />

## Part B

$$\begin{aligned}
\frac{3.65}{2.00\times10^{-3}} &= \frac{3.65}{2.00}\times 10^{3}\\
&= 1.825 \times 10^{3}\\
&= 1.83 \times 10^{3}
\end{aligned}$$

<br />

<hr>

# Question 3: Density

Answer the following questions regarding density.

## Part A

?> The density of water is $1.0 g/mL$ at room temperature. What is the density of room temperature water in units of $kg/dL$? Do you expect your answer to be greater than or less than $1.0$? Explain your prediction and then solve the problem.

The density of room temperature water in units of $kg/dL$ should be smaller than $1.0$, as the difference between $1\ g\rightarrow 1\ kg$ is bigger than the difference of $1\ mL\rightarrow 1\ dL$.

$$\begin{aligned}
\frac{1.0\ g}{mL}\cdot\frac{10^{-3}\ kg}{g}\cdot\frac{ mL}{10^{-2}\ dL} &= 1.0\frac{10^2\ kg}{10^3\ dL}\\
&= 1.0 \times 10^{-1} \frac{kg}{dL}
\end{aligned}$$

<br />

## Part B

?> The density of water can also be expressed in cubic units: $1.0\ g/cm^3$. What would it be in units of $g/m^3$? Do you expect that the answer would be greater than or less than $1.0$? Explain your prediction and then solve the problem.

This time, we are keeping the units of mass constant and only changing the units of volume. $1\ cm^3$ corresponds to $10^{-6}\ m^3$, so numeric value for the density in terms of $g/m^3$ will be greater than the numeric value for the density in $g/cm^3$:

$$\begin{aligned}
\frac{1.0\ g}{cm^3}\cdot\frac{cm^3}{10^{-6}\ m^3} &= 1.0\times 10^6\frac{g}{m^3}
\end{aligned}$$

<br />

## Part C

?> Two common student answers to Part B are: $1.0\times 10^6\ g/m^3$ and $100\ g/m^3$. Which of these two answers is correct? What error was made by the student who gave the wrong answer?

The first student is correct. The mistake the second student made was incorrectly using the ratio of $1\ cm = 10^{-2}\ m$. They did not realize that they needed this conversion factor three times, in order to complete convert from $cm^3$ to $m^3$.

What they really have, from dimensional analysis, is:

$$\begin{aligned}
\frac{1.0\ g}{cm^3}\cdot\frac{cm}{10^{-2}\ m} &= 1.0\times 10^2 \frac{g}{cm^2\ m}
\end{aligned}$$

<br />

<hr>

# Question 4: Volume from Density

?> The density of liquid mercury $(Hg)$ is $13.5\ g/mL^3$. What is the volume of a sample of liquid mercury that weighs $3.8\ g$?

$$\text{density} = \frac{\text{mass}}{\text{Volume}}\Rightarrow V=\frac{m}{\rho}$$

$$\begin{aligned}
V &= \frac{m}{\rho}\\
&= \frac{3.8\ g}{1}\cdot\frac{1\ mL}{13.5\ g}\\
&= 0.2\overline{814}\ mL\\
&= 2.8 \times 10^{-1}\ mL
\end{aligned}$$
