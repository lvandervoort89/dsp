[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

**Exercise 2.4 Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. Compute Cohen’s d to quantify the difference between the groups. How does it compare to the difference in pregnancy length?**

When comparing the mean weight of babies (in pounds) for first and other babies, the mean weight of babies for the first pregnancy is 7.20 pounds and the mean weight of babies for other pregnancies is 7.33 pounds. First babies, on average, are 0.12 pounds lighter than other pregnancies.

<code>Python
    import numpy as np
    import nsfg
    
    preg = nsfg.ReadFemPreg()
    
    first_totalwgt = firsts['totalwgt_lb']mean()
    other_totalwgt = others['totalwgt_lb']mean()
    difference = first_totalwgt - other_totalwgt
</code>

When taking effect size into account, the Cohen's d between the two groups is -0.09. This means that the effect size is a trivial amount. The negative effect size indicates that the other babies group has a higher mean than the first babies group, meaning that other babies are heavier at birth. 

<code>Python
    def myCohenEffectSize(group1, group2):
    difference_in_means = group1.mean() - group2.mean()
    group1_variance = group1.var()
    group2_variance = group2.var()
    sample_size_group1 = len(group1)
    sample_size_group2 = len(group2)

    pooled_variance = (sample_size_group1 * group1_variance + sample_size_group2 * group2_variance) / 
                      (sample_size_group1 + sample_size_group2)
    d = difference_in_means / np.sqrt(pooled_variance)
    return d
    
    myCohenEffectSize(firsts['totalwgt_lb'], others['totalwgt_lb'])
</code>


The pregnancy length for other babies was shorter than first babies and other babies weighed more than first babies. While there was a difference in the means, when effect size was computed, neither of these findings were statistically significant for this data set. 