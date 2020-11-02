---
title: "FIN413 homework 1"
author: Xie Zejian
# date: Sep 27, 2020
output:
  pdf_document:
    toc: true
    toc_depth: 2
    # number_sections: true  
    highlight: tango
    latex_engine: pdflatex

export_on_save:
  pandoc: true
---

## 1
### 1
$$ \begin{aligned}
    \min \frac{1}{2}\mathbf{\omega'V\omega} \quad s.t. \quad\mathbf{e'\omega-1,\omega'\overline{r}}=\overline{r}_p
\end{aligned} $$

By Lagrangian and FOC:

$$ L=\frac{1}{2} \mathbf{\omega'V\omega+\lambda}(\overline{r}_p-\mathbf{\omega'\overline{r})+\gamma(1-\omega'e)}$$

$$ \frac{\partial L}{\partial \omega}= \mathbf{V\omega-\lambda\overline{r}-\gamma e=0}\implies \omega^*=\mathbf{\lambda V^-\overline{r}+\gamma V^- e}$$

### 2

Substitute $\omega^*$ into $\overline{r}_p$ and $\mathbf{e'\omega}$:

$$ \begin{aligned}
    &\overline{r}_p=\mathbf{\overline{r}'\omega^*=\lambda \overline{r}'V^-\overline{r}+\gamma\overline{r}'V^-e}
    \\&\mathbf{1=e'\omega^*=\lambda e'V^-\overline{r}+\gamma e'V^-e}
\end{aligned} $$

denoted $\delta=\mathbf{e'V^-e},\alpha=\mathbf{\overline{r}'V^-e},\xi = \mathbf{\overline{r}'V^-\overline{r}}$ where $\delta,\xi>0$ since $\mathbf{V}$ is positive define. Thus we have a linear equations:

$$ \left[\begin{array}{cc}
  \xi & \alpha\\
  \alpha & \delta
\end{array}\right]\left[\begin{array}{c}
  \lambda\\
  \gamma
\end{array}\right]=\left[\begin{array}{c}
  \overline{r}_p\\
  1
\end{array}\right]$$

Note $\Delta=\delta\xi-\alpha^2>0$ since $\mathbf{(\alpha\overline{r}-\xi e)'V^-(\alpha\overline{r}-\xi e)}=\xi(\delta\xi-\alpha^2)>0$ and thus such equations is consistent.

solve and get ($\mathbf{Ax=b}\implies \mathbf{x=A^-b}$)

$$ \lambda=\frac{\delta \overline{r}_p-\alpha}{\delta\xi-\alpha^2},\gamma=\frac{\xi-\alpha\overline{r}_p}{\delta\xi-\alpha^2} $$

hence

$$ \begin{aligned}
  \omega^*&=\mathbf{\lambda V^-\overline{r}+\gamma V^- e}
  \\&=\frac{\delta \overline{r}_p-\alpha}{\delta\xi-\alpha^2}\mathbf{V^-\overline{r}}+\frac{\xi-\alpha\overline{r}_p}{\delta\xi-\alpha^2}\mathbf{V^-e}
  \\&=a+b\overline{r}_p
\end{aligned} $$

where $a=\frac{\mathbf{\xi V^-e-\alpha V^- \overline{r}}}{\delta\xi-\alpha^2}$ and $b=\frac{\mathbf{-\alpha V^- e+\delta V^-\overline{r}}}{\delta\xi-\alpha^2}$

### 3

The minimum variance is given by

$$ \sigma_p^2=\mathbf{\omega'^*V\omega^*}=\omega'^*(\mathbf{\lambda\overline{r}+\gamma e})={\lambda\overline{r}_p+\gamma}=\frac{1}{\delta}+\frac{\delta({\overline{r}_p-\frac{\alpha}{\delta}})^2}{\delta\xi-\alpha^2} $$

Thus the **global minimum variance**(GMV) portfolio is $\frac{1}{\delta}$ when ${\overline{r}_p=\frac{\alpha}{\delta}}$. 

Meanwhile

$$ \begin{aligned}
  \lambda&=0\\
  \gamma&=\frac{1}{\delta}\\
  \omega_{mv}&=\frac{\mathbf{V^-e}}{\delta}=\frac{\mathbf{V^-e}}{\mathbf{e'V^-e}}
\end{aligned} $$

The minimum variance is given by

$$ \sigma_p^2=\mathbf{\omega'^*V\omega^*}=\omega'^*(\mathbf{\lambda\overline{r}+\gamma e})={\lambda\overline{r}_p+\gamma}$$

by some algebra

$$ \lambda\overline{r}_p+\gamma=\frac{1}{\delta}+\frac{\delta({\overline{r}_p-\frac{\alpha}{\delta}})^2}{\delta\xi-\alpha^2}  $$

### 4

The relationship between $\sigma^2_p$ and $\overline{r}_p$ is a parabola in $(\overline{r}_p,\sigma^2_p)$

### 5

Rewrite $\sigma_p^2=\frac{1}{\delta}+\frac{\delta({\overline{r}_p-\frac{\alpha}{\delta}})^2}{\delta\xi-\alpha^2}$ as

$$ \frac{\sigma_p^2}{1/\delta}-\frac{({\overline{r}_p-\frac{\alpha}{\delta}})^2}{(\delta\xi-\alpha^2)/\delta^2}=1 $$

$$ \begin{aligned}
    d\frac{\sigma_p^2}{1/\delta}-d\frac{({\overline{r}_p-\frac{\alpha}{\delta}})^2}{(\delta\xi-\alpha^2)/\delta^2}=d1
    &\implies d\sigma_p\frac{2\sigma_p}{1/\delta}-d\overline{r}_p\frac{2({\overline{r}_p-\frac{\alpha}{\delta}})}{(\delta\xi-\alpha^2)/\delta^2}=0
    \\&\implies \frac{d\overline{r}_p}{d\sigma_p}=\frac{\Delta\sigma_p}{\delta (\overline{r}_p-\frac{\alpha}{\delta})}
\end{aligned} $$

Note when $\sigma_p\to \infty$:

$$  \frac{\sigma_p^2}{1/\delta}-\frac{({\overline{r}_p-\frac{\alpha}{\delta}})^2}{(\delta\xi-\alpha^2)/\delta^2}=0 $$

hence 

$$ \lim_{\sigma_p\to \infty} \frac{\overline{r}_p-\frac{\alpha}{\delta}}{\sigma_p}=\sqrt{\Delta/\delta} $$

$$ \begin{aligned}
    \lim_{\sigma_p \to \infty}\frac{\Delta\sigma_p}{\delta (\overline{r}_p-\frac{\alpha}{\delta})}&=\frac{\Delta}{\delta}\sqrt{\frac{\delta}{\Delta}}=\sqrt{\frac{\Delta}{\delta}}
\end{aligned} $$

### 6

The **global minimum variance**(GMV) portfolio is $\frac{1}{\delta}$ when ${\overline{r}_p=\frac{\alpha}{\delta}}$ since $\sigma_p^2=\frac{1}{\delta}+\frac{\delta({\overline{r}_p-\frac{\alpha}{\delta}})^2}{\delta\xi-\alpha^2}$ meanwhile

$$ \begin{aligned}
  \lambda&=\frac{\delta \overline{r}_p-\alpha}{\delta\xi-\alpha^2}=0\\
  \gamma&=\frac{\xi-\alpha\overline{r}_p}{\delta\xi-\alpha^2}=\frac{\xi-\alpha\frac{\alpha}{\delta}}{\delta\xi-\alpha^2}=\frac{1}{\delta}\\
  \omega_{mv}&=0+\frac{\mathbf{V^-e}}{\delta}=\frac{\mathbf{V^-e}}{\mathbf{e'V^-e}}
\end{aligned} $$

## 2

Suppose covariance between portfolios $p$ and $q$

$$ \text{Cov}(\mathbf{r_p,r_q})=\omega_p'\mathbf{V}\omega_q $$

Suppose $q$ on the frontier, then

$$ \omega_p'\mathbf{V}\omega_q=\omega_p'\mathbf{(\lambda \overline{r}+\gamma e)} $$

Moreover, if $p$ is GMV portfolio, then 

$$ \omega_p'\mathbf{(\lambda \overline{r}+\gamma e)} =\omega_p'(\frac{1}{\delta}\mathbf{e})=\frac{1}{\delta} $$

since $\lambda=0$ and $\gamma=\frac{1}{\delta}$.

## 3

Recall

$$ \left[\begin{array}{cc}
  \xi & \alpha\\
  \alpha & \delta
\end{array}\right]\left[\begin{array}{c}
  \lambda\\
  \gamma
\end{array}\right]=\left[\begin{array}{c}
  \overline{r}_p\\
  1
\end{array}\right] $$

hence we have $\lambda\alpha+\gamma\delta=1$ clearly.

## 4

A portofolio $\omega$ is on the efficient froniter iff(if and only if)  it's return $\overline{r}_p\ge r_{mv}$ and recall $\omega=a+b \overline{r}_p$, thus there is a bijection between $\omega_i$ and $r_i$. Suppose the return of $\omega_i$ is $r_i$, 

$$\omega=\begin{bmatrix}
    \omega_1&\cdots&\omega_n
\end{bmatrix},\mathbf{c}=\begin{bmatrix}
    c_1\\
    \vdots\\c_n
\end{bmatrix}$$

Firstly, verify the convex combination is a legal portfolio:

$$ \mathbf{e'(\omega c)=(e'\omega)c=e'c}=1 $$

since $\forall \omega_i \mathbf{e'\omega_i}=1, \mathbf{e'c}=1$. Then it's sufficient to show that $\mathbf{c'r} \ge r_{mv}$. It's clearly since

$$ \mathbf{c'r}=\sum c_i\omega_i\ge \sum c_i \min(r_i)=\min(r_i)\sum c_i=\min(r_i)\ge r_{mv} $$

## 5
### 1
Substitute $\omega_0=1-\mathbf{e'\omega}$, then

$$ \mathbf{\omega'\overline{r}}+ (1-\mathbf{e'\omega})r_f=\overline{r}_p\implies \omega'(\mathbf{\overline{r}}-r_f\mathbf{e})+r_f=\overline{r}_p $$

The problem is

$$ \min_{\omega,\omega_0} \frac{1}{2}\omega'\mathbf{V}\omega \quad s.t.\quad \omega'(\mathbf{\overline{r}}-r_f\mathbf{e})+r_f=\overline{r}_p $$

by the Lagrangian 

$$ L=\frac{1}{2}\omega'\mathbf{V}\omega+\lambda(\overline{r}_p-\omega'(\mathbf{\overline{r}}-r_f\mathbf{e})-r_f) $$

FOC with $\omega$:
$$ \frac{\partial L}{\partial\omega}=\mathbf{V}\omega-\lambda(\mathbf{\overline{r}}-r_f\mathbf{e})=0\implies \omega^*=\lambda\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e}) $$

### 2

$$ \overline{r}_p-{\omega^{*}}'(\mathbf{\overline{r}}-r_f\mathbf{e})-r_f=0\implies\lambda=\frac{\overline{r}_p-r_f}{(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})} =\frac{\overline{r}_p-r_f}{\xi-2\alpha r_f+\delta r_f^2}$$

Substitute into $\omega^*$:

$$ \omega= \frac{\overline{r}_p-r_f}{\xi-2\alpha r_f+\delta r_f^2}\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})$$

The tangency portofolio is

$$ \omega_D=\frac{\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})}{\mathbf{e'V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})}=\frac{\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})}{\alpha-r_f\delta}$$

### 3


$$ \sigma_p^2=\omega'\mathbf{V}\omega= \lambda^2(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-\mathbf{V}\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})=\frac{(\overline{r}_p-r_f)^2}{(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})}$$

In geometry view, the frontier degenerate into two crossing line:

$$ \overline{r}_p=r_f\pm\sqrt{(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})}=r_f\pm \sqrt{\xi-2\alpha r_f+\delta r_f^2}\sigma_p $$

### 4

$$ \begin{aligned}
  \text{Cov}(\overline{r}_p,\overline{r}_q)&=
  \omega_p'\mathbf{V}\omega_q
  \\&=(\lambda_p\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e}))'\mathbf{V}(\lambda_q\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e}))
  \\&=\lambda_p\lambda_q (\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})
  \\&=\frac{(\overline{r}_p-r_f)(\overline{r}_q-r_f)}{ (\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})}
  \\&=\frac{(\overline{r}_p-r_f)(\overline{r}_q-r_f)}{ \xi-2\alpha r_f+\delta r_f^2}
\end{aligned}$$

### 5

The shrpe ratio is defined by

$$S_p=\frac{\overline{r}_p-r_f}{\sigma_p} = \frac{\omega'(\mathbf{\overline{r}}-r_f\mathbf{e})}{\sqrt{\omega'\mathbf{V}\omega}} $$

Let $\mathbf{r}=\mathbf{\overline{r}}-r_f\mathbf{e}$ and

$$\phi: w\mapsto \begin{bmatrix}\omega'\mathbf{r} \\ \omega'\mathbf{V}\omega\end{bmatrix},\quad h(x,y):=\frac x {y^{1/2}}$$
Then $S_p = h\circ\phi(w)$, and thus

$$ \begin{aligned}
  \frac{\partial S_p}{\partial \omega}&=\frac{\partial h}{\partial \phi}\frac{\partial \phi}{\partial \omega}
  \\&=\begin{bmatrix}
    \frac{1}{( \omega'\mathbf{V}\omega)^{1/2}} &
    -\frac{\omega'\mathbf{r}}{2( \omega'\mathbf{V}\omega)^{3/2}}
  \end{bmatrix}
  \begin{bmatrix}
    \mathbf{r'}
    \\2\omega'\mathbf{V}
  \end{bmatrix}
  \\&=\frac{ \omega'\mathbf{V}\omega \mathbf{r'}-\omega'\mathbf{r}\omega'\mathbf{V}}{( \omega'\mathbf{V}\omega)^{3/2}}
\end{aligned} $$

Setting to zero, 

$$ \omega'\mathbf{V}\omega \mathbf{r}-\omega'\mathbf{r}\mathbf{V}\omega=\mathbf{0}\implies\omega=\frac{ \omega'\mathbf{V}\omega }{\omega'\mathbf{r}}\mathbf{V^-r}$$

Note the scale of $\omega$ is independent to $S_p$. If we assume $\mathbf{e'\omega}=1$ additionally, then 

$$ \omega=\frac{\mathbf{V^-r}}{\mathbf{e'V^-r}}=\frac{\mathbf{V^-}(\overline{\mathbf{r}}-r_f\mathbf{e})}{\mathbf{e'V^-}(\overline{\mathbf{r}}-r_f\mathbf{e})}=\frac{\tilde{\omega}}{\mathbf{e}'\tilde{\omega}}=\omega_D $$

For now, we have

$$ \omega=(1-x)\omega_D+x\mathbf{e_i} \implies \frac{\partial\omega}{\partial x}=\mathbf{e_i}-\omega_D $$

where $\mathbf{e_i}$ is the vector all zero but the $i$th component is $1$. Hence

$$ \frac{\partial S_p}{\partial x}= \frac{\partial S_p}{\partial \omega}\frac{\partial\omega}{\partial x}=\frac{ (\omega'\mathbf{V}\omega \mathbf{r'}-\omega'\mathbf{r}\omega'\mathbf{V})(\mathbf{e_i}-\omega_D)}{( \omega'\mathbf{V}\omega)^{3/2}} $$

When $x=0$, $\omega=\omega_D$, note $\omega_D$ is the solution to $\frac{\partial S_p}{\partial\omega}=0$, hence $\frac{\partial S_p}{\partial x}=0$ also holds when $x=0$, that is what we desired. Then consider

$$ \begin{aligned}
  \omega_D'\mathbf{V}\omega_D \mathbf{r}-\omega_D'\mathbf{r}\mathbf{V}\omega_D=\mathbf{0}&\implies \sigma_D^2\mathbf{r}-({r_D}-r_f)\mathbf{V\omega_D}=0
  \\&\implies \sigma_D^2\mathbf{r}-({r_D}-r_f) \text{Cov}(\mathbf{\tilde{r}},\tilde{r_D})=0
  \\&\implies \sigma_D^2(\mathbf{\overline{r}}-r_f\mathbf{e})-({r_D}-r_f)\text{Cov}(\mathbf{\tilde{r}},\tilde{r_D})=0
  \\&\implies\mathbf{\overline{r}}-r_f\mathbf{e}=\frac{\text{Cov}(\mathbf{\tilde{r}},\tilde{r_D})}{\sigma_D^2}({r_D}-r_f)
\end{aligned} $$

Then note 

$$ \mathbf{\overline{r}}=\begin{bmatrix}
  E[\tilde{r_1}]\\
  E[\tilde{r_2}]\\
  \vdots\\
  E[\tilde{r_n}]\\
\end{bmatrix},\text{Cov}(\mathbf{\tilde{r}},\tilde{r_D})=\begin{bmatrix}
  \text{Cov}(\tilde{r_1},\tilde{r_D})\\
  \text{Cov}(\tilde{r_2},\tilde{r_D})\\
  \vdots\\
  \text{Cov}(\tilde{r_n},\tilde{r_D})
\end{bmatrix} $$

thus we can split it into

$$ E[\tilde{r_i}]-r_f=\frac{\text{Cov}({\tilde{r_i}},\tilde{r_D})}{\sigma_D^2}E[{\tilde{r_D}}-r_f] $$

This is not CAPM since the tangency portfolio may not be the market portfolio.

## 6

### 1

It's increasing since

$$ \frac{\partial U}{\partial W}= b \exp(-bW)>0 $$

and it's concave since

$$ \frac{\partial^2 U}{\partial W^2}=-b^2\exp(-bW)<0 $$

### 2

$$ \begin{aligned}
  E[U(W)]=E[U(r_p)]=E[-e^{-b(r_f+\omega'\mathbf{r})}]
\end{aligned} $$

where $\mathbf{r}={\mathbf{\tilde{r}}}-r_f\mathbf{e}\sim N(\mathbf{\overline{r}}-r_f\mathbf{e},\mathbf{V})$. It's sufficent to maximize

$$ E[e^{(-b\omega)'\mathbf{r}}]=\exp\{(-b\omega)'E(\mathbf{{r}})+b^2\omega'\mathbf{V}\omega/2\} $$

then

$$ \frac{\partial(-b\omega)'E(\mathbf{{r}})+b^2\omega'\mathbf{V}\omega/2  }{\partial\omega}=-bE(\mathbf{{r}})+b^2\mathbf{V\omega}=0 $$

hence

$$ \omega=\frac{\mathbf{V^-}E(\mathbf{{r}})}{b}=\frac{\mathbf{V^-}(\mathbf{\overline{r}}-r_f\mathbf{e})}{b}=\frac{\mathbf{V^-}(\mathbf{\overline{r}}-r_f\mathbf{e})\mathbf{e'V}(\mathbf{\overline{r}}-r_f\mathbf{e})}{b\mathbf{e'V}(\mathbf{\overline{r}}-r_f\mathbf{e})}=\frac{\mathbf{e'V}(\mathbf{\overline{r}}-r_f\mathbf{e})}{b}\omega_D $$

### 3

Larger $b$ reduce the wealth invested in the tangency portfolio, that is why it measure the extent of risk aversion.


## 7

### 1

$$ r_A-r_f=\beta (r_B-r_f)+\epsilon $$

where $\beta=\frac{\text{Cov}(r_A-r_f,r_B-r_f)}{\sigma_B^2}$, since the intercept is $0$, we have

$$ \overline{r}_A-r_f=\beta(\overline{r}_B-r_f) \implies \beta=\frac{\overline{r}_A-r_f}{\overline{r}_B-r_f}$$

Thus

$$ \begin{aligned}
  \frac{\overline{r}_B-r_f}{\sigma_B}>  \frac{\overline{r}_A-r_f}{\sigma_A}&\iff \frac{\overline{r}_A-r_f}{\overline{r}_B-r_f}<\frac{\sigma_A}{\sigma_B}
  \\&\iff \beta<\frac{\sigma_A}{\sigma_B}
  \\&\iff \frac{\text{Cov}(r_A-r_f,r_B-r_f)}{\sigma_B^2}<\frac{\sigma_A}{\sigma_B}
  \\&\iff \frac{\text{Cov}(r_A,r_B)}{\sigma_B^2}<\frac{\sigma_A}{\sigma_B}
  \\&\iff \text{Cov}(r_A,r_B) < \sigma_A\sigma_B
\end{aligned} $$

which is clearly holds.

### 2

If $\alpha \neq 0$:

$$ r_A-r_f= \alpha+\beta (r_B-r_f)+\epsilon$$

Denote $r=r_B-r_f$, $\text{Var}(r)=\sigma_B^2, \text{Var}(\epsilon)=\sigma^2$, then we have

$$ \text{Var}(r_A)=\text{Var}(r_A-r_f)=\beta^2\sigma_B^2+\sigma^2 $$

Recall the maximum sharpe ratio is

$$ S_p=\sqrt{(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})} $$

where

$$ \overline{\mathbf{r}}-r_f\mathbf{e}=\begin{bmatrix}
  r_A-r_f\\
  r_B-r_f
\end{bmatrix} =\begin{bmatrix}
  \beta r+\alpha\\
  r
\end{bmatrix}$$

$$ \mathbf{V}=\begin{bmatrix}
  \beta^2\sigma_B^2+\sigma^2& \beta \sigma_B^2 
  \\
  \beta \sigma_B^2 & \sigma_B^2
\end{bmatrix} $$

Compute the maximun sharpe ratio directly:

$$ 
\begin{aligned}
  \begin{bmatrix}
  \beta r+\alpha\\
  r
\end{bmatrix}'\begin{bmatrix}
  \beta^2\sigma_B^2+\sigma^2& \beta \sigma_B^2 
  \\
  \beta \sigma_B^2 & \sigma_B^2
\end{bmatrix}^-\begin{bmatrix}
  \beta r+\alpha\\
  r
\end{bmatrix}&=
  \begin{bmatrix}
  \beta r+\alpha\\
  r
\end{bmatrix}'\begin{bmatrix}
 \frac{1}{\sigma ^2} & -\frac{\beta }{\sigma ^2} \\
 -\frac{\beta }{\sigma ^2} &  \frac{\beta ^2 \sigma_B^2+\sigma ^2}{\sigma^2 \sigma_B^2} \\
\end{bmatrix}\begin{bmatrix}
  \beta r+\alpha\\
  r
\end{bmatrix}
\\&=r \left(\frac{r \left(\beta ^2\sigma_B^2+\sigma ^2\right)}{\sigma ^2\sigma_B^2}-\frac{\beta  (\alpha +\beta  r)}{\sigma ^2}\right)+(\alpha +\beta  r) \left(\frac{\alpha +\beta  r}{\sigma ^2}-\frac{\beta  r}{\sigma ^2}\right)
\\&=\frac{\alpha ^2}{\sigma ^2}+\frac{r^2}{\sigma_B^2}
\end{aligned}
 $$


$$ \max_\omega S_p=\sqrt{\frac{\alpha ^2}{\sigma ^2}+\frac{(r_B-rf)^2}{\sigma_B^2}} $$










