Let's say there are n distinct coupons -
$1,2,3,...,n$
so that when you collect all $n$ of these coupons, you get a Prize
Each cereal box has exactly one coupon
Each coupon is equally likely to be in a cereal box

In expectation, # cereal boxes that we need to buy until we get all coupons?

$X$: random variable denoting # cereal boxes that one buys to get all coupons ($1,2,3,...,n$)
$X_i$: # cereal boxes that we need to buy to go from having $(i-1)$ distinct coupons to having $i$ distinct coupons
(i.e:
$3,4,3,3,4,3,1,2$
$X_1=1$
$X_{2}=1$
$X_{3}=5$
$X_{4}=1$
$X=\sum\limits_{i=1}^{n}X_i$
By LOE,
$E[X] = \sum\limits_{i=1}^{n}E[X_i]$
$X_i$ is a geometric random variable with a parameter $\frac{n-(i-1)}{n}$

$E[X] = \sum\limits_{i=1}^{n}\frac{n}{n-i+1}$
$=\frac{n}{n}+\frac{n}{n-1}+\frac{n}{n-2}+...+{n}{1}$
$=n(\frac{1}{n} + \frac{1}{n-1}+...+\frac{1}{1})$
$=nHn \approx n\ln{n}$

