![](https://lh3.googleusercontent.com/proxy/wCgMz8nClgFY_eDrQyjBR5D4A6Zyk8kNnMTr1aXN-RB1Hz3df3Qh8LVGKLlqbNJPmCG6rKQclAA4q9aT0eOMOJ8QPN1rdizzdx_DZpdnJgFCliBHqVa2VRw2IwGcxenQaZpudlKTJEt0gl3kncpcf1H5tOTvZZtgog)

- What is the real world problem? 
- Where are you going to get that data?
- How should the data actually look like?
- What patterns and trends do you notice at first glance?
- If you don't have the necessary features you will need to create your own.
- Build the model
- Visualize the data and share it with others
- Assess the impact results have on the real world

1. **Question/Problem formulation:**
	1. What do we want to know or what problems do we want to solve?
	2. What are our hypothesis?
	3. What are our metrics of success?
2. **Data Acquisition and Cleaning:**
	1. What data do we have and what data do we need?
	2. How will we collect more data?
	3. How do we oganize the data for analysis?
3. **Exploratory Data Analysis:**
	1. Do we already have relevant data?
	2. What are the biases, anomalies, or other issues with the data?
	3. How do we transform the dta to enable effective analysis?
4. **Prediction and Inference:**
	1. What does the data say about the world?
	2. Does it answer our questions or accurately solve the problem?
	3. How robust are our conclusions?



### Sampling bias
Sampling is different than looking at an entire population, and it's important to be aware of how certain data collecting methods may be systematically undercounting certain minority groups. For example: looking at the population of the U.S. through tax records will exclude people who don't file taxes i.e. people under 18 and undocumented workers. 

Sampling looks at a subset of the population and makes inferences about the whole population. Sampling has it's own systematic biases that should also be noted.

![](https://fourpillarfreedom.com/wp-content/uploads/2019/05/nonResponseBias.jpg)

In general we want our samples to be representative of our populations, however, there are instances where we might want them to be different.  For example, if we want to hear more perspectives from minority groups, we might intentionally rebalance our sample. At the end of the day, it's important to recognize how your sample compares to the overall population and the implications that has on the questions you're trying to answer. 

**Self-Selection bias:** or volunteer bias. If you go to a population and ask people to take part in a survey, the people who respond will not represent the population. They're the type of people who want to respond to a survey which tends to be associated with many confounding factors.

**Exclusion bias:** If you're looking at history from families that have been in Vermont for 20+ years, you're systematically excluding  newer families that might have moved into the area, which might be different than the prior population.

**Pre-screening bias:** similar to exclusion bias, where there's potentail to systematically leave out certain groups of people. For example, if you were researching undergraduates and went to the dorms to survey students, you'd systematically be leaving out people who are continuing education perhaps from home, or who don't live in the dorms.  

**Survivorship bias:** Surviving sample is not representative of the population before the survivorship occured.  

**Convenience bias:** It's easier to sample people who are like you, or sample people whose data is more easily available. ***Just because data is easy to get does not mean it is the right data for your problem!***

### Confounding variables
![](https://ars.els-cdn.com/content/image/3-s2.0-B9780128142769000143-f14-02-9780128142769.jpg)

Just because you found a correlated link does not mean that it is a causal link. Always collaborate with experts who might have insights into why these features are correlated. 

**Spurious correlation**
![](https://miro.medium.com/max/8000/1*aewtqUE_6qin8LtXRaF-JQ.png)

Ice cream is obviously not causing more shark attacks, but warmer weather might increase ice cream sales, in addition to increasing the amount of time people spend in the ocean leading to more shark attacks.

**P-hacking** Given a large enough sample size, you're likely to see some relation between variables. However, that does not mean that the relationship actually exists. *The more attempts you make at trying to find a correlation, the more skeptical you should be when you actually find one.*

**Cluster sampling** Instead of trying to capture the entire populatin in one sample. Break the population in to clusters and sample from the subsets of the population. 

**Stratified sampling** break the population up into categories, and sample from each of the categories. For example age, gender, or ethnicity.

**Paired (matched) sampling** Try and match features between groups. 

### Sampling best practice
**Simple random sample** Choose randomly throughout your population. By doing this you're sampling the frequencies of the population. This assumes you have the full population and the ability to randomly sample from it.

["Burkley textbook"](http://www.textbook.ds100.org/intro.html)
["Textbook for advanced course"](https://www.inferentialthinking.com/chapters/01/what-is-data-science.html)
["Burkley homepage"](https://ds100.org/sp21/)
["Burkley lectures"](https://www.youtube.com/watch?v=JtwBwogRZkI&list=PLPHXc20GewP8J56CisONS_mFZWZAfa7jR&index=1)
