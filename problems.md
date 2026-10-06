# Problems: Categorical and Numeric Variables

**Q1.**

Consider the data:
` [ red, blue, blue, red, green, grey] `

- a. Represent these data as a matrix of one hot encoded variables
    - before we encode the categorical variable into a one-hot matrix, we need to make a column for each unique category. then we will fill the matrix with 0s and 1s to indicate the presence and absence of the category.

    | values | red | blue | green | grey |
    | red | 1 | 0 | 0 | 0 |
    | blue | 0 | 1 | 0 | 0 |
    | blue | 0 | 1 | 0 | 0 |
    | red | 1 | 0 | 0 | 0 |
    | green | 0 | 0 | 1 | 0 |
    | grey | 0 | 0 | 0 | 1 |

    - the matrix is something like this:
    $$
    \begin{bmatrix}
    1 & 0 & 0 & 0 \\
    0 & 1 & 0 & 0 \\
    0 & 1 & 0 & 0 \\
    1 & 0 & 0 & 0 \\
    0 & 0 & 1 & 0 \\
    0 & 0 & 0 & 1
    \end{bmatrix}
    $$


- b. Compute the sample proportions for each label
    p(red) = 2/6 = 1/3 = 0.333
    p(blue) = 2/6 = 1/3 = 0.333
    p(green) = 1/6 = 0.167
    p(grey) = 1/6 = 0.167

    - the vector sample proportions is:
    $$
    \mathbf{p} = [0.333, 0.333, 0.167, 0.167]
    $$
Consider the data: 
$$
X = [ 1, 3, 3, 6, 11 ]
$$

- c. Compute and sketch the empirical CDF for this sample.

| x | count<=x | F(x) |
|---|----------|------|
| 1 | 1 | 0.2 |
| 3 | 2 | 0.4 |
| 3 | 2 | 0.4 |
| 6 | 3 | 0.6 |
| 11 | 5 | 1.0 |

$$
\sketch{
    x = [1, 3, 3, 6, 11]
    F(x) = [0.2, 0.4, 0.4, 0.6, 1.0]
}
$$



**Q2.**

We often want to take transformations of random variables, particularly when doing feature engineering.

- a. Suppose we have a random variable $X$ and transform it as $Y = a + b X$, with $b>0$. The distribution of $X$ is given by $F_X(x)$. What is the distribution of $Y$, $F_Y(y)$? What is the density, $f_Y(y)$?

    The distribution of $Y# is given by:
    $$
    F_Y(y) = P(Y <= y) = P(a+bX <=y) = P(X <= (y-a)/b) = F_X((y-a)/b)
    $$

    The density of $f_Y(y)$ is given by:
    $$
    f_Y(y) = \frac{d}{dy} F_Y(y) = \frac{d}{dy} F_X((y-a)/b) = \frac{1}{b} f_X((y-a)/b)
    $$

Suppose your sample is:
$$
X = [ 1, 3, 4 ]
$$

- b. What is the mean of the sample?
 $$
 \bar{X} = \frac{1}{3} (1+3+4) = \frac{8}{3} = 2.667
 $$

- c. Square all the values. What the mean of $X^2$?
$$
X^2 = [1^2, 3^2, 4^2] = [1, 9, 16]
\bar{x^2} = \frac{1}{3} (1+9+16) = \frac{26}{3} = 8.667
$$


- d. Compute the square of the mean from part b. Does this equal the mean of the square from part c?
$$
{X}^2 = (\frac{8}{3})^2 = \frac{64}{9} = 7.111
$$ 
Non-linear transformations change the moments/statistics of the data in a non-linear way. This is important to remember.


**Q3.**

The **exponential distribution** is
$$
F(x) = \begin{cases}
0, & x < 0\\
1-e^{-x}, & x \ge 0
\end{cases}
$$

- a. Sketch a graph of the exponential distribution and density.

$$
F(x) = \begin{cases}
0, & x < 0\\
1-e^{-x}, & x \ge 0
\end{cases}
$$
f(x) = \frac{d}{dx} F(x) = \begin{cases}
0, & x < 0\\
e^{-x}, & x \ge 0
\end{cases}
$$

$$
At $x=0$, the density is 1, and the distribution function is 0.
$$

