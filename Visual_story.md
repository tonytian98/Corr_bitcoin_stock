# 1. First we take a look at our data source:
The study uses daily closing price of Bitcoin, S&P500 Index, STOXX50 Index and Hang Seng Index.
from October 1st 2014 to December 1st 2021, a total of 1852 trading days.

The red line indicates the date Match 1st, 2020, which is defined as the date of outbreak of Covid-19.

There are 1397 days before this day and 455 days after in the sample
![alt text](https://github.com/tonytian98/Corr_bitcoin_stock/blob/main/C1.png)

## We are interested in the returns and their correlations with each other, so let's at a look at their returns' distribution
![alt text](https://github.com/tonytian98/Corr_bitcoin_stock/blob/main/C2.png)

By camparing to the cyan normal distribution, we can see that their distributions are like student t distribution， which is like a fat-tailed normal distribution, which is common in financial time series.

# 2.After we ran our GCC-GARCH Model on the return seires, we will get their Dynamic conditional **correlation**, let's first plot these series out before further analysing them
![alt text](https://github.com/tonytian98/Corr_bitcoin_stock/blob/main/C3.png)

Look at the Bitcoin-S&P 500 Dynamic conditional **correlation** for example (the blue line), the dotted line indicates mean value of the series, and the red vertical line indicates the break point, which is the date of outbreak of Covid-19

We can clearly see, before the outbreak, the correlation is like a mean-reversing seires around 0, but after, it goes straight up (becomes positive). (Although we will still need OLS and T-test to prove the observation's validity)


# 3. When we run the DCC-GARCH Model, we will get the so called "implied volatility" from GARCH, let's plot those out
![alt text](https://github.com/tonytian98/Corr_bitcoin_stock/blob/main/C4.png)

Using Bitcoin-S&P 500 as an example, the above two is just scatter plot of the log return series, before and after the outbreak. If our preious hypothesis is correct, we should see that most of the points on the right graph on the diagonal(from bottom left to top right).
It indicates positive correlation, which is exactly what the graph is showing us.

The two graph at the bottom are the implied volatility, which can be interpreted as the absolute value of the log return. The relationship becomes clearer as after taking the absolute value,
only the magnitude matters, not the direction. As we can see, there is a clearer diagonal line formed by (white) points on the right bottom graph).

So, indeed, the correlation went from mean-reverting around 0, to just positive.

And by comparing the scale of the left and that of the right, we can also see market volatility became higher too (from -5~5,0~50 to -10~10, 0~150). 
