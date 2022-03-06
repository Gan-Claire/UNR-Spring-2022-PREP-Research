# UNR-Spring-2022-PREP-Research
## Stock Market Performance Analyze
### By Claire Gan

## Introduction:
>  Exchanged-traded funds investing in stocks and bonds are popular investment tools. Throughout the market, many investors try to predict the market and have different opinions on when is the best time to invest. Some predicts to invest when the fund is in high-performing because they believe as the fund performs well, it will continue this trend. Others may say buy low-performing funds because they believe the price will eventually revert to the long-term mean in the future. Is there a strategy or system to correctly predict the future market? There are three different hypotheses for this question.
> - Momentum, when past high returns imply future high returns. Our strategy is to buy high-performing funds because they will continue to be high-performing in the future.
> - Mean Reversion, when past high returns imply future low returns. This implies contrarian strategy where we buy low-performing funds expecting high-performing in the future.
> - Efficient Market Hypothesis, when stocks already reflect all publicly available information. If we invest based on publicly information, we will not be able to systematically outperform the market overtime.<br />
> 
> My goal is to determine which of my hypothesis best suitable for the market.

## Methods and Data:
> To analyze the market, we chose twenty-one ETFs from different categories such as value ETF, growth ETF, Mid Cap ETF, Small Cap ETF, developed markets, and emerging market, addition to ten bonds to compute their autocorrelation. We first download data of ETFs from iShares and data of bonds from Black Rock. Based on the data, we used time series to compute autocorrelation function for monthly returns with lag 1 on autocorrelation since the ETF or bond exist, the autocorrelation since January 2007, and January 2016 by using Excel. The lag k autocorrelation is defined as 
> 
> <img src="http://latex.codecogs.com/svg.latex?rk&space;=&space;\frac{\sum_{i=1}^{N-k}(Y_{i}-\bar{Y})(Y_{i-k}-\bar{Y})}{\sum_{i=1}^{N}(Y_{i}-\bar{Y})^2}" title="http://latex.codecogs.com/svg.latex?rk = \frac{\sum_{i=1}^{N-k}(Y_{i}-\bar{Y})(Y_{i-k}-\bar{Y})}{\sum_{i=1}^{N}(Y_{i}-\bar{Y})^2}" />
> 
> We also recorded the sample size for the purpose of determining whether the correlation is significant.
> 
| Name of EFT/Bond | Overall autocorrelation | Sample size | Autocorrelation since Jan. 2007 | Autocorrelation since Jan. 2016 |
|------------------|-------------------------|-------------|---------------------------------|---------------------------------|
| HDV              | -0.1386415              | 130         |                                 | -0.1276585                      |
| IVV              | 0.05978554              | 261         | 0.06121677                      | -0.1406699                      |
| IUSB             | 0.03607117              | 91          |                                 | 0.11626221                      |
| IDEV             | -0.0223165              | 58          |                                 |                                 |
| DGRO             | -0.1267573              | 91          |                                 | -0.130534                       |
| IVW              | 0.05387962              | 260         | 0.03744368                      | -0.117592                       |
| IGRO             | -0.0229677              | 68          |                                 |                                 |
| IJT              | 0.06364805              | 251         | 0.04828613                      | -0.0312563                      |
| IJK              | 0.08006693              | 258         | 0.06625718                      | -0.1083738                      |
| IVE              | 0.08789623              | 260         | 0.08445575                      | -0.1202385                      |
| IJS              | 0.04857777              | 258         | 0.03029736                      | -0.0065235                      |
| IJJ              | 0.07266481              | 258         | 0.05313278                      | -0.0567782                      |
| IJH              | 0.07316421              | 260         | 0.06042167                      | -0.0863572                      |
| IJR              | 0.03316589              | 260         | 0.0394976                       | -0.0169131                      |
| FXI              | 0.0511023               | 207         | 0.05486229                      | -0.200533                       |
| IEMG             | 0.05368247              | 111         |                                 | 0.00253184                      |
| ILF              | 0.12859793              | 243         | 0.14637793                      | 0.08557024                      |
| INDA             | -0.089113               | 119         |                                 | -0.0848631                      |
| DVYE             | 0.08016009              | 119         |                                 | 0.04891166                      |
| EEMS             | 0.02314593              | 125         |                                 | 0.05473916                      |
| IXUS             | 0.00147018              | 111         |                                 | 0.01489972                      |
| TLT              | 0.04712816              | 234         | 0.05784082                      | 0.14829042                      |
| ISTB             | 0.04177211              | 111         |                                 | 0.13511231                      |
| IMTB             | 0.10040227              | 62          |                                 |                                 |
| ILTB             | 0.06761543              | 145         |                                 | 0.06949515                      |
| IAGG             | 0.06887515              | 74          |                                 | 0.08900682                      |
| AGG              | 0.08268953              | 220         | 0.07441978                      | 0.14015808                      |
| HYG              | 0.16708581              | 177         |                                 | -0.0047792                      |
| HYXU             | -0.0093955              | 117         |                                 | 0.06957094                      |
| MUB              | -0.0035766              | 172         |                                 | 0.0320936                       |
| TIP              | -0.0082128              | 217         | 0.019997                        | -0.0164191                      |

