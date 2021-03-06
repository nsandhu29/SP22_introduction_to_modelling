# the k-Nearest Neighbor, or KNN model
[source to learn](https://web.archive.org/web/20200121091131/http://www.statsoft.com/Textbook/k-Nearest-Neighbors)

In this lesson, we'll talk about a simple model for solving classification problems  which can easily deal with cases in which there are more than two classes. This model is called the k-Nearest Neighbor, or KNN model, and the basic idea is simple. Suppose we have a data set with two predictors and a response. 

![knearest1](images/2022/02/Knearest.png)

For example, a bank might be trying to decide whether or not to give loans to applicants based on the applicant's credit scores and incomes. We can plot all the information on a graph where the horizontal axis shows credit score, the vertical axis shows household income, and each previous applicant is either a green data point if they repaid their entire loan, or a red data point if they defaulted. Instead of trying to draw a line or other function to separate the red points from the green points, we can use a different approach. Assume that each new applicant is similar to previous applicants that it's closest to. For example, if we look at the five closest points to this new one, four of them are green, and only one is red. So, we might assume that the new data point is more likely to be green, and recommend giving that person a new loan. As you might expect, there's nothing magical about using the five closest points.
We can pick any number of points to use. Usually the number of points we're using is denoted by k, which is where the name k-Nearest Neighbor comes from.

![knearest](images/2022/02/knearest1.png)

This works easily, not just for two classes, but also for more. In this example, each color is a different class. Let's say k is seven.
When a new point is found, we look at the seven closest points and pick the color that appears the most. In this example, there are two orange points, one green point, and four red points. Red appears the most, so we classify this new point as red. So, that's pretty straightforward, but there are some complexities you should be aware of.

- First, when we're looking for the k closest points, there's more than one way to measure distance. The most common method is to use straight line distance, $\sqrt[2]{\sum_{i=1}^n\lvert x_i - y_i\rvert^2}$ but there are others as well. **Distance Matrix**
- A second complexity is that some attributes might be more important than others to the classification. One way to deal with this is to weight each dimension's distance differently. $\sqrt[2]{\sum_{i=1}^nw_i\lvert x_i - y_i\rvert^2}$The larger the weight, the greater the impact of that dimension's distance. Finding the right weights can be harder and might require techniques such as Regression, for example. In the extreme case, some attributes might not be very important at all for classification. So much so, that we can remove those attributes and only measure distance in the important ones.
- Finally, **how to find the right value of k?**.How many closest points should you check when trying to classify a new point? We have to try different values of k and measure how well each value of k works. **Measuring the quality of a model is called validation**
