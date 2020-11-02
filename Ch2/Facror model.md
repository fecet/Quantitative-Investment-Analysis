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

$$ 
r_i-r_f=\beta_{i,m}(r_m-r_f) 
$$

### Realized return

Now consider both $r_i$ and $r_m$ is random variable, let $\epsilon$ be a random vector with zero expection and zero covariance with $r_i$ and $r_m$, then

$$ 
r_i-r_f=\beta_{i,m}(r_m-r_f)+\epsilon_i
$$

This is a regression equation, if one include an intercept, then the model

$$ 
r_i-r_f=\alpha_i+\beta_{i,m}(r_m-r_f)+\epsilon_i
$$

is called **market model**, such $\alpha$ is called **Jensen's alpha**.

### Variance decomposition

Decomposition the variance as:

$$ \text{Var}(r_i)=\overbrace{\underbrace{\beta_i\sigma_m^2}_{\text{Systematic risk}}+\underbrace{\text{Var}(\epsilon_i)}_{\text{Idiosyncratic risk}}}^{\text{total risk}} $$

The $R^2$ is just the proportion of systematic risk

$$ R^2=\frac{\beta_i^2\sigma_m^2}{\beta_i^2\sigma_m^2+\sigma^2} $$

since [Fraction of variance unexplained](https://en.wikipedia.org/wiki/Fraction_of_variance_unexplained).


### Testing CAPM

Suppose we run time series regressions for each of the $n$ risky assets

$$ \mathbf{r_t^e=\alpha}+{\beta r_{m,t}^e+\nu_t} $$

where $\alpha,\mathbf{r_t^e},\beta,\nu_t$ are $n\times 1$ vector and  $r_{m,t}^e$ is scalar.

By the discussion above, $\alpha=\mathbf{0}$ when CAPM holds. Assume $\{\nu_t\}_{t=1}^T$ i.i.d with $N(0,\Sigma)$, we have $\mathbf{r_t^e}\mid r_{m,t}^e\sim N(\alpha+\beta r_{m,t}^e,\Sigma)$. 

Hence the p.d.f is

$$f(\mathbf{r}_t^e)= ( 2 \pi ) ^ { - n / 2 } | \Sigma | ^ { - \frac { 1 } { 2 } } \exp \left\{ - \frac { 1 } { 2 } ( \mathbf { r_t^e } - \alpha-\beta r_{m,t}^e)' \Sigma ^ { - 1 } ( \mathbf { r_t^e } - \alpha-\beta r_{m,t}^e)  \right\} $$

By the indepedence, from $t=1$ to $t=T$, the joint p.d.f is $L=\prod_{t=1}^Tf(\mathbf{r}_t^e)=$.

$$ \log L= \sum_{t=1}^T \log f(\mathbf{r_t^e})= -\frac{-n T}{2}\ln(2\pi)-\frac{T}{2}\ln |\Sigma|-\frac{1}{2}\sum_{t=1}^T (\mathbf { r_t^e } - \alpha-\beta r_{m,t}^e)' \Sigma ^ { - 1 } ( \mathbf { r_t^e } - \alpha-\beta r_{m,t}^e) $$

MLE for $(\alpha,\beta,\Sigma)$ is found by maximize $\log L$, W.r.t. $\beta$, it's the same as minimize 

$$ \sum_{t=1}^T (\mathbf { r_t^e } - \alpha-\beta r_{m,t}^e)' \Sigma ^ { - 1 } ( \mathbf { r_t^e } - \alpha-\beta r_{m,t}^e) $$

The FOC:

$$ \begin{aligned}
  \frac{\partial \log L}{\partial \beta}&=\sum_{t=1}^T (\mathbf { r_t^e } - \alpha-\beta r_{m,t}^e)' \Sigma ^ { - 1 } ( \mathbf { r_t^e } - \alpha-\beta r_{m,t}^e)
  \\&=\sum_{t=1}^T \frac{\partial (\mathbf { r_t^e } - \alpha-\beta r_{m,t}^e)' \Sigma ^ { - 1 } ( \mathbf { r_t^e } - \alpha-\beta r_{m,t}^e)}{\partial \beta}
  \\&=\sum_{t=1}^T\tr \frac{\partial (\mathbf { r_t^e } - \alpha-\beta r_{m,t}^e)' \Sigma ^ { - 1 } ( \mathbf { r_t^e } - \alpha-\beta r_{m,t}^e)}{\partial \mathbf { r_t^e } - \alpha-\beta r_{m,t}^e} \frac{\partial \mathbf { r_t^e } - \alpha-\beta r_{m,t}^e}{\partial \beta}
\end{aligned} $$














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
