[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

```Python
resp = nsfg.ReadFemResp()

num_children_pmf = thinkstats2.Pmf(resp.numkdhh, label='actual')

def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf

num_children_pmf_biased = BiasPmf(num_children_pmf, label='biased')

thinkplot.PrePlot(2)
thinkplot.Pmfs([num_children_pmf, num_children_pmf_biased])
thinkplot.Config(xlabel='Number of Children', ylabel='PMF')
```

![Number of Children Plot](https://github.com/bwsturm/dsp/blob/master/statistics/figures/num_children_pmf.png)


```Python
print('The mean for the actual distribution is: {}'.format(num_children_pmf.Mean()))
print('The mean for the biased distribution is: {}'.format(num_children_pmf_biased.Mean()))

>> The mean for the actual distribution is: 1.024205155043831
>> The mean for the biased distribution is: 2.403679100664282
```

This problem asks us to plot the distribution for the number of children under 18 in the household using the data found in the NSFG data set.  In the first case, we are to plot the actual distribution (labeled 'actual') and in the second case we are to plot the biased distribution (labeled 'biased').  I employed the BiasPmf() function found in the ThinkStats repository in order to generate the biased probability mass function.  Then, it was a simple matter to generate the plot using the ThinkPlot library.  Examining the plot, it is clear that the biased distribution is skewed to the right (i.e., greater number of children) in comparison to the actual distribution.  This makes sense, because families with no children will be underrepresented in the biased distribution.  This results in a larger mean for the biased distribution (2.41 children) versus the actual distribution (1.02 children).