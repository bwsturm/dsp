[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

```Python
rand_nums = np.random.random(1000)
randnums_pmf = thinkstats2.Pmf(rand_nums)
thinkplot.PrePlot(1)
thinkplot.Pmf(randnums_pmf, width=.01)
thinkplot.Config(xlabel='Number', ylabel='PMF')
```

![Random number pmf](https://github.com/bwsturm/dsp/blob/master/statistics/figures/rand_num_pmf.png)

```Python
cdf = thinkstats2.Cdf(rand_nums)
thinkplot.Cdf(cdf)
thinkplot.Config(xlabel='Number', ylabel='CDF')
```

![Random number cdf](https://github.com/bwsturm/dsp/blob/master/statistics/figures/rand_num_cdf.png)

The question was to plot the PMF and the CDF for an array of 1000 random numbers generated using the numpy.random.random() method.
Once I created the array of random numbers, then I just called the thinkstats2.Pmf() and thinkstats2.Cdf() methods to generate the pmf and cdf respectively.  The PMF plot looks a little strange, because it appears as a box from 0-1 with a height of 0.001.  However, this makes sense because any value from 0-1 has an equal probability of being sampled, and the integral of the pmf is 1.  Likewise, the CDF is more or less linear following the function y = x.  As the book explains, this is because 10% of the sample is below the 10th percentile (i.e., between 0 - 0.1), 20% is below the 20th percentile (i.e., between 0 - 0.2), and so on.   
