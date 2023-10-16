#note 

Bayes estimator uses the whole posteriori distribution of $\theta$ but it is still desireable to have a single estimated point. So the Maximum posteriori estimator(MAP) finds the $\theta$ value that maximizes the posteriori probability.

$$
\begin{align*}
\theta_{MAP} &= \underset{\theta}{argmax} \ p(\theta | X) \\
&= \underset{\theta}{argmax} \ p(X | \theta) \ p(\theta)
\end{align*}
$$
