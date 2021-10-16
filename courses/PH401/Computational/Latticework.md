# Latticework

The `Latticework` object is a collection of [`Nodes`](/courses/PH401/Computational/Node.md) of [spacetime](/courses/PH401/Physics/Spacetime.md). The name is inspired from [Taylor and Wheeler]'s discussion of a "latticework of rods and clocks" used to map out and record events in spacetime. Functionally, this will be implemented as a [multi-dimensional array] of `Nodes`, and will be aware of the underlying geometry of spacetime implemented.

## Creation

This object will be created at the start of runtime and accept parameters dictating the overall number of Nodes available for subsequent simulations and calculations.

## Functions and Methods

Since the `Latticework` is aware of the underlying geometry of spacetime, it will contain the methods to convert from a [geometric] to a [physical] representation of the region.
