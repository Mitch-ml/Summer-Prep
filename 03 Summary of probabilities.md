<!---
The math equations from LaTeX were not working so I used 
http://www.sciweavers.org/free-online-latex-equation-editor
To paste the code in and copied the image adress, which seems
to have worked.
--->

**Bernoulli Distributions:** There are only two outcomes, true or false, and the probability associated with each outcome is p and 1-p respectively. Note that these are single events, i.e. flipping a coin *once*.

**Binomial Distributions:** A sequence of multiple Bernoulli trials. i.e. flipping a coin multiple times and counting the number of heads. 

**Expectation:** The mean. But in more general settings it's the weighted average of all possible outcomes of X i.e. 

![$$\mathbb{E}(X) = \sum\limits_{\forall x} x\mathbb{P}(X=x)$$](http://www.sciweavers.org/upload/Tex2Img_1617113137/eqn.png)

We can transform random variables and still calculate the expected value nicely.

Distributive: ![$$\mathbb{E}(aX+b) = a\mathbb{E} + b$$](http://www.sciweavers.org/upload/Tex2Img_1617113373/eqn.png)

Additivity: ![$$\mathbb{E}(X + Y) = \mathbb{E}(X) + \mathbb{E}(Y)$$](http://www.sciweavers.org/upload/Tex2Img_1617113443/eqn.png)

**Variance:** How much do you expect the sample to differ from the population. Alternatively, how far away from the expectation can X be, just by chance?

Transformations of variance: 

![$$\mathbb{V}ar(aX+b) = a^2\mathbb{V}ar(X)$$](http://www.sciweavers.org/upload/Tex2Img_1617113497/eqn.png)

**Standard Deviation:** Scales the variance ![$$\sigma = \sqrt{\mathbb{V}ar(X)}$$](http://www.sciweavers.org/upload/Tex2Img_1617113549/eqn.png)

**Covariance/Correlation** Covariance indicates the direction of a linear relationship between variables. Correlation measures both the strength and direction. Correlation is just a standardized version of the covariance.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/Covariance_trends.svg/170px-Covariance_trends.svg.png)

Important note: Independent random variables are uncorrelated. **However**, not all uncorrelated random variables are independent. 

**Standardization:** ![$$z = \frac{X-\mathbb{E}(X)}{\mathbb{SD}(X)} = \frac{X-\mu}{\sigma}$$](http://www.sciweavers.org/upload/Tex2Img_1617113675/eqn.png)

**Central Limit Theorem:** Most things tend to be normally distributed. 
