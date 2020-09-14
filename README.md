# Keep On Closing #
## Graduate Course: Quantitative Analysis for Business

This was an individual project from a course on Multiple Linear Regression (a supervised machine learning technique for quantitative analysis). Below is the prompt from the client:

> Hello! I hope this message finds you well! After our last project predicting house prices was so successful, I thought we could work on a follow up project. Since the last time I have collected more data to improve the model to predict house prices. It was clear that I needed at least one other predictor, so I decided to start recording the style of architecture of each property. I specialize in three types of Architectures: Craftsman, Queen Anne, and Victorian. The new data that I collected is in the attached data file.
> 
> In our last project we verified how much the square footage of the house affects the price of the property, but I don't know how this relationship is affected when we take the architecture style into consideration. I would like to better understand how both the square footage and the style of the house affects the price so that I can better target specific homes to make the most profit on a sale. Can you help me to better understand how both of these variables affect the Price of these properties?

[Please click here to visit the previous project with this client!](https://github.com/SagarBansal7/Always-Be-Closing)

### Analysis Summary

#### 1) Understanding the relationships:

To understand how the relationship of square footage with house price will change after taking architecture style into consideration, I started with some data exploration to see if I have any evidence to believe that architecture style can be correlated with the House price. I have used Architecture Style and Type interchangeably in the report. Also, numerical summaries of the variables can be found in Table 1 and 2 below.

#### Table 1: Descriptive Statistics - Price and Sqft

![Table 1](https://user-images.githubusercontent.com/37155988/93031712-05bb9f80-f5fb-11ea-8dd7-bbd6a09c0568.png)

#### Table 2: Descriptive Statistics - Type

![Table 2](https://user-images.githubusercontent.com/37155988/93031714-05bb9f80-f5fb-11ea-88e5-b7418f697e51.png)

I produced three box plots of Price variable for each of the architectural type and noticed that all three boxplots are considerably different from each other (see Figure 1). Each box plot gives us a sense of the Price distribution by showing us the minimum, first quartile below which 25% of the data lies, median below which half of the data lies, third quartile below which 75% of the data lies and maximum values of the Price for a particular architecture type. From the box plots, we found that the median price of Victoria type is highest, followed by the median price of Craftsman type and then, the median price of Queen Anne type. Similar sequences were observed for minimum, maximum, first and third quartile values of the Price among the three types. This gave us a strong indication that the type variable can be correlated with our response variable so we decided to include the variable term in our model. 

#### Figure 1: Box plot – Price vs Architecture Type

![Figure 1](https://user-images.githubusercontent.com/37155988/93031708-05230900-f5fb-11ea-95a8-44e7a959c342.png)

Moreover, we also generated a scatter plot with Price on Y-axis, Sqft on X-axis and data points colored by Type variable (see Figure 2). We noticed that Sqft can have a positive linear correlation with our response so we agreed to include it in our model. Interestingly, when we added reference line for each of the three type of houses in the scatter plot, we found that all of them suggests a linear correlation with the response. Also, it was visible that reference lines are slanted to each other (different slopes). In other words, it showed different house types may change the relationship between square footage and house prices differently. It motivated us to further investigate this effect by including interaction terms between these two variables in the model. 

#### Figure 2: Scatter plot – Price vs Sqft (Coloured by Type)

![Figure 2](https://user-images.githubusercontent.com/37155988/93031709-05230900-f5fb-11ea-84df-5d7e9df6e8df.png)

After estimating the coefficients, we revealed three important correlations of Square Footage and Architecture Type with House Price according to our model (see Table 5). First, a 100 unit increase in the Square footage is associated with 3251.20 dollars increase in the average house price for Queen Anne house types. Second, a 100 unit increase in the Square footage is associated with 12907.5 dollars increase in the average house price for Craftsman house types. Third, a 100 unit increase in the Square footage is associated with 22569.30 dollars increase in the average house price for Victorian house types.    

#### Table 5: Coefficients

![Table 5](https://user-images.githubusercontent.com/37155988/93031718-06543600-f5fb-11ea-819c-b9559252c677.png)

For the house types, the model estimates that the change in average house prices is roughly 14915.89 dollars higher for Victorian types than Queen Anne types when square footage is zero. In addition, the model estimates that the change in average house prices is 29749.83 dollars higher for Craftsman types than Queen Anne types when square footage is zero. Also, the average house price for Queen Anne house types is roughly 166596.77 dollars when square footage is set to zero. Please note that a house of zero square footage is practically infeasible. These values are theoretical to help the client understand the individual correlation of different house types with the house prices. In practice, we will always have some value of square footage for a particular house. 

One more thing, only the intercept and interaction terms are found to be statistically significant at 5% significance level. By this we mean that the relationship between the square footage and house price is affected by the type of house which we also expected during the data exploration phase. However, the individual predictor terms do not provide values relative to the variability in the House Price i.e., these terms will not add much to our response value according to the model.      

#### 2) Limitations of the analysis:

Based on our analysis, it is crucial to keep in mind that the relationships determined are only valid for house area values (Sqft) ranging from roughly 813.80 ft2 to 3284.65 ft2 and architecture types of Queen Anne, Victorian and Craftsman. In addition, 91.3% of the variability in the model is explained by this model after accounting for the model size. This is a great value and we will not actively encourage our client to collect additional features for future analysis considering the costs associated with data collection. However, if the client wishes to further improve the variability explained by the model or to understand the relationship between a new variable and the House Price, he may consider some of the following factors for that purpose: 1) Distance from frequently visited places such as Supermarket, Hospital and Airport, 2) Age of the property 3) Current state of local real estate market (Recession or not) and 4) Condition of the house.

### Appendix

#### 1) Statistical analysis:

I summarized the data and found that the (mean, minimum, maximum) values of Price and Sqft are roughly (475218.29, 142585.53, 939780.40) and (1907.50, 813.80, 3284.65), respectively (see Table 1).  We discovered that 42 percent of all the houses in the dataset are Victorian type, 40 percent of all the houses are Craftsman type and rest of the houses are of type Queen Anne (see Table 2). 
  After accounting all information, we hypothesized the following Multiple Linear Regression model for further study:

Yi = β0 + β1Xi + β2D1i + β3D2i + β4D1iXi + β5D2iXi + εi

where Yi is the price in USD of the ith house, Xi is the area in square foot of the ith house, D1i and D2i are two dummy variables where 1 stands for Craftsman and Victorian type, respectively and Queen Anne type is the reference level for the ith house, β4D1iXi and β5D2iXi are the interaction terms between X, D1 and X, D2, respectively, β0, β1, β2 and β3 are the intercept, slope and coefficients of two dummy variables, β4 and β5 are interaction effects, ε i is the error term with the following assumptions: εi ~ indp. Normal(0, σ).

After running the regression for this model, we got the estimated co-efficient β0, β1, β3, β4, β5 and β6 as roughly 166596.77, 32.51, 14915.89, 29749.830, 96.56 and 193.181, respectively (see Table 5). From table 3, we can note that the R square for this model came out to be 0.922 which means that 92.2% of the variability in this Price is explained by this model. Also, adjusted R square value is 0.913 which means that 91.3% of the variability is explained by our model after accounting for the model size. Note that the values of R square and adjusted R square are very close indicating that the additional terms do not have a big penalty relative to our sample size of 50. The standard error of the estimate is roughly 58336.03 which is also good relative to the mean house price of 475218.29 USD approximately. Finally, as reported in Table 4, the result of F-test shows us that our model is statistically significant with a p-value of nearly 0.000 which is less than 0.05 at 5% significance level i.e., our model is found to be useful as a whole. These different criteria strongly suggest that the model should be considered useful.  

	To check the validity of our model, we first looked at the Unstandardized Residual vs Unstandardized Predicted value plot (see Figure3). The plot doesn’t show any clear pattern demonstrating that the model has no heterogeneity issue and it fits well. In addition, in Figure 4 we see that Q-Q plot is aligned with the normal distribution diagonal line suggesting the error terms are almost normal i.e., the model has no normality issue. Lastly, we did not find any evidence of time series structure in our data so no need to perform Durbin-Watson test i.e., no independence issue. Hence, we do not have any evidence to reject the model based on validity issues.
  
Furthermore, we conducted hypothesis testing for the intercept, slope and interaction coefficient at 5% significance level (see Table 5). For β0, the null and alternative hypotheses were as follows: H0: β0 = 0; HA: β0 ≠ 0. Since the P-value (0.010) is less than 0.05 at 5% significance level, we reject the null hypothesis i.e., β0 is statistically significant. For β1, β2 and β3, the null and alternative hypotheses were as follows: H0: β1 = 0; HA: β1 ≠ 0, H0: β2 = 0; HA: β2 ≠ 0 and H0: β3 = 0; HA: β3 ≠ 0, respectively. Since the P-values for β1 (0.265), β2 (0.836) and β3 (0.688) are more than 0.05 at 5% significance level, we fail to reject the null hypotheses i.e., β1, β2 and β3 are not very different from what we would expect if they were zero, according to the model. For β4 and β5, the null and alternative hypotheses were as follows: H0: β4 = 0; HA: β4 ≠ 0 and H0: β5 = 0; HA: β5 ≠ 0, respectively. The P-values came out to be more than 0.05 for both β4 (0.010) and β5 (0.000) i.e., the interaction effects are statistically significant at 5% significance level and there is some interaction between our dummy variables and Sqft that will change the relationship of Sqft with House Price as D1 (Victoria Type) or D2 (Craftsman Type) changes.  

