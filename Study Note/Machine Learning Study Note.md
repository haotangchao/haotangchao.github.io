# Machine Learning Study Note

1. **Machine Learning**：A computer programmer is said to learn from experience E with respect to some task T and some performance P,if its performance on T, as measured by P, improves with experience E.

2. **Supervised Learning**：In supervised learning, we are given a data set and already know what our correct output should look like,having an idea that there is a relationship between the input and output.Supervised learning problems are categorized into "regression" and "classification" problems.

3. **Unsupervised Learning**：Unsupervised learning allows us to approach problems with no or little idea what our results should look like.We can derive structure from the data where we don't necessarily know the effect of the variables.We can derive this structure by clustering the data based on relationships among the variables in the data.With unsupervised learning, there is no feedback based on the prediction results.

4. **Cost Function**：We can measure the accuracy of our hypothesis function by using a cost function.

5. **Normal Equation**：θ = (X'X)^(-1)X'y

   ​	In octave： `pinv(X'*X)*X*y'`

6. **Comparsion of Gradient Descent and Normal Equation**：

   * Normal Equation don't need choose α
   * Gradient Descent is O(kn^2) while Normal Equation is O(n^3)
   * If n (the number of features) is too big, you'd better choose Gradient Descent.

7. When X'X will be non-invertible？

   * Redundant features( linearly dependent ).
   * Too many features ( e.g. m <= n )


