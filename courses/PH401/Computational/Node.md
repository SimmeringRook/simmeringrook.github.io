# Node

The `Node` object is a essentially the manifestation of an intersection of gridlines on 2 Dimensional graph paper.

## Creation

This object will be created with the Latticework and will be given the corresponding coordinates at this time. In a very raw sense, this object will know its $x$, $y$, and $z$ position with respect the [`Latticework`](/courses/PH401/Computational/Latticework.md), but unaware of its position with respect the geometry of spacetime.

## Functions and Methods

Possible useful functions to be able to ask a `Node`:

### GetCoordinatesInLatticework

If for whatever reason we're addressing a `Node` saved or passed by reference, it'll be pretty useful to be able to ask for a [tuple](https://www.w3schools.com/python/python_tuples.asp) that contains the $x$, $y$, and $z$ position in the `Latticework`, e.g.:

```python
def GetCoordinatesInLatticework():
  return (self.latticeX, self.latticeY, self.latticeZ, self.latticeT)
```

### ListOfLocalNeighbors

Since we have the `Node.GetCoordinatesInLatticework()` functionality, the `Latticework` could pass down a collection of nearest neighbors as determined by the geometry of the spacetime. In general, this should be equivalent to the collection of geometric neighbors.

```python

def SetListOfLocalNeighbors(localNeighbors):
  self.localNeighbors = localNeighbors

def GetListOfLocalNeighbors():
  return self.localNeighbors.copy()
```