> After computing the autocorrelation for three different period, we need to determine the significancy of each autocorrelation. Assume there is no real correlation, <img src="http://latex.codecogs.com/svg.latex?\emph{p}=0" title="http://latex.codecogs.com/svg.latex?\emph{p}=0" />, but because of the large size in data, empirical <img src="http://latex.codecogs.com/svg.latex?\hat{p}" title="http://latex.codecogs.com/svg.latex?\hat{p}" /> will be nonzero but close to zero. By using the significant level of probability 95%, a real correlation will be between <img src="http://latex.codecogs.com/svg.latex?\frac{-1.96}{\sqrt{N}}" title="http://latex.codecogs.com/svg.latex?\frac{-1.96}{\sqrt{N}}" /> to <img src="http://latex.codecogs.com/svg.latex?\frac{1.96}{\sqrt{N}}" title="http://latex.codecogs.com/svg.latex?\frac{1.96}{\sqrt{N}}" />, where N is the sample size. The reason why 1.96 is being use is because the “Bell Curve” of Standard Normal Distribution. 95% of the “Bell Curve” of Standard Normal Distribution is between -2σ and 2σ, which is -1.96 to 1.96. Therefore, if empirical correlation <img src="http://latex.codecogs.com/svg.latex?\hat{p}" title="http://latex.codecogs.com/svg.latex?\hat{p}" /> is outside of the interval <img src="http://latex.codecogs.com/svg.latex?|\hat{p}|>&space;\frac{1.96}{\sqrt{N}}" />, then there is a real correlation. Otherwise, an event with low probability of 5% will occur. Based on its significancy, if the autocorrelation function is significantly negative, then it will prove the market is Mean Reversion. If the autocorrelation function is significantly positive, it proves the market is Momentum. If the autocorrelation function is not significant, then the market is in Efficient Market. 

## Result:
> From all ETFs and bonds since they start, only Latin America 40 ETF and iShares iBoxx $ High Yield Corporate Bond ETF have significant positive correlation. For the period since January 2007, only Latin America 40 ETF has significant positive correlation. There is no significant correlation from any ETFs and bonds of the period since January 2016. Overall, majority of ETFs and bonds are not significant.

## Conclusion:
> Based on computing the autocorrelation function for ETFs and bonds, we found most of them are not significant, which means they lie on the low probability of 5%. Other than some special cases, we can conclude the market is an Efficient Market Hypothesis. There is no relationship between the past performance and future performance of ETFs and bonds. In an Efficient Market, it is difficult to predict the future market since the market price will only react to new information in the market. Also, there are no type of information that will give advantage to investors in the market. 
