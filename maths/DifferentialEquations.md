==Definition==
'''Definition''': A differential equation is an equation that involves the function and its derivatives. Differential equations are used to model concepts that change proportionally to their own derivative(s).

There are a few different important classifications of a differential equation. Exclusive classifications are listed in the same section:
<br />


<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Order</div>
<div class="mw-collapsible-content">
The order of a differential equation correspond to the highest derivative of the dependent variable present in the equation. Sometimes, but not always, the lower the order of the differential equation, the easier it is to solve. The two most common versions of this classification are:
*; First order :  y = α•dy/dx
*; Second order :  d^2y/(dx)^2 = y
</div></div>

<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Linear or Nonlinear</div>
<div class="mw-collapsible-content">
*; Linear : A differential equation that can be written in a form where the function, or [[Variable|dependent variable]], is represented by as a linear combination of terms. Notably, the equation can be written in a general sense as:
*: <strong>TODO:: Get Image</strong> [[File:General_Linear_ODE.png]]
*: and as:
*: <strong>TODO:: Get Image</strong> [[File:General_Linear_PDE.png]]
<br />

*; Nonlinear : at least one derivative of the function is multiplied by another higher/lower derivative of the function.
</div></div>

<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Homogeneous or Nonhomogeneous</div>
<div class="mw-collapsible-content">
Annoyingly, there are two different types of classifications for homogeneous:
# When describing the [[Forcing Function|forcing function]]:
#; Homogeneous :  y' + y = f(x), f(x) is 0
#: e.g., y' + y = 0
#; Nonhomogeneous :  y' + y = f(x), f(x) is a nonzero constant or function
# When describing the dependent variable function
#; Homogeneous : A multiplicative scaling function. "If all arguments are multiplied by a factor, then its value is multiplied by some power of this factor." ([https://en.wikipedia.org/wiki/Homogeneous_function Wikipedia: "Homogeneous function"])
#; Nonhomogeneous : The absence of this behaviour. (<strong>TODO:: Elaborate?</strong>)
</div></div>

<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Ordinary or Partial</div>
<div class="mw-collapsible-content">
*; Ordinary : If the dependent variable is a function of a single independent variable. This property is denoted by the fact that all derivatives of the independent variable are [[Derivative|ordinary derivatives]].
*; Partial : If the dependent variable is a function of multiple independent variables. This property is denoted by the fact that all derivatives are [[Derivative|partial derivatives]].
</div></div>

<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Optional classifications:</div>
<div class="mw-collapsible-content">
*; Constant coefficients : All multiplicative terms associated with the dependent variable (and its derivatives) are constants.
</div></div>

==Ordinary Differential Equations==
===First Order===
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">[[First Order Linear Ordinary Differential Equation|First Order Linear]]</div>
<div class="mw-collapsible-content">
<strong>TODO:: Get Image</strong> [[File:FirstOrder_Linear_ODE.png]]

*Homogeneous (Forcing function is equal to 0)
** [[Separation of Variables]]
*Nonhomogeneous (Forcing function is not 0)
** [[Integrating Factor]]
</div></div>

<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">[[First Order Nonlinear Ordinary Differential Equation|First Order Nonlinear ]]</div>
<div class="mw-collapsible-content">
<strong>TODO:: Get Image</strong> [[File:FirstOrder_Nonlinear_ODE.png]]

* Special Forms:
** [[Bernoulli Equation Method]]
** [[Homogeneous (Function) Method]]
* Homogeneous (Forcing function is equal to 0)
** [[Separation of Variables]]
* Nonhomogeneous (Forcing function is not 0)
** [[Exact Equation Method]]
</div></div>

===Second Order===
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">[[Second Order Linear Ordinary Differential Equation|Second Order Linear]]</div>
<div class="mw-collapsible-content">
<strong>TODO:: Get Image</strong> [[File:SecondOrder_Linear_ODE.png]]

* Homogeneous (Forcing function is equal to 0)
*; with Constant Coefficients : [[Characteristic Polynomial, (Differential)|Characteristic Polynomial]]
*; without Constant Coefficients : [[Abel's Formula|Abel's Formula (Wronskian)]]
* Nonhomogeneous (Forcing function is not 0)
*; with Constant Coefficients : [[Undetermined Coefficients]]
*; without Constant Coefficients
*:* Special Form: [[Euler Equation, (Differential)|Euler Equation]]
*:* [[Variation of Parameters]]
* Other Methods
** [[Reduction of Order]]
** [[Series Solutions, (Differential)|Power Series Solutions]]
** [[Laplace Transforms]]
</div></div>

==Partial Differential Equations==
===First Order===
Do they exist?
===Second Order===
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">[[Second Order Linear Partial Differential Equation|Second Order Linear]]</div>
<div class="mw-collapsible-content">
<strong>TODO:: Get Image</strong> [[File:SecondOrder_Linear_PDE.png]]

<strong>TODO::Verify</strong>
* Homogeneous (Forcing function is equal to 0)
*; with Constant Coefficients : [[Characteristic Polynomial, (Differential)|Characteristic Polynomial]]
*; without Constant Coefficients : [[Abel's Formula|Abel's Formula (Wronskian)]]
* Nonhomogeneous (Forcing function is not 0)
*; with Constant Coefficients : [[Undetermined Coefficients]]
*; without Constant Coefficients
*:* [[Variation of Parameters]]
* Other Methods
** [[Reduction of Order]]
** [[Series Solutions, (Differential)|Power Series Solutions]]
** [[Fourier Transforms]]
</div></div>
