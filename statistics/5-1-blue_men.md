[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

The percentage of U.S. males between 5'10" and 6'1" is determined as follows.

```Python
import scipy.stats

mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)

dist.cdf((6*12+1)*2.54) - dist.cdf((5*12+10)*2.54)

>> 0.34274683763147457
```

If you evaluate the cdf for males with the independent variable of 6'1", this will give the fraction of men in the population with a height less than or equal to 6'1".  Likewise, if you evaluate the cdf with x=5'10", this will give the fraction of men with height less than or equal to 5'10".  Therefore, it is a simple matter to determine the percentage of U.S. males between these two heights by taking the difference of their respective cdf's.  In this case the percentage comes out to 34.3%.  