---
title: "Mean-variance portfolio notes"
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
$$R_p=\frac{\sum R_i\omega_iW_0}{W_0}=\omega'R$$

$$ \mathbf{r_p}=R_p-1=\omega'\mathbf{r} $$

where $\mathbf{r}$ is random vector with mean $\overline{\mathbf{r}}$ and variance $\mathbf{V}$.

hence $E[\mathbf{r_p}]=\omega'\mathbf{\overline{r}}$ and 

$$ \text{Cov}(\mathbf{r})=\text{cov}(\mathbf{\omega'r})=\mathbf{\omega'\text{Cov}(r)\omega}=\mathbf{\omega'V\omega} $$

Then the problem is 

$$ \begin{aligned}
    \min \frac{1}{2}\mathbf{\omega'V\omega} \quad s.t. \quad\mathbf{e'\omega-1,\omega'\overline{r}}=\overline{r}_p
\end{aligned} $$

By Lagrangian

$$ L=\frac{1}{2} \mathbf{\omega'V\omega+\lambda}(\overline{r}_p-\mathbf{\omega'\overline{r})+\gamma(1-\omega'e)}$$

$$ \frac{\partial L}{\partial \omega}= \mathbf{V\omega-\lambda\overline{r}-\gamma e=0}\implies \omega^*=\mathbf{\lambda V^-\overline{r}+\gamma V^- e}$$

Hence 

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

Note $\delta\xi-\alpha^2>0$ since $\mathbf{(\alpha\overline{r}-\xi e)'V^-(\alpha\overline{r}-\xi e)}=\xi(\delta\xi-\alpha^2)>0$ and thus such equations is consistent.

solve and get

$$ \lambda=\frac{\delta \overline{r}_p-\alpha}{\delta\xi-\alpha^2},\gamma=\frac{\xi-\alpha\overline{r}_p}{\delta\xi-\alpha^2} $$

and

$$ \begin{aligned}
  \omega^*&=\mathbf{\lambda V^-\overline{r}+\gamma V^- e}
  \\&=\frac{\delta \overline{r}_p-\alpha}{\delta\xi-\alpha^2}\mathbf{V^-\overline{r}}+\frac{\xi-\alpha\overline{r}_p}{\delta\xi-\alpha^2}\mathbf{V^-e}
  \\&=a+b\overline{r}_p
\end{aligned} $$

where $a=\frac{\mathbf{\xi V^-e-\alpha V^- \overline{r}}}{\delta\xi-\alpha^2}$ and $b=\frac{\mathbf{-\alpha V^- e+\delta V^-\overline{r}}}{\delta\xi-\alpha^2}$

The minimum variance is given by

$$ \sigma_p^2=\mathbf{\omega'^*V\omega^*}=\omega'^*(\mathbf{\lambda\overline{r}+\gamma e})={\lambda\overline{r}_p+\gamma}=\frac{1}{\delta}+\frac{\delta({\overline{r}_p-\frac{\alpha}{\delta}})^2}{\delta\xi-\alpha^2} $$

Thus the **global minimum variance**(GMV) portfolio is $\frac{1}{\delta}$ when ${\overline{r}_p=\frac{\alpha}{\delta}}$. 

Meanwhile

$$ \begin{aligned}
  \lambda&=0\\
  \gamma&=\frac{1}{\delta}\\
  \omega_{mv}&=\frac{\mathbf{V^-e}}{\delta}=\frac{\mathbf{V^-e}}{\mathbf{e'V^-e}}
\end{aligned} $$

## Geometry

In geometry view

$$ \frac{\sigma_p^2}{1/\delta}-\frac{({\overline{r}_p-\frac{\alpha}{\delta}})^2}{(\delta\xi-\alpha^2)/\delta^2}=1 $$

it's a hyperbola with center $(0,\alpha/\delta)$ and asymptote ${\overline{r}_p=\frac{\alpha}{\delta}\pm \sqrt{\frac{\delta\xi -\alpha^2}{\xi}}\sigma_p}$(recall that asymptote is $y=\pm\frac{b}{a}x$ in $\frac{x^2}{a^2}-\frac{y^2}{b^2}=1$).

## Two Fund Theorem

The mean-variance frontier can be replicated by any two frontier portfolios and any linear combination of frontier portfolios is on the frontier.

Suppose ${r_1}$ and ${r_2}$ are any given expected return, note

$$\forall {r_3},\exists x\ni x{r_1}+(1-x){r_2}={r_3}$$

Then the weight combined such way is just what we want

$$\omega_3=x\omega_1+(1-x)\omega_2= x({a+br_1})+(1-x)({a+br_2})={a+br_3} $$

If ${r_1,r_2\ge \frac{\alpha}{\delta}}$, thus they are on efficient frontier, their convex combine still $\ge \frac{\alpha}{\delta}$

$$ c{r_1}+(1-c){r_2}=\frac{\alpha}{\delta}+c({r_1-}\frac{\alpha}{\delta})+(1-c)({r_2}-\frac{\alpha}{\delta})\ge \frac{\alpha}{\delta} $$

that is, any convex combination of efficient frontier portfolios will be an efficient
frontier portfolio.

## Decomposition

Suppose covariance between portfolios $p$ and $q$

$$ \text{Cov}(\mathbf{r_p,r_q})=\omega_p'\mathbf{V}\omega_q $$

Suppose $q$ on the frontier, then

$$ \omega_p'\mathbf{V}\omega_q=\omega_p'\mathbf{(\lambda \overline{r}+\gamma e)} $$

Moreover, if

1.
    $p$ is GMV portfolio, then

    $$ \omega_p'\mathbf{(\lambda \overline{r}+\gamma e)} =\omega_p'(\frac{1}{\delta}\mathbf{e})=\frac{1}{\delta} $$
2.
    $p$ has the same expected return with $q$, then

    $$ \omega_p'\mathbf{(\lambda \overline{r}+\gamma e)}=\lambda {\overline{r}_q+\gamma}=\sigma_q^2 $$

Thus we have

> The covariance of the return on the global minimum variance (GMV) portfolio
and that on any portfolio (not necessary on the frontier) is always equal to $\sigma_{mv}^2=\frac{1}{\delta}$.

Apply this we get $\text{Cov}(\mathbf{r_p-r_{mv},r_{mv}})=\text{Cov}(\mathbf{r_p,r_{mv}})-\sigma_{mv}^2=0$ immediately. We call $\epsilon=\mathbf{r_p-r_{mv}}$ **excess return**.

> The covariance of the return on a frontier portfolio $q$ and that on any portfolio
$p$ (not on the frontier) with the same expected return as $q$ is always equal to
the variance of the frontier portfolio $q$. Formally $E[\mathbf{r_p}]=E[\mathbf{r_q}]\implies \text{Cov}(\mathbf{r_p,r_q})=\sigma_q^2$.

It implies that we can decompose $\mathbf{r_p=r_q+\epsilon_p}$ where $E[\epsilon]=\text{Cov}(\epsilon_p,\mathbf{r_q})=0$

Rewrite the excess return as $\epsilon=b_p \mathbf{r^*}$, then $\mathbf{r_p}$ can be decomposed into

$$ \mathbf{r_p=r_{mv}}+b_p\mathbf{r^*}+\epsilon_p $$

where $\mathbf{r}^*$ is an excess return and $b_p\in \mathbb{R}$.Note $\text{Cov}(\mathbf{r_{mv},\epsilon_p})=\text{Cov}(\mathbf{r_{mv},r_p-r_q})=0$ then $\text{Cov}(\mathbf{r}^*,\epsilon_p)$ is also zero. Hence

$$ \text{Var}(\mathbf{r_p})=\overbrace{\underbrace{\sigma_{mv}^2}_{\text{unavoidable risk}}+b_p^2\text{Var}(\mathbf{r^*})}^{\text{systematic risk}}+\underbrace{\text{Var}(\epsilon_p)}_{\text{idiot risk}} $$

One can reduce $\epsilon_p$ to zero to avoid idiot risk and get a frontier portfolio.

## Zero covariance

Recall the covariance between $p$ and $q$, now suppose they are both on frontier:

$$ \begin{aligned}
  \omega_p'\mathbf{V}\omega_q=\frac{1}{\delta}+\frac{\delta(\overline{r}_p-\frac{\alpha}{\delta})(\overline{r}_q-\frac{\alpha}{\delta})}{\delta\xi-\alpha^2}
\end{aligned} $$

Setting this to $0$ and slove for $\overline{r}_q$

$$ \overline{r}_q=\frac{\alpha}{\delta}-\frac{\delta\xi-\alpha^2}{\delta^2(\overline{r}_p-\alpha/\delta)} $$

Suppose the tagent line in $\overline{r}_p$, which slope is

$$ \frac{\partial \overline{r}_p}{\partial \sigma_p}=\frac{\delta\xi-\alpha^2}{\delta(\overline{r}_p-\frac{\alpha}{\delta})}\sigma_p $$

(Recall $\frac{x^2}{a^2}-\frac{y^2}{b^2}=1\implies \frac{2x}{a^2}-\frac{2yy'}{b^2}=0\implies y'=\frac{b^2x^2}{a^2y^2}$)

hence its intercept at $\sigma_p=0$ is

$$ \overline{r}_p-\frac{\delta\xi-\alpha^2}{\delta(\overline{r}_p-\frac{\alpha}{\delta})}\sigma_p^2=\overline{r}_p-\frac{\delta\xi-\alpha^2}{\delta(\overline{r}_p-\frac{\alpha}{\delta})} (\frac{1}{\delta}+\frac{\delta({\overline{r}_p-\frac{\alpha}{\delta}})^2}{\delta\xi-\alpha^2})=\frac{\alpha}{\delta}-\frac{\delta\xi-\alpha^2}{\delta^2(\overline{r}_p-\alpha/\delta)} =\overline{r}_q$$

[]()




<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>