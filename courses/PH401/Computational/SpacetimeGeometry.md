# Spacetime Geometry

### Object Description

The is the base class or interface that will skeleton out the contract for how the [`Latticework`] interacts with and responds to the geometry of spacetime. This will define the function signatures for a series of "mathematical helper functions".

### Physical Description

"Spacetime" is just a shorthand for denoting the addition of time to the dimensions considered when talking about distances. Inherently, we must measure distance differently in the context of spacetime than we would in 1, 2, or 3 dimensions of space. Distance in this more common sense is typically done through the Pythagorean Theorem (also known as a Euclidean distance measurement), whereas, distance in spacetime is measured using Non-Euclidean geometry.

The mathematical object that informs us how to measure distance in our new geometric framework is called the [Metric](/courses/PH401/Physics/Metric.md).

## Functions and Methods

### Metric

We will either need to retrieve the functional form of the [Metric](/courses/PH401/Physics/Metric.md) or pass in a set of parameters for the Metric to act on. The simplest manifestation of this is taking the inner product between $d\vec{r}$ and itself to give the line element of the space (or restricted region in the space). For simplicity, we will assume orthogonal coordinate systems for now:

$$d\vec{r} \cdot d\vec{r} = g(\sigma^i \hat{e}_i , \sigma^j \hat{e}_j ) = ds^2$$

In 2-dimensional Euclidean space, $d\vec{r} = dx \hat{x} + dy\hat{y}$, and the line element is given:

$$\begin{aligned}
d\vec{r} \cdot d\vec{r} &= g(\sigma^i \hat{e}_i , \sigma^j \hat{e}_j ) \\
&= g(dx\hat{x} + dy\hat{y}, dx\hat{x} + dy\hat{y})\\
&= g(dx,dx)g(\hat{x},\hat{x}) + g(dy,dy)g(\hat{y},\hat{y}) \\
&= dx^2 + dy^2
&= ds^2
\end{aligned}$$

```Python
def Metric(pForm1, pForm2):
  return (self.latticeX, self.latticeY, self.latticeZ, self.latticeT)
```

### GetLineElementOf

Most likely, we will want to use the Metric to describe the distance between two [`Nodes`](/courses/PH401/Computational/Node.md):

```Python
def GetLineElementOf(drVector1):
  return self.Metric(drVector1, drVector1)
```


## Geometric vs Physical Coordinates
