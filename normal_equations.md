**Explaining the normal equations**

The normal equations arise from setting the partial derivatives of the sum of squared errors (SSR) to zero, which gives us two equations for b0 and b1. This method, developed by Legendre in 1805 and later refined by Gauss, is used for least-squares estimation:

1. n b0 + b1 Σ xi = Σ yi  
2. b0 Σ xi + b1 Σ xi² = Σ xi yi  

These equations are then solved for b0 and b1. Interesting context: Gauss used least-squares earlier but published his work in 1809. If you want, I can dive deeper into multivariate normal equations or their geometric interpretation!
# Direct Answer

The normal equations arise by minimizing the sum of squared residuals in simple linear regression. You form the loss  
\[
S(b_0,b_1)=\sum_{i=1}^n\bigl(y_i - b_0 - b_1x_i\bigr)^2
\]  
and set its partial derivatives with respect to \(b_0\) and \(b_1\) to zero. This yields two simultaneous linear equations—the “normal equations”—which you then solve for \(b_0\) and \(b_1\).

---

## 1. Derivation from First Principles

Given data points \((x_i,y_i)\), define the residual \(e_i = y_i - b_0 - b_1x_i\).  
The least-squares objective is  
\[
S = \sum_{i=1}^n e_i^2 = \sum_{i=1}^n (y_i - b_0 - b_1x_i)^2.
\]  
Take gradients and set to zero:

1. ∂S/∂\(b_0\)=0  
   \[
   -2\sum_{i=1}^n(y_i - b_0 - b_1x_i)=0
   \;\;\Longrightarrow\;\;
   n\,b_0 + b_1\sum_{i}x_i = \sum_{i}y_i.
   \]
2. ∂S/∂\(b_1\)=0  
   \[
   -2\sum_{i=1}^n x_i(y_i - b_0 - b_1x_i)=0
   \;\;\Longrightarrow\;\;
   b_0\sum_{i}x_i + b_1\sum_{i}x_i^2 = \sum_{i}x_i\,y_i.
   \]

These two equations in \(b_0\) and \(b_1\) are the normal equations. Solving them gives the familiar formulas:
\[
b_1 = \frac{\sum_i (x_i-\bar x)(y_i-\bar y)}{\sum_i (x_i-\bar x)^2}, 
\quad
b_0 = \bar y - b_1\,\bar x.
\]

---

## 2. Historical Origin

- **Adrien-Marie Legendre (1805)** first published the method of least squares without attribution to anyone else, introducing it as a tool for geodesy.  
- **Carl Friedrich Gauss** claimed earlier use (circa 1795) in astronomical orbit calculations, and formally presented the theory of least squares and the normal equations in *Theoria motus corporum coelestium* (1809).  
- The term “normal equations” reflects their role in projecting data onto the subspace spanned by the regressors—mathematically “normal” to the residual vector.

---

## 3. Geometric Interpretation

- In vector form, let \(\mathbf{X}\) be the \(n\times2\) design matrix \([\mathbf{1}\;\;\mathbf{x}]\) and \(\mathbf{y}\) the \(n\)-vector of responses.  
- The least-squares solution \(\hat{\boldsymbol b} = (\hat b_0,\hat b_1)^\top\) solves  
  \[
  \mathbf{X}^\top \mathbf{X}\,\hat{\boldsymbol b} = \mathbf{X}^\top \mathbf{y},
  \]  
  which are exactly the normal equations. This equation means the residual vector \(\mathbf{y} - \mathbf{X}\hat{\boldsymbol b}\) is orthogonal (“normal”) to the column space of \(\mathbf{X}\).

---

## Beyond Simple Linear Regression

- In multiple regression, you generalize to an \(n\times p\) design matrix and get \(p\) normal equations: \(\mathbf{X}^\top\mathbf{X}\boldsymbol\beta = \mathbf{X}^\top\mathbf{y}\).  
- The invertibility of \(\mathbf{X}^\top\mathbf{X}\) ties directly to the absence of perfect multicollinearity among predictors.

---

Would you like to explore how these equations extend to ridge regression (adding a regularization term), or see a worked example step-by-step with your own data?