$$
\begin {array}{c|cccccc}
x & 0 & 1 & 2 & 3 & 4 & 5 \\
F(x) & 0 & 1-e^{-1} & 1-e^{-2} & 1-e^{-3} & 1-e^{-4} & 1-e^{-5} \\
f(x) & e^{0} & e^{-1} & e^{-2} & e^{-3} & e^{-4} & e^{-5} \\
\end{array}
$$


- b. What is the probability that $X \ge 3$? What is the probability that $X \le 35$?

$$
P(X \ge 3) = 1 - F(3) = e^{-3} = 0.0498
P(X \le 35) = F(35) = 1 - e^{-35} = 1 - 0.0000 = 1
$$
- c. Suppose we transform $X$ by $ Y = 1 + 3X$. What is the distribution of $Y$, $F_Y(y) = pr[ Y \le y]$? Provide a formula and sketch a graph in comparison to $F_X$. What is the probability that $Y$ is less than 10?

$$
F_Y(y) = P(Y \le y) = P(1+3X \le y) = P(X \le \frac{y-1}{3}) = F_X\left(\frac{y-1}{3}\right)
$$

$$
f_Y(y) = \frac{d}{dy} F_Y(y) = \frac{d}{dy} F_X\left(\frac{y-1}{3}\right) = f_X\left(\frac{y-1}{3}\right) \cdot \frac{1}{3}
$$

$$
P(Y < 10) = F_Y(10) = F_X\left(\frac{10-1}{3}\right) = F_X(3) = 1 - e^{-3} = 0.9502
$$

$$
\begin{array}{c|cccccc}
x & 0 & 1 & 2 & 3 & 4 & 5 \\ \hline
F_X(x) & 0 & 1-e^{-1} & 1-e^{-2} & 1-e^{-3} & 1-e^{-4} & 1-e^{-5} \\ \hline
y = 1+3x & 1 & 4 & 7 & 10 & 13 & 16 \\ \hline
F_Y(y) & F_X(0) & F_X(1) & F_X(2) & F_X(3) & F_X(4) & F_X(5) \\ \hline
\end{array}
$$

**Q4.**

The **logistic distribution** is
$$
F(x) = \dfrac{1}{1+e^{-x}}
$$

- a. Sketch a graph of the logistic distribution and density.
$$
F(x) = \frac{1}{1+e^{-x}}
$$

$$
f(x) = \frac{d}{dx} F(x) = \frac{d}{dx} \frac{1}{1+e^{-x}} = \frac{e^{-x}}{(1+e^{-x})^2}
$$

$$
F(x) = \left( 1 + e^{-x} \right)^{-1}
F'(x) = -\left( 1 + e^{-x} \right)^{-2} \cdot \left(-e^{-x}\right) = \frac{e^{-x}}{(1+e^{-x})^2}
$$
 #Density function of the logistic distribution

 $$
 f(x) = F(x)\bigl(1 - F(x)\bigr)
 $$

 $$
 F(-x) = 1-F(x), \qquad f(-x)=f(x)
 $$

 F(0) = 0.5, \qquad f(0) = 0.25
 $$
 $$
 \text{mean} = \text{median} = \text{mode}=0, \qquad\text{variance} = \frac{\pi^2}{3}
 $$

 $$
 F(x) =\frac{1}{1+e^{-(x-\mu)/\sigma}}
 $$

$$
f(x) = \frac{e^{-(x-\mu)/\sigma}}{\sigma \left(1+e^{-(x-\mu)/\sigma}\right)^2}
$$

- b. What is the probability that $X \ge .8$? What is the probability that $X \le .3$?
 $$
 P(X \ge .8) = 1 - F(.8) 
 P(X \le .3) = F(.3) = 1- F(-.3)
 $$

- c. Suppose we transform $X$ by $ Y = 2X-1$. What is the distribution of $Y$? Provide a formula and sketch a graph. What is the probability that $Y$ is less than 0?
$$
F_Y(y) = P(Y\le y) = P(X\le \frac{y+1}{2}) = F_X\left(\frac{y+1}{2}\right)
$$

#to get the density function of $Y$
$$
f_Y(y) = \frac{d}{dy} F_Y(y) = \frac{d}{dy} F_X\left(\frac{y+1}{2}\right) = f_X\left(\frac{y+1}{2}\right) \cdot \frac{1}{2}
$$
f_Y(y) = \frac{1}{2} f_X\left(\frac{y+1}{2}\right)
$$



