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

# Risky Assets
Suppose $\mathbf{r}$ is a $n\times 1$ random vector with mean $\overline{\mathbf{r}}$ and invertible variance $\mathbf{V}$, then the portofolio return is

$$ \mathbf{r_p}=\omega'\mathbf{r} $$

hence $E[\mathbf{r_p}]=\omega'\mathbf{\overline{r}}$ and 

$$ \text{Cov}(\mathbf{\overline{r}_p})=\text{cov}(\mathbf{\omega'r})=\mathbf{\omega'\text{Cov}(r)\omega}=\mathbf{\omega'V\omega} $$

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

Note $\Delta=\delta\xi-\alpha^2>0$ since $\mathbf{(\alpha\overline{r}-\xi e)'V^-(\alpha\overline{r}-\xi e)}=\xi(\delta\xi-\alpha^2)>0$ and thus such equations is consistent.

solve ($\mathbf{Ax=b}\implies \mathbf{x=A^-b}$):

$$ \lambda=\frac{\delta \overline{r}_p-\alpha}{\delta\xi-\alpha^2},\gamma=\frac{\xi-\alpha\overline{r}_p}{\delta\xi-\alpha^2} $$

and

$$ \begin{aligned}
  \omega^*&=\mathbf{\lambda V^-\overline{r}+\gamma V^- e}
  \\&=\frac{\delta \overline{r}_p-\alpha}{\delta\xi-\alpha^2}\mathbf{V^-\overline{r}}+\frac{\xi-\alpha\overline{r}_p}{\delta\xi-\alpha^2}\mathbf{V^-e}
  \\&=a+b\overline{r}_p
\end{aligned} $$

where $a=\frac{\mathbf{\xi V^-e-\alpha V^- \overline{r}}}{\delta\xi-\alpha^2}$ and $b=\frac{\mathbf{-\alpha V^- e+\delta V^-\overline{r}}}{\delta\xi-\alpha^2}$

The minimum variance is given by

$$ \sigma_p^2=\mathbf{\omega'^*V\omega^*}=\omega'^*(\mathbf{\lambda\overline{r}+\gamma e})={\lambda\overline{r}_p+\gamma}$$

by some algebra

$$ \lambda\overline{r}_p+\gamma=\frac{1}{\delta}+\frac{\delta({\overline{r}_p-\frac{\alpha}{\delta}})^2}{\delta\xi-\alpha^2}  $$

Thus the **global minimum variance**(GMV) portfolio is $\frac{1}{\delta}$ when ${\overline{r}_p=\frac{\alpha}{\delta}}$, meanwhile

$$ \begin{aligned}
  \lambda&=\frac{\delta \overline{r}_p-\alpha}{\delta\xi-\alpha^2}=0\\
  \gamma&=\frac{\xi-\alpha\overline{r}_p}{\delta\xi-\alpha^2}=\frac{\xi-\alpha\frac{\alpha}{\delta}}{\delta\xi-\alpha^2}=\frac{1}{\delta}\\
  \omega_{mv}&=0+\frac{\mathbf{V^-e}}{\delta}=\frac{\mathbf{V^-e}}{\mathbf{e'V^-e}}
\end{aligned} $$

## Geometry

In geometry view, rewrite $\sigma_p^2=\frac{1}{\delta}+\frac{\delta({\overline{r}_p-\frac{\alpha}{\delta}})^2}{\delta\xi-\alpha^2}$ as

$$ \frac{\sigma_p^2}{1/\delta}-\frac{({\overline{r}_p-\frac{\alpha}{\delta}})^2}{(\delta\xi-\alpha^2)/\delta^2}=1 $$

it's a hyperbola with center $(0,\alpha/\delta)$ and asymptote ${\overline{r}_p=\frac{\alpha}{\delta}\pm \sqrt{\frac{\delta\xi -\alpha^2}{\delta}}\sigma_p}$(recall that asymptote is $y=\pm\frac{b}{a}x$ in $\frac{x^2}{a^2}-\frac{y^2}{b^2}=1$).

## Two Fund Theorem

The mean-variance frontier can be replicated by any two frontier portfolios and any linear combination of frontier portfolios is on the frontier.

Suppose ${r_1}$ and ${r_2}$ are any given expected return, note

$$\forall {r_3},\exists x\ni x{r_1}+(1-x){r_2}={r_3}$$

Then the weight combined such way is just what we want.


$$\omega_3=x\omega_1+(1-x)\omega_2= x({a+br_1})+(1-x)({a+br_2})={a+br_3} $$


> Any convex combination of efficient frontier portfolios will be an efficient frontier portfolio.

**Proof** A portofolio $\omega$ is on the efficient froniter iff(if and only if)  it's return $\overline{r}_p\ge r_{mv}$ and recall $\omega=a+b \overline{r}_p$, thus there is a bijection between $\omega_i$ and $r_i$. Suppose the return of $\omega_i$ is $r_i$, 

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

Continue the discussion of the covariance between $p$ and $q$, now suppose they are both on frontier:

$$ \begin{aligned}
  \omega_p'\mathbf{V}\omega_q=\frac{1}{\delta}+\frac{\delta(\overline{r}_p-\frac{\alpha}{\delta})(\overline{r}_q-\frac{\alpha}{\delta})}{\delta\xi-\alpha^2}
\end{aligned} $$

Setting this to $0$ and slove for $\overline{r}_q$

$$ \overline{r}_q=\frac{\alpha}{\delta}-\frac{\delta\xi-\alpha^2}{\delta^2(\overline{r}_p-\alpha/\delta)} $$

Then we are ready to show that

> $\overline{r}_q$ is equal to the intercept of the tangent line to MVF at $(\overline{r}_p,\sigma_p)$ 

Suppose the tagent line in $\overline{r}_p$, the slope is 

$$ \frac{\partial \overline{r}_p}{\partial \sigma_p}=\frac{\delta\xi-\alpha^2}{\delta(\overline{r}_p-\frac{\alpha}{\delta})}\sigma_p $$

(Recall $\frac{x^2}{a^2}-\frac{y^2}{b^2}=1\implies \frac{2x}{a^2}-\frac{2yy'}{b^2}=0\implies y'=\frac{b^2x^2}{a^2y^2}$)

thus its intercept at $\sigma_p=0$ is

$$ \overline{r}_p-\frac{\delta\xi-\alpha^2}{\delta(\overline{r}_p-\frac{\alpha}{\delta})}\sigma_p^2=\overline{r}_p-\frac{\delta\xi-\alpha^2}{\delta(\overline{r}_p-\frac{\alpha}{\delta})} (\frac{1}{\delta}+\frac{\delta({\overline{r}_p-\frac{\alpha}{\delta}})^2}{\delta\xi-\alpha^2})=\frac{\alpha}{\delta}-\frac{\delta\xi-\alpha^2}{\delta^2(\overline{r}_p-\alpha/\delta)} =\overline{r}_q$$

Let $\overline{r}_q=0$, then

$$ \frac{\alpha}{\delta}-\frac{\delta\xi-\alpha^2}{\delta^2(\overline{r}_p-\alpha/\delta)}=0 $$

solve for $\overline{r}_p$, we get

$$ \overline{r}_p=\frac{\delta\xi-\alpha^2}{\alpha\delta}+\frac{\alpha}{\delta} $$

Substituted in $a+b\overline{r}_p$:

$$ \omega_D=-\frac{\mathbf{V^-e}}{\delta}+\frac{\mathbf{V^-\overline{r}}}{\alpha}+(a+b)\frac{\alpha}{\delta}=-\frac{\mathbf{V^-e}}{\delta}+\frac{\mathbf{V^-\overline{r}}}{\alpha}+\frac{\mathbf{V^-e}}{\delta}=\frac{\mathbf{V^-\overline{r}}}{\alpha}$$

That is the tangency portofolio. If $\overline{r}_q>0$, $\overline{r}_q$ can be interpreted as risk-free asset return in [next chapter](#beta-representation)

# Risk-free asset

Suppose we have a riskless asset with return $r_f$, and we  assign $\omega_0$ weight on it. Then the portfolio choice problem becomes

$$ \min_{\omega,\omega_0} \frac{1}{2}\omega'\mathbf{V}\omega \quad s.t. \quad \mathbf{e'\omega}+\omega_0=1, \mathbf{\omega'\overline{r}}+\omega_0 r_f=\overline{r}_p $$

substitute $\omega_0=1-\mathbf{e'\omega}$, then

$$ \mathbf{\omega'\overline{r}}+ (1-\mathbf{e'\omega})r_f=\overline{r}_p\implies \omega'(\mathbf{\overline{r}}-r_f\mathbf{e})+r_f=\overline{r}_p $$

The problem is 

$$ \min_{\omega,\omega_0} \frac{1}{2}\omega'\mathbf{V}\omega \quad s.t.\quad \omega'(\mathbf{\overline{r}}-r_f\mathbf{e})+r_f=\overline{r}_p $$

Again by the Lagrangian:

$$ L=\frac{1}{2}\omega'\mathbf{V}\omega+\lambda(\overline{r}_p-\omega'(\mathbf{\overline{r}}-r_f\mathbf{e})-r_f) $$

$$ \frac{\partial L}{\partial\omega}=\mathbf{V}\omega-\lambda(\mathbf{\overline{r}}-r_f\mathbf{e})=0\implies \omega^*=\lambda\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e}) $$

$$ \overline{r}_p-{\omega^{*}}'(\mathbf{\overline{r}}-r_f\mathbf{e})-r_f=0\implies\lambda=\frac{\overline{r}_p-r_f}{(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})} $$

$$ \sigma_p^2=\omega'\mathbf{V}\omega= \lambda^2(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-\mathbf{V}\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})=\frac{(\overline{r}_p-r_f)^2}{(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})}$$

In geometry view, the frontier degenerate into two crossing line:

$$ \overline{r}_p=r_f\pm \sqrt{(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})}\sigma_p $$

## One Fund Theorem

Substitue $\lambda$ in the expression of $\omega^*$:

$$ \omega^*= \frac{(\overline{r}_p-r_f)}{(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})}\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})$$

We denote $c=\frac{(\overline{r}_p-r_f)}{(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})}$(since it's a scalar) and $\tilde{\omega}=\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})$ then we can write

$$ \omega^*=c\tilde{\omega} $$

That is so called one fund theorem

> When $r_f\ne r_{mv}$ any minimal-variance frontier portfolio is a combination of the tangency portfolio (with risk assets only) and the riskless asset

Normalized $\tilde{\omega}$($\frac{\tilde{\omega}}{\mathbf{e'}\tilde{\omega}}$) is the tangecy portfolio, i.e. $\omega_D=\frac{\tilde{\omega}}{\mathbf{e'}\tilde{\omega}}$, the reason is showing below.

Now we prove the degenerated frontier is tangent to the the origin frontier, that is, the hyperbola $\frac{\sigma_p^2}{1/\delta}-\frac{({\overline{r}_p-\frac{\alpha}{\delta}})^2}{(\delta\xi-\alpha^2)/\delta^2}=1$. Assume they do tangent and the tangent point is $(\sigma_p,\overline{r}_p)$ 

Recall the polar of $(x_0,y_0)$ w.r.t. $\frac{x^2}{a^2}-\frac{y^2}{b^2}=1$ is $\frac{x_0x}{a^2}-\frac{y_0y}{b^2}=1$ and the slope is 
$$ \frac{b^2x_0}{a^2y_0}=\sqrt{\frac{b^4x_0^2}{a^4y_0^2}}=\sqrt{\frac{b^2(a^2b^2+a^2y_0^2)}{a^4y_0^2}} $$
Then since the tangent line through $(0,r_f)$:

$$ \begin{aligned}
  -\frac{({\overline{r}_p-\frac{\alpha}{\delta}})(r_f-\frac{\alpha}{\delta})}{\Delta/\delta^2}=1
\end{aligned} $$

solved for $\overline{r}_p$:

$$ \overline{r}_p=\frac{-\alpha^2+r_f\alpha\delta-\Delta}{\delta(-\alpha+r_f\delta)}=\frac{\xi-r_f\alpha}{\alpha-r_f\delta} $$

the square of slope is

$$
\begin{aligned}
  \frac{\Delta  \left(\frac{\Delta }{\delta ^3}+\frac{\left({y_0}-\frac{\alpha }{\delta }\right)^2}{\delta }\right)}{\left(y_0-\frac{\alpha }{\delta }\right)^2}&=\frac{\Delta  \left(\alpha ^2+\Delta +\delta ^2 y_0^2-2 \alpha  \delta  y_0\right)}{\delta  (\alpha -\delta  y_0^2}
  \\&=\frac{\Delta  \left(\alpha ^2+\Delta -\frac{2 \alpha  \left(-\alpha ^2-\Delta +\alpha  \delta  r_f\right)}{\delta  r_f-\alpha }+\frac{\left(-\alpha ^2-\Delta +\alpha  \delta  r_f\right)^2}{(\delta  r_f-\alpha )^2}\right)}{\delta  \left(\alpha -\frac{-\alpha ^2-\Delta +\alpha  \delta  r_f}{\delta  r_f-\alpha }\right)^2}
  \\&=\frac{\alpha ^2+\Delta +\delta ^2 r_f^2-2 \alpha  \delta  r_f}{\delta }
  \\&=\xi+\delta r_f^2-2\alpha r_f
\end{aligned}
$$

Which is equal to

$$ (\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})=\xi+\delta r_f^2-2\alpha r_f $$

Hence our assumption is correct. Consider the tangency portfolio:

$$ \overline{r}_p=\frac{\xi-r_f\alpha}{\alpha-r_f\delta}=\frac{\Delta/\delta^2}{r_{mv}-r_f}+r_{mv} $$

If $r_f=\frac{\alpha}{\delta}=r_{mv}$, the tangency doesn't exist and the frontier becomes asymptotes. If $r_f> r_{mv}$, the tangency is in the lower straight line and vice versa.

The weight is

$$ \omega^*=a+b\overline{r}_p=\frac{\mathbf{V^-}(\overline{\mathbf{r}}-r_f\mathbf{e})}{\alpha-\delta r_f}=\frac{\mathbf{V^-}(\overline{\mathbf{r}}-r_f\mathbf{e})}{\mathbf{e'V^-}(\overline{\mathbf{r}}-r_f\mathbf{e})}=\frac{\tilde{\omega}}{\mathbf{e}'\tilde{\omega}} $$

That is why we called $\tilde{\omega}$ tangency portfolio. Recall the result in [zero covariance](#zero-covariance), for any portofolio $\overline{r}_p>r_{mv}$, we can find $r_f=\overline{r}_q$ with zero covariance with $\overline{r}_p$ to make $\overline{r}_p$ be a tangency portfolio.

## Sharpe ratio

The shrpe ratio is defined by

$$S_p=\frac{\overline{r}_p-r_f}{\sigma_p} = \frac{\omega'(\mathbf{\overline{r}}-r_f\mathbf{e})}{\sqrt{\omega'\mathbf{V}\omega}} $$

Which can be interpreted as a measure of **expected excess return per unit of risk**.

To maximize $S_p$, suppose

$$ \frac{\partial S_p}{\partial \omega}=0 $$

Let $\mathbf{r}=\mathbf{\overline{r}}-r_f\mathbf{e}$

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

$$   \omega'\mathbf{V}\omega \mathbf{r}-\omega'\mathbf{r}\mathbf{V}\omega=\mathbf{0}\implies\omega=\frac{ \omega'\mathbf{V}\omega }{\omega'\mathbf{r}}\mathbf{V^-r}$$

Note the scale of $\omega$ is independent to $S_p$. If we assume $\mathbf{e'\omega}=1$ additionally, then 

$$ \omega=\frac{\mathbf{V^-r}}{\mathbf{e'V^-r}}=\frac{\mathbf{V^-}(\overline{\mathbf{r}}-r_f\mathbf{e})}{\mathbf{e'V^-}(\overline{\mathbf{r}}-r_f\mathbf{e})}=\frac{\tilde{\omega}}{\mathbf{e}'\tilde{\omega}}=\omega_D $$

**Remark**

1. The maximun sharpe ratio is the slope of frontier $\sqrt{(\mathbf{\overline{r}}-r_f\mathbf{e})'\mathbf{V}^-(\mathbf{\overline{r}}-r_f\mathbf{e})}$.

2. $\omega_D$ is the only maxima on the frontier without risk-free asset. However, every portfolio on the frontier with a risk-free asset has the maximal sharpe ratio by one fund theorem($\omega^*=c\tilde{\omega}$) if $r_f>r_{mv}$. (Otherwise $\omega_D$ is on the lower straight line and become a minima).

## Indifference curve

If the utility function of investor is negative exponential, then the optimal portfolio is still tangency portfolio. Suppose its utility is

$$ U(W)=-e^{-bW} $$

and initial wealth is $1$, we assume the return is normally distributed. Then

$$ W=r_p=(1-\mathbf{e'\omega})r_f+\omega'\mathbf{r}=r_f+\omega'\mathbf{r} $$

To maximize its utility expection 

$$ \begin{aligned}
  E[U(W)]=E[U(r_p)]=E[-e^{-b(r_f+\omega'\mathbf{r})}]
\end{aligned} $$

where $\mathbf{r}={\mathbf{\tilde{r}}}-r_f\mathbf{e}\sim N(\mathbf{\overline{r}}-r_f\mathbf{e},\mathbf{V})$. It's sufficent to maximize

$$ E[e^{(-b\omega)'\mathbf{r}}]=\exp\{(-b\omega)'E(\mathbf{{r}})+b^2\omega'\mathbf{V}\omega/2\} $$

then

$$ \frac{\partial(-b\omega)'E(\mathbf{{r}})+b^2\omega'\mathbf{V}\omega/2  }{\partial\omega}=-bE(\mathbf{{r}})+b^2\mathbf{V\omega}=0 $$

hence

$$ \omega=\frac{\mathbf{V^-}E(\mathbf{{r}})}{b}=\frac{\mathbf{V^-}(\mathbf{\overline{r}}-r_f\mathbf{e})}{b}$$

# CAPM

## Beta representation

Recall the tangency portfolio is $\omega_D=\frac{\mathbf{V^-}(\overline{\mathbf{r}}-r_f\mathbf{e})}{\mathbf{e'V^-}(\overline{\mathbf{r}}-r_f\mathbf{e})}$. Write $\omega_D=m \mathbf{V^-} (\overline{\mathbf{r}}-r_f\mathbf{e})$ where $m=\frac{1}{\mathbf{e'}\mathbf{V^-} (\overline{\mathbf{r}}-r_f\mathbf{e})}$, then we have

$$ \overline{r}-r_f\mathbf{e}=\frac{1}{m}\mathbf{V}\omega_D $$

Note $\text{Cov}(\mathbf{r},\omega'\mathbf{r})=\mathbf{V\omega}$ and

$$ \sigma_D^2=\omega_D'\mathbf{V}\omega_D=m\omega'_D(\overline{\mathbf{r}}-r_f\mathbf{e})= mr_D-mr_f $$

we have

$$ \overline{\mathbf{r}}-r_f\mathbf{e}=\frac{r_D-r_f}{\sigma_D^2}\text{Cov}(\mathbf{r},{r_D}) $$

Denote $\frac{\text{Cov}(\mathbf{r},{r_D})}{\sigma_D^2}=\beta_D$, we have

$$ \overline{\mathbf{r}}-r_f\mathbf{e}=\beta_D({r_D-r_f}) $$

Similar results also holds for any portfolio $\overline{r}_p$ in the MVF:

$$ \overline{\mathbf{r}}-\overline{r}_q\mathbf{e}=\beta_p(\overline{r}_p-\overline{r}_q) $$

It's clear in the view of every portfolio $\overline{r}_p$ is also a tangency portfolio by selecting proper $r_f$. One can also check it in a dirty way:

**Proof** Suppose $r_p$ and $r_q$ both in the MVF without risk-free asset, recall

$$ \begin{aligned}
  \omega_p'\mathbf{V}\omega_q=\frac{1}{\delta}+\frac{\delta(\overline{r}_p-\frac{\alpha}{\delta})(\overline{r}_q-\frac{\alpha}{\delta})}{\delta\xi-\alpha^2}
\end{aligned} $$

If the covariance is $0$, we have

$$ \overline{r}_q=\frac{\alpha}{\delta}-\frac{\delta\xi-\alpha^2}{\delta^2(\overline{r}_p-\alpha/\delta)} $$

Then

$$ \begin{aligned}
  \mathbf{\overline{r}}-\overline{r}_q \mathbf{e}&=\mathbf{\overline{r}}-(\frac{\alpha}{\delta}-\frac{\delta\xi-\alpha^2}{\delta^2(\overline{r}_p-\alpha/\delta)})\mathbf{e}
  \\&=\frac{1}{\delta^2(\overline{r}_p-\alpha/\delta)}(\delta^2(\overline{r}_p-\alpha/\delta))(\mathbf{\overline{r}}-(\frac{\alpha}{\delta}-\frac{\delta\xi-\alpha^2}{\delta^2(\overline{r}_p-\alpha/\delta)})\mathbf{e})
  \\&=\frac{1}{\delta^2(\overline{r}_p-\alpha/\delta)}(\mathbf{\overline{r}}(\delta^2(\overline{r}_p-\alpha/\delta))-(\alpha\delta(\overline{r}_p-\alpha/\delta)-(\delta\xi-\alpha^2))\mathbf{e})
  \\&=\frac{1}{\delta^2(\overline{r}_p-\alpha/\delta)}(\mathbf{\overline{r}}(\delta^2(\overline{r}_p-\alpha/\delta))-(\alpha\delta\overline{r}_p-\delta\xi)\mathbf{e}
  \\&=\frac{
    (\delta^2\overline{r}_p\mathbf{\overline{r}}-\alpha\delta\mathbf{\overline{r}})-(\alpha\delta\overline{r}_p-\delta\xi)\mathbf{e}}
  {\delta^2(\overline{r}_p-\alpha/\delta)}
  \\&=\frac{
    (\delta\overline{r}_p-\alpha)\mathbf{\overline{r}}-(\alpha\overline{r}_p-\xi)\mathbf{e}}
  {\delta(\overline{r}_p-\alpha/\delta)}
\end{aligned} $$

On the other hand:

$$ \begin{aligned}
  \beta_p&=\frac{\mathbf{V\omega_p}}{\omega_p'\mathbf{V}\omega_p}
  \\&=\frac{1}{\omega_p'\mathbf{V}\omega_p}(\lambda_p\overline{\mathbf{r}}+\gamma \mathbf{e})
  \\&=\frac{1}{\omega_p'\mathbf{V}\omega_p}(\frac{\mathbf{\xi e-\alpha  \overline{r}}}{\delta\xi-\alpha^2}+\frac{\mathbf{-\alpha e+\delta\overline{r}}}{\delta\xi-\alpha^2}\overline{r}_p)
  \\&=\frac{1}{\omega_p'\mathbf{V}\omega_p}(\frac{ (\delta\overline{r}_p-\alpha)\mathbf{\overline{r}}-(\alpha\overline{r}_p-\xi)\mathbf{e}}{\Delta})
\end{aligned} $$

Then it's remain to show that

$$ (\overline{r}_p-\overline{r}_q)\delta(\overline{r}_p-\alpha/\delta)=\omega'\mathbf{V}\omega\Delta $$

It's clear since

$$ \omega'\mathbf{V}\omega \Delta=\sigma_p^2\Delta=\frac{\Delta}{\delta}+\delta(\overline{r}_p-\frac{\alpha}{\delta})^2 $$

and

$$ \begin{aligned}
  (\overline{r}_p-\overline{r}_q)\delta(\overline{r}_p-\alpha/\delta)&=
  ((\overline{r}_p-\frac{\alpha}{\delta})+\frac{\delta\xi-\alpha^2}{\delta^2(\overline{r}_p-\alpha/\delta)})\delta(\overline{r}_p-\alpha/\delta)
  \\&=\frac{\Delta}{\delta}+\delta(\overline{r}_p-\frac{\alpha}{\delta})^2. \blacksquare
\end{aligned} $$

## CAPM

In capital market equilibrium, the market portfolio is tangecy portfolio $r_D={r}_m$, then 

$$ \overline{\mathbf{r}}-r_f\mathbf{e}=\beta_m({{r}_m-r_f}) $$

where 

$$ \beta_m=\begin{bmatrix}
  \frac{\text{Cov}(r_1,r_m)}{\sigma^2_m}\\
  \frac{\text{Cov}(r_2,r_m)}{\sigma^2_m}\\
  \cdots\\
  \frac{\text{Cov}(r_n,r_m)}{\sigma^2_m}\\
\end{bmatrix} $$

this equation is called **Sharpe-Lintner CAPM**. $r_m-r_f$ is called **market risk premium** and $\frac{r_m-r_f}{\sigma_m}$ is called **market sharpe ratio**. Translate it from vector form, we get the **Security Market Line**:

$$ r_i-r_f=\frac{\text{Cov}(r_i,r_m)}{\sigma_m^2}(r_m-r_f)=\beta_{i,m}(r_m-r_f) 
$$

## Variance decomposition

Now consider both $r_i$ and $r_m$ is random variable, let $\epsilon$ be a random vector with zero expection and zero covariance with $r_i$ and $r_m$, then

$$ {\mathbf{r}}-r_f\mathbf{e}=({{r}_m-r_f})\beta_m+\mathbf{\epsilon} $$

thus

$$ \begin{aligned}
  \text{Var}(\mathbf{r})&=\text{Var}(\mathbf{r}-r_f\mathbf{e})
  \\&=\text{Var}(\beta_m(r_m-r_f))+\text{Var}(\epsilon)
  \\&=\text{Var}(r_m\beta_m)+\text{Var}(\epsilon)
  \\&=\beta_m\beta_m'\sigma_m^2+\text{Var}(\epsilon)
\end{aligned} $$

Split in






















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