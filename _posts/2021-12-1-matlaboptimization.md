---
title: 'matlab optimization'
date: 2021-12-01
permalink: /posts/2021/12/matlaboptimization/
tags:
  - optimization
  - matlab
---

use [optimization Toolbox](https://www.mathworks.com/help/optim/index.html) in matlab to solve linear, quadratic, conic, integer, and nonlinear optimization problems:  [Tutorial for Optimization Toolbox™](https://www.mathworks.com/help/optim/ug/optimization-toolbox-tutorial.html)



# [fminunc](https://www.mathworks.com/help/optim/ug/fminunc.html)

Find minimum of unconstrained multivariable function

Finds the minimum of a problem specified by 
$$
\min _{x} f(x)
$$
where *f*(*x*) is a function that returns a scalar, *x* is a vector or a matrix; see [Matrix Arguments](https://www.mathworks.com/help/optim/ug/matrix-arguments.html).

- we try to solve a problem of `J(θ) =  (θ1 - 5)^2 + (θ2 - 5)^2` in gradient decent:

```matlab
% write a single function to compute the cost.
function [f, g] = costFunction(theta)
	f = sum((theta - 5).^2);	% cost
	g = 2*(theta - 5);			% gradient
end

% set options
options = optimoptions('fminunc','Algorithm','trust-region','SpecifyObjectiveGradient',true);

% use 
theta0 = zeros(2,1);  
x = fminunc(@costFunction,theta0,options)
```

> output

```
Local minimum found.
Optimization completed because the size of the gradient is less than
the value of the optimality tolerance.

x =
     5
     5
```



# [lsqnonlin](https://www.mathworks.com/help/optim/ug/lsqnonlin.html)

Solve **nonlinear least-squares** (nonlinear **data-fitting**) problems

- **Description**

Nonlinear least-squares solver

Solves nonlinear least-squares curve fitting problems of the form
$$
\min _{x}\|f(x)\|_{2}^{2}=\min _{x}\left(f_{1}(x)^{2}+f_{2}(x)^{2}+\ldots+f_{n}(x)^{2}\right)
$$
with optional lower and upper bounds *lb* and *ub* on the components of *x*.

*x*, *lb*, and *ub* can be vectors or matrices; see [Matrix Arguments](https://www.mathworks.com/help/optim/ug/matrix-arguments.html).

Rather than compute the value ||*f*(*x*)||^2_2 (the sum of squares), `lsqnonlin` requires the user-defined function to compute the *vector*-valued function
$$
f(x)=\left[\begin{array}{c}
f_{1}(x) \\
f_{2}(x) \\
\vdots \\
f_{n}(x)
\end{array}\right]
$$
`x = lsqnonlin(fun,x0)` starts at the point `x0` and finds a minimum of the sum of squares of the functions described in `fun`. The function `fun` should return a vector (or array) of values and not the sum of squares of the values. (The algorithm implicitly computes the sum of squares of the components of `fun(x)`.)

```matlab
xdata = [0.9 1.5 13.8 19.8 24.1 28.2 35.2 60.3 74.6 81.3];
ydata = [455.2 428.6 124.1 67.3 43.2 28.1 13.1 -0.4 -1.3 -1.5];

fun = @(x)x(1)*exp(x(2)*xdata)-ydata;
x0 = [100,-1];
options = optimoptions(@lsqnonlin,'Algorithm','trust-region-reflective');
x = lsqnonlin(fun,x0,[],[],options)
```

>output:

```
Local minimum possible.
lsqnonlin stopped because the final change in the sum of squares relative to 
its initial value is less than the value of the function tolerance.
x = 1×2
  498.8309   -0.1013
```