**Q5.**

The **median** is the value $x$ for which the probability that $X$ is above or below $x$ is $.5$, or $F(\text{median})= \frac{1}{2}.$

- a. What is the median of the exponential distribution?
$$
F_X(x) = 1 - e^{-\lambda x}
$$

Set $F_X(x) = \frac{1}{2}$ to find the median:
$$
\frac{1}{2} = 1 - e^{-\lambda x} \implies e^{-\lambda x} = \frac{1}{2} \implies -\lambda x = \ln\left(\frac{1}{2}\right) \implies x = \frac{\ln 2}{\lambda}
$$
$$
\text{median} = \frac{\ln 2}{\lambda}
$$

- b. What is the median of the logistic distribution?
$$
F(x) = \frac{1}{1+e^{-(x-\mu)/\sigma}}
$$

$$
\frac{1}{2} = \frac{1}{1+e^{-(x-\mu)/\sigma}} \implies 1+e^{-(x-\mu)/\sigma} = 2 \implies e^{-(x-\mu)/\sigma} = 1 \implies -(x-\mu)/\sigma = 0 \implies x = \mu
$$
\text{median} = \mu
$$

The **quantile function** is the inverse of the distribution function. The CDF answers the question, "What fraction $u$ of the time is $X$ below $x$?" ($F(x)=u$) and the quantile function answers the question, "For what value $x$ is $X$ below $x$ with probability $u$?" ($F^{-1}(u)=x$)

- c. What is the quantile function of the exponential distribution? 
$$
F(x) = 1 - e^{-\lambda x}
$$

Set $F(x) = u$ to find the quantile function:
$$
u = 1 - e^{-\lambda x} \implies e^{-\lambda x} = 1 - u \implies -\lambda x = \ln(1 - u) \implies x = -\frac{\ln(1 - u)}{\lambda}
$$
$$
F^{-1}(u) = -\frac{\ln(1 - u)}{\lambda}
$$
- d. What is the quantile function of the logistic distribution?
$$
F(x) = \frac{1}{1+e^{-(x-\mu)/\sigma}}
$$

Set $F(x) = u$ to find the quantile function:
$$
u = \frac{1}{1+e^{-(x-\mu)/\sigma}} \implies 1+e^{-(x-\mu)/\sigma} = \frac{1}{u} \implies e^{-(x-\mu)/\sigma} = \frac{1}{u} - 1 \implies -(x-\mu)/\sigma = \ln\left(\frac{1}{u} - 1\right) \implies x = \mu - \sigma \ln\left(\frac{1}{u} - 1\right)
$$
$$
F^{-1}(u) = \mu - \sigma \ln\left(\frac{1}{u} - 1\right)
$$


**Q6.**

Load `./data/metabric.csv`.

- a. Make an ECDF plot of `Overall Survival (Months)`. 
$$
import matplotlib.pyplot as plt
import pandas as pd

data = pd.read_csv('./data/metabric.csv')
plt.figure(figsize=(10,6))
plt.plot(data['Overall Survival (Months)'].sort_values().cumsum()/len(data), label='ECDF')
plt.xlabel('Overall Survival (Months)')
plt.ylabel('Cumulative Probability')
plt.title('ECDF of Overall Survival (Months)')
plt.legend()
plt.show()
$$
- b. Make an ECDF plot of `Overall Survival (Months)`, hued by `Chemotherapy`. 
Conditional on a patient receiving Chemotherapy, should we predict they will live a longer or shorter amount of time? Explain your answer clearly. 
$$
plt.figure(figsize=(10,6))
for chemo in data['Chemotherapy'].unique():
    subset = data[data['Chemotherapy'] == chemo]
    plt.plot(subset['Overall Survival (Months)'].sort_values().cumsum()/len(subset), label=f'Chemotherapy: {chemo}')
plt.xlabel('Overall Survival (Months)')
plt.ylabel('Cumulative Probability')
plt.title('ECDF of Overall Survival (Months) by Chemotherapy')
plt.legend()
plt.show()
$$
- c. Is chemotherapy an effective treatment? Explain your answer clearly.
$$
Chemotherapy appears to be effective if the ECDF for patients receiving chemotherapy is shifted to the right, however there is no clear indication that chemotherapy by itself is an effective treatment. 
$$
