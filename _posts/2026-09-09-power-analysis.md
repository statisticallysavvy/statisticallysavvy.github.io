# Power Analysis Done Properly

Completing a power analysis is something all statisticians and data scientists should be able to do, but is one of those things that is often overlooked in introductory courses. A power analysis will allow you to figure out one of the following things if you know the others:

* sample size
* power
* effect size
* variance

The important thing to understand is that these quantities are not independent of one another. Change one, and the others will have to change as well.

## What is power?

Statistical power is the probability that a statistical test will correctly reject the null hypothesis when the alternative hypothesis is actually true.

In other words, if there really is an effect, power tells us how likely we are to detect it.

For example, suppose we are testing whether a new treatment changes the mean outcome compared with a control group. If our test has 80% power, then under the assumptions of our power calculation, we would detect the specified effect in about 80% of repeated studies.

This is closely related to the concept of a **Type II error**. Type II errors are where we incorrectly fail to reject the null hypothesis. If β is the probability of failing to reject the null hypothesis when the alternative is true, then:

**Power = 1 − $\beta$**

So, a study with 80% power has a Type II error rate of 20%.

## The four ingredients

A useful way to think about power analysis is that we are balancing four quantities:

1. **Sample size** — how much data we collect.
2. **Effect size** — how large the effect we want to detect is.
3. **Power** — how likely we are to detect the effect.
4. **Variance** — how much natural variation there is in the measurements.

There is also usually a fifth ingredient hiding in the background: the **significance level**, $\alpha$.

Most commonly, $\alpha$ is set to 0.05. This determines how willing we are to have a Type I error — rejecting the null hypothesis when it is actually true.

Once $\alpha$ is fixed, the relationship between sample size, effect size, power, and variance becomes much clearer.


## The general power formula

For a two-independent-sample t-test, we can derive a general relationship between **sample size, power, effect size and variance**.

Assume two independent groups with equal sample sizes $n$, population means $\mu_1$ and $\mu_2$, and a common population variance $\sigma^2$.

We want to test

$$
H_0:\mu_1=\mu_2
$$

against the two-sided alternative

$$
H_1:\mu_1\neq\mu_2.
$$

Let the true difference between the population means be

$$
\Delta=\mu_1-\mu_2.
$$

The standard error of the difference between two independent sample means is:

$$
\mathrm{SE}(\bar{X}_1-\bar{X}_2)
$$

For equal-sized groups with a common variance, this becomes:

$$
\sqrt{\frac{\sigma^2}{n}+\frac{\sigma^2}{n}}
$$

which simplifies to:

$$
\sigma\sqrt{\frac{2}{n}}
$$

Under the alternative hypothesis, the expected value of the test statistic is therefore

$$
\frac{\Delta}{\sigma\sqrt{2/n}}.
$$

The test rejects the null hypothesis when the magnitude of the test statistic exceeds the critical value. Using the normal approximation, the critical value for a two-sided test at significance level $\alpha$ is

$$
z_{1-\alpha/2}.
$$

If we want power $1-\beta$, then the alternative distribution needs to be sufficiently separated from the null distribution that

$$
\frac{\Delta}{\sigma\sqrt{2/n}}
=z_{1-\alpha/2}+z_{1-\beta}.
$$

Rearranging gives the central equation:

$$
\boxed{
\Delta
=\sigma
\sqrt{\frac{2}{n}}
\left(
z_{1-\alpha/2}+z_{1-\beta}
\right)
}
$$

This equation links the four quantities we are interested in:

* **effect size:** $(\Delta)$
* **variance:** $(\sigma^2)$ (or standard deviation $\sigma$)
* **sample size:** $(n)$ per group
* **power:** $(1-\beta)$

The significance level $\alpha$ is also required and is usually specified in advance.

We can rearrange the same equation to solve for any one of these quantities.

### Sample size

Solving for $n$:

$$
\boxed{
n=
\frac{
2\sigma^2
\left(
z_{1-\alpha/2}+z_{1-\beta}
\right)^2
}{
\Delta^2
}
}
$$

### Effect size

Solving for $\Delta$:

$$
\boxed{
\Delta
=\sigma
\sqrt{\frac{2}{n}}
\left(
z_{1-\alpha/2}+z_{1-\beta}
\right)
}
$$

### Variance

Solving for $\sigma^2$:

$$
\boxed{
\sigma^2
=\frac{
n\Delta^2
}{
2\left(
z_{1-\alpha/2}+z_{1-\beta}
\right)^2
}
}
$$

### Power

Power can also be obtained by rearranging for $\beta$. Starting with

$$
\frac{\Delta}{\sigma\sqrt{2/n}}
=z_{1-\alpha/2}+z_{1-\beta},
$$

we obtain

$$
z_{1-\beta}=
\frac{\Delta\sqrt{n}}
{\sigma\sqrt{2}}
-z_{1-\alpha/2}.
$$

Therefore,

$$
\boxed{
\text{Power}
=\Phi\left(
\frac{\Delta\sqrt{n}}
{\sigma\sqrt{2}}
-z_{1-\alpha/2}
\right)
}
$$

where $\Phi$ is the cumulative distribution function of the standard normal distribution.

So, given any three of **sample size, effect size, variance and power**, we can use these equations to solve for the fourth.

This is the key idea behind power analysis. It isn't a collection of unrelated calculations for sample size, effect size and power. They are all different ways of solving the **same underlying relationship**.

## Suggestions

In the power calculation above, we assumed the same sample size for each group, and a common variance $\sigma^2$. Can you come up with a more general version of the formula that doesn't make this assumption?

Can you create a similar formula for a test of two proportions?
