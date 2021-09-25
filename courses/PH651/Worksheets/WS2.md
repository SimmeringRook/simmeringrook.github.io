---
title: Worksheet 2
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Friday, September 24, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[LO,LE]{Knudson}
---

# Question 1

> You are an experimentalist in nanoscience who studies nanometer-size features. You have two microscopes: one is an optical microscope, in which you illuminate your sample with visible light ($\lambda$ ~ 400 nm), another one is an electron microscope, in which you bombard your sample with electrons accelerated to energies of 10 keV. Estimate how many orders of magnitude you (in theory) can gain in the resolution of your experiment by choosing the electron microscope over the optical one if the resolution is diffraction limited (i.e. limited by the wavelength). (In practice, electron microscope resolution is limited by aberrations of the electron optics, which reduces the resolution.) $$\ $$

Using the de Brogile wavelength formula, we can find the wavelength of an electron (assuming rest mass):

$$\lambda = \frac{h}{m\cdot v}$$

To find the speed of the electron, we can manipulate its energy and solve for speed and then substitute that expression back into the de Brogile equation.

$$\begin{aligned}
E &= \frac{m_{e^-}\cdot v^2}{2}\\
v &= \sqrt{\frac{2E}{m_{e^-}}}
\end{aligned}
\qquad\qquad\qquad
\begin{aligned}
\lambda_{e^-} &= \frac{h}{m_{e^-}\cdot v}\\
&= \frac{h}{m_{e^-}}\sqrt{\frac{m_{e^-}}{2E}}\\
&= \frac{h}{\sqrt{m_{e^-}2E}}
\end{aligned}$$

Finally, we calculate the wavelength by substituting in the values for Plank's constant ($h=6.63\times 10^{-34}\ J\cdot s$), the energy of the Electron ($E=10\ keV= 1.6\times 10^{-15}\ J$), and the (rest) mass the of Electron ($m_{e^-}=9.1\times 10^{-31}\ kg$)

$$\begin{aligned}
\lambda_{e^-} &= \frac{h}{\sqrt{m_{e^-}2E}}\\
&= \frac{6.63\times 10^{-34}\ J\cdot s}{\sqrt{(9.1\times 10^{-31}\ kg)\cdot 2(1.6\times 10^{-15}\ J)}}\\
&= 1.2\times 10^{-11}\ m = 12\ pm
\end{aligned}$$

Therefore, in theory, an electron microscope would give us four orders of magnitude in resolution over an optical microscope:

$$\underbrace{\lambda_{light} \rightarrow 10^{-7}\ m}_{\text{optical microscope}} \qquad\text{versus}\qquad \underbrace{\lambda_{e^-} \rightarrow 10^{-11}\ m}_{\text{electron microscope}}$$

### Sense Making, Dimensional Analysis:

$$\begin{aligned}
\lambda_{e^-} &[=] \frac{J\cdot s}{\sqrt{kg\cdot J}} \\
&= \frac{\frac{kg\cdot m^2}{s^2}\cdot s}{\sqrt{kg\cdot \frac{kg\cdot m^2}{s^2}}}\\
&= \frac{kg\cdot m^2}{s}\cdot \frac{s}{kg\cdot m}\\
&=\ m
\end{aligned}$$
