## Message

How can we measure things not in our frame?


## Background

$$ds^2 = -f(r)^2 dt^2 + \frac{dr^2}{f(r)^2}$$

The metric gives us a way to measure distance on a line element.

In special relativity, this is easier as the line element looks something more like $$ds^2 = -dt^2 + dx^2$$ and we know that there exists a rest frame for each event. If using $ds$ is too messy, we can just shift to a different frame and then find the correction factor for our measurements ($\gamma$ -> time dilation, length contraction). We can broadly classify reference frames under two categories: belongs to the object in question (relative velocity = 0) or some observer (relative velocity is non-zero).

In general relativity, we have three families:

1. the Object in question
2. the Bookkeeper (global/universal observer)
3. Shell observers (constant $r$ or $t$ coordinates)

The line element works very well for answering what each frame measures but with the important caveat: the measurement must be done in their frame.

## The Problem

> What is the speed of a free-falling object?

We have three very distinct and different answers:

1. The object is in free-fall, so it has no acceleration. Therefore the object measures a speed of $0$ for all values of $r$: it is the BH that approaches them at increasing speed.
2. The bookkeeper derives $v(r)=-\sqrt{1-\frac{2M}{r}}\sqrt{\frac{2M}{r}}$, the object is at rest out at infinity or when it tries to approach the horizon!
3. A shell observer can only measure the speed as the object enters its shell. The process is the same as the BK but obtains a different equation: $v(r_{shell})=-\sqrt{\frac{2M}{r_{shell}}}$.

Sure this is weird, but where's the problem? What if we wanted to record the object's path as observed from a couple observers? $v(r_{shell})$ only describes what $r_{shell}$ measures at $r_{shell}$. This is the problem. We cannot change our basis to answer this question: doing so only gives us the answer of what a different shell observer would measure as the object enters their shell; but we already know that!

## Progress & the Answer

So what do we do?

The sneakiness lies in how we measure everything: light. We strap a lightblub to the object falling in and record what we see. That is, we combine the effects of doppler and gravitational redshifting:

$$\lambda_{measured} = (z+1)\zeta\lambda_{emitted}$$

Some algebra later, we have speed as a function of four variables: $$v(\lambda_{m},\lambda_{e},r_e,r_m) = -c \frac{\frac{\lambda_e}{\lambda_m}\sqrt{\frac{1-\frac{2M}{r_e}}{1-\frac{2M}{r_M}}}-1}{\frac{\lambda_e}{\lambda_m}\sqrt{\frac{1-\frac{2M}{r_e}}{1-\frac{2M}{r_M}}}+1}$$

