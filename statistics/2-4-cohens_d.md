[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

```python
def CohenEffectSize(group1, group2):
    """Computes Cohen's effect size for two groups.
    
    group1: Series or DataFrame
    group2: Series or DataFrame
    
    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d
```

```python
CohenEffectSize(firsts.totalwgt_lb,others.totalwgt_lb)

>> -0.088672927072602
```

To solve this problem, I used code found in the ThinkStats repo.  I did not write the CohenEffectSize() function, however, I do understand how it works.  As the book indicates, Cohen's D is a statistic that describes the difference between two groups.  In this case, the difference in the means is -0.089 standard deviations.  In this case, first pregnancies typically result in lighter babies.  The Cohen's D difference for birth weights has a greater magnitude than it has for pregnancy length.   

