[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

**Exercise 7.1 Using data from the NSFG, make a scatter plot of birth weight versus mother’s age. Plot percentiles of birth weight versus mother’s age. Compute Pearson’s and Spearman’s correlations. How would you characterize the relationship between these variables?**

There is not much of a linear relaitonship between the varaibles, as can be seen in the scatterplot. Additionally, the Pearson Correlation (0.069) and Spearman Correlation (0.095) are both close to zero, indicating a very weak linear relationship.

<code>Python
    import numpy as np
    import pandas as pd

    import brfss

    import thinkstats2
    import thinkplot
    
    import first

    live, firsts, others = first.MakeFrames()
    live = live.dropna(subset=['agepreg', 'totalwgt_lb'])
    pd.options.display.max_columns = None
    
    thinkplot.Scatter(live['totalwgt_lb'], live['agepreg'], alpha=0.1)
    thinkplot.Config(xlabel='Birth Weight (lb)',
                 ylabel='Mother\'s Age',
                 legend=False)
    
    pearson_correlation = Corr(live['totalwgt_lb'], live['agepreg'])
    pearson_correlation
    
    spearman_correlation = SpearmanCorr(live['totalwgt_lb'], live['agepreg'])
    spearman_correlation


</code>
