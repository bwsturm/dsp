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



```Python
print('The mean for the actual distribution is: {}'.format(num_children_pmf.Mean()))
print('The mean for the biased distribution is: {}'.format(num_children_pmf_biased.Mean()))

>> The mean for the actual distribution is: 1.024205155043831
>> The mean for the biased distribution is: 2.403679100664282
```