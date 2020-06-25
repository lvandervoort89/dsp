[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

**Exercise 3.1 Something like the class size paradox appears if you survey children and ask how many children are in their family. Families with many children are more likely to appear in your sample, and families with no children have no chance to be in the sample.Use the NSFG respondent variable NUMKDHH to construct the actual distribution for the number of children under 18 in the household.** 

The Probability Mass Function (PMF) of the number of children under 18 in the household for the NSFG dataset is below. 

<code>Python
    import numpy as np
    import nsfg
    import first
    import thinkstats2
    import thinkplot
    
    resp = nsfg.ReadFemResp()

    pmf_numkdhh = thinkstats2.Pmf(resp['numkdhh'], label='numkdhh')
    
    thinkplot.Pmf(pmf_numkdhh)
    thinkplot.Config(xlabel='Number of Children Under 18', ylabel='PMF')
</code>

**Now compute the biased distribution we would see if we surveyed the children and asked them how many children under 18 (including themselves) are in their household. Plot the actual and biased distributions, and compute their means. As a starting place, you can use chap03ex.ipynb.** 

<code>Python
    def BiasPmf(pmf, label):
        new_pmf = pmf.Copy(label=label)

        for x, p in pmf.Items():
            new_pmf.Mult(x, x)
        
        new_pmf.Normalize()
        return new_pmf
    
    biased_pmf = BiasPmf(pmf_numkdhh, label='observed')
    thinkplot.PrePlot(2)
    thinkplot.Pmfs([pmf_numkdhh, biased_pmf])
    thinkplot.Config(xlabel='Number of Children Under 18', ylabel='PMF')
    
    pmf_numkdff.Mean()
    biased_pmf.Mean()
</code>



