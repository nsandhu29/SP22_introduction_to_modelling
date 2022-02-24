# Scaling And Standardization

In this lesson we'll see two common data preparation tasks, scaling and standardization, and some situations where it's important to use one or the other.

Let's start off with a situation where scaling is important. Think back to the support vector machine, or SVM model for classification.

Here, we're trying to classify loan applicants into good and bad credit risks, using two predictive factors. Household income, which is usually in the tens of thousands or more, and credit score which is in the hundreds. The basic SVM idea was to find the pair of parallel lines that were farthest apart while keeping all red points on one side of the lines and all green points on the other side of the lines. The classifier would then be right in the middle of those two lines.

Model:

- Given data $\{x_{ij}\}$ where $x_{ij}$ is the $j^{th}$ factor of data point $i$
- The classifier is line $0= a_0 + \sum_{j}a_j.x_j$
- Maximize gap by minimizing $\sum_j(a_j)^2$
- $0 = 700,000 + 37.8\, X \,Income + 700\, X\,CreditScore$


It's hard to tell because there aren't any units shown on the graph,but a reasonable set of coefficients might be something like five times income and 700 times credit score.

- Sum of squared coefficents $\sum_j(a_j)^2 = 5^2 + 700^2 = 490,025$

But what if we make a small change to the credit score coefficient. Suppose we tried the coefficients five times income plus 701 times credit score. That looks like a very small change in the credit score coefficient less than one percent difference, and it's a very small change in the slope of the line. But the sum of squared coefficients is now five squared plus 701 squared, or 491,426, a change of 1401 from before.

- New Sum  $\sum_j(a_j)^2 = 5^2 + 701^2 = 491,426$ (higher by 1401)

**How much would we need to change the income coeffecient to get the same level of change?** If we keep the credit score coefficient at 700,the income coefficient would have to go all the way up from five to about 37.8, a change of more than 600% and a huge change in the line.

- Third Sum $\sum_j(a_j)^2 = 37.8^2 + 700^2 \cong 491,426$
  - Require large difference in first coefficent
  - Line is very different from first two

Because the data are at such different scales,the coefficients are also of different scales,which means that the sum of squared oefficients is much more sensitive to changes in one coefficient than the other.And that means our SVM model isn't going to work well,as we can see from the graph.We first need to adjust the data so the numbers are on the same scale.

The first way to adjust the data is to scale it down to the same interval.For example, suppose we want all of our data to be between zero and one.

## Adjust the data - Scaling

For each factor $j$, we set $x_{minj}$ and $x_{maxj}$ to be the smallest and largest factor values and then for each point $i$, its new scaled factor value, $x_{ij}$ scaled is just $x_{ij}$ minus $x_{minj}$ divided by $x_{maxj}$ minus $x_{minj}$. If we want to scale to some other range, say from $a\; to\; b$, then we just take our zero one scale value multiply by a minus b and add b.

Common Scaling: data between 0 and 1
Scale factor by factor

- let $x_{minj}  = min_{i}x_{ij}$
- let $x_{maxj}  = max_{i}x_{ij}$
- For each data point i:
  - $x_{ij}^{scaled} = \frac{x_{ij} -x_{minj}}{x_{maxj} -x_{minj}} $

- General Scaling $x_{ij}^{scaled[b,a]} = x_{ij}^{scaled[0,1]}(a - b) + b$

## Adjust the data - Standardizing
So that's how to scale linearly but we might also want to scale to a normal distribution, to measure how far from the mean each data point is. The most common way to do that is to scale to a mean of
zero and a standard deviation of one, the standard normal. That's also pretty straightforward. If we let new $j$ be the mean of factor j's values, and sigma j be the standard deviation of factor j's values,then for each data point i, xij standardized, is just $x_{ij}$ minus $\mu_j$ divided by $\sigma_j$.
- Scaling to a normal distribution
  - Common scaling mean = 0, standard deviation = 1
  - Factor $j$ has mean $\mu_{j} = = \frac{\sum_{i=1}^{n}.x_{ij}}{n}$
  - Factor $j$ has standard deviation $\sigma_j$
  - For each data point $i$:
    - $x_{ij}^{standardized} = \frac{x_{ij}- \mu_j}{\sigma_j}$
  
For some models it's important that your data be within a bounded range.Scaling can do that but standardization can't.Some examples where the bounded range is important, are things like neural networks, that often require inputs to be between zero and one, and optimization models that might require data to be bounded to ensure feasibility. It also might be that the type of data itself has to be within a certain range. For example, batting averages in baseball are between zero and one. RGB color intensities are between zero and 255. SAT scores are between 200 and 800, et cetera. On the other hand, some models seem to work better with standardization. Principal component analysis and clustering are two examples and in many cases, it's not clear whether one is better than the other, sometimes you just have to try both and see what works best. Either way, the important thing is that it's often necessary to scale or standardize the input data.