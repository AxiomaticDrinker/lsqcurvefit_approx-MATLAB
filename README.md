# `lsqcurvefit_approx` [![View Approximate Least Squares Curve Fitting (lsqcurvefit_approx) on File Exchange](https://www.mathworks.com/matlabcentral/images/matlab-file-exchange.svg)](https://www.mathworks.com/matlabcentral/fileexchange/93710-approximate-least-squares-curve-fitting-lsqcurvefit_approx)

Fits linear and polynomial models to data using linear least squares and approximates nonlinear models through linearization.


## Syntax

`[c,r2,eqn] = lsqcurvefit_approx(x,y)`\
`[c,r2,eqn] = lsqcurvefit_approx(x,y,'linear')`\
`[c,r2,eqn] = lsqcurvefit_approx(x,y,'poly',n)`\
`[c,r2,eqn] = lsqcurvefit_approx(x,y,'power')`\
`[c,r2,eqn] = lsqcurvefit_approx(x,y,'exp')`\
`[c,r2,eqn] = lsqcurvefit_approx(x,y,'log')`

## Description

`[c,r2,eqn] = lsqcurvefit_approx(x,y)` returns the model coefficient vector `c = [m,b]` for the linear fit <img src="https://render.githubusercontent.com/render/math?math={\color{white}y = mx %2B b}#gh-dark-mode-only"><img src="https://render.githubusercontent.com/render/math?math={y = mx %2B b}#gh-light-mode-only"> to a data set defined by the vectors `x` (independent variable) and `y` (dependent variable).

`[c,r2,eqn] = lsqcurvefit_approx(x,y,'linear')` does the exact same thing as the syntax above.

`[c,r2,eqn] = lsqcurvefit_approx(x,y,'poly',n)` returns the model coefficient vector `c = [a0,...,an]` for the <img src="https://render.githubusercontent.com/render/math?math={\color{white}n^{\textrm{th}}}#gh-dark-mode-only"><img src="https://render.githubusercontent.com/render/math?math={n^{\textrm{th}}}#gh-light-mode-only"> degree polynomial fit <img src="https://render.githubusercontent.com/render/math?math={\color{white}y=a_0 %2B a_1x %2B a_2x^2 %2B \dots %2B a_nx^n}#gh-dark-mode-only"><img src="https://render.githubusercontent.com/render/math?math={y=a_0 %2B a_1x %2B a_2x^2 %2B \dots %2B a_nx^n}#gh-light-mode-only"> to a data set defined by the vectors `x` (independent variable) and `y` (dependent variable).

`[c,r2,eqn] = lsqcurvefit_approx(x,y,'power')` returns the model coefficient vector `c = [a,b]` for the power fit <img src="https://render.githubusercontent.com/render/math?math={\color{white}y=ax^b}#gh-dark-mode-only"><img src="https://render.githubusercontent.com/render/math?math={y=ax^b}#gh-light-mode-only"> to a data set defined by the vectors `x` (independent variable) and `y` (dependent variable).

`[c,r2,eqn] = lsqcurvefit_approx(x,y,'exp')` returns the model coefficient vector `c = [a,b]` for the exponential fit <img src="https://render.githubusercontent.com/render/math?math={\color{white}y=ae^{bx}}#gh-dark-mode-only"><img src="https://render.githubusercontent.com/render/math?math={y=ae^{bx}}#gh-light-mode-only"> to a data set defined by the vectors `x` (independent variable) and `y` (dependent variable).

`[c,r2,eqn] = lsqcurvefit_approx(x,y,'log')` returns the model coefficient vector `c = [a,b]` for the logarithmic fit <img src="https://render.githubusercontent.com/render/math?math={\color{white}y=a %2B b\ln x}#gh-dark-mode-only"><img src="https://render.githubusercontent.com/render/math?math={a %2B b\ln x}#gh-light-mode-only"> to a data set defined by the vectors `x` (independent variable) and `y` (dependent variable).

**NOTE:** Additionally, for all the syntaxes, the coefficient of determination (`r2`) and a string (`eqn`) storing the fitted equation (for use in figure text with LaTeX interpreter) are also returned.


## Additional Notes/Warnings:
   - **Only the linear and polynomial fits are true linear least squares fits**. The nonlinear fits (power, exponential, and logarithmic) are _approximated_ through transforming the model to a linear form and then applying a least squares fit.
   - Taking the logarithm of a negative number produces a complex number. When linearizing, for simplicity, this function will take only the real part of the resulting complex numbers in the case that a negative data point has to be linearized. The resulting fit is typically poor, and a (slightly) better fit could be obtained by excluding those data points altogether.


## Examples and Additional Documentation

   -  See "EXAMPLES.mlx" or the "Examples" tab on the File Exchange page for examples.
   -  See ["Least_Squares_Curve_Fitting.pdf"](https://tamaskis.github.io/documentation/Least_Squares_Curve_Fitting.pdf) (also included with download) for the technical documentation.
