Youtube Link To Presentation Video: https://studio.youtube.com/video/99lU06um4Tk/edit

Slide 1: 
Hi, I am Damaen from Data Cleaners In Demand, and together with Dawn, Celine and Marth, we will be presenting our machine learning model to predict gdp growth and recessions. 

Slide 2: 
We are given two datasets - quarterly data and monthly data. The quarterly data is more suitable for the ML model implementation as it includes more relevant features, minimizes noise, and reduces the possibility of overfitting. 

Slide 3: 
For the data cleaning process, we extract the most important columns, rename columns to more readable formats, handle NA values, check for duplicates and correct improper data types. 

Slide 4: 
Next, we conducted a series of data visualizations including stock prices and civilian unemployment rates. We created line plots, area charts, bar graphs and heat maps. We subsequently analyzed the visualizations and provided insights.

Slide 5: 
For the Machine Learning model, we utilized the ARDL model to forecast recessions by capturing dynamic relationships with quarter on quarter real GDP growth. Furthermore, we employed AIC to optimize model selection by obtaining the optimal lag structure for improved forecasting accuracy.

Slide 6: 
To accurately evaluate our model's performance, we must go beyond its predictive ability and assess the statistical properties of its residuals. Ensuring well-behaved residuals is crucial for a model’s validity, so we conducted a series of tests to check for autocorrelation, normality, skewness, and tailed-distribution. The Durbin-Watson statistic indicate no significant autocorrelation, which confirms that our residuals are independent. However, both the Omnibus and the Jarque-Bera tests showed that the residuals significantly deviate from normality. We also observed extreme negative residuals, and a heavy-tailed distribution.

Slide 7: 
To improve the reliability of our model, we identified and handled outliers in the residuals using standardized residuals, Cook’s distance, and leverage. After these adjustments, we reassessed the residual properties. Now, the Omnibus and Jarque-Bera tests suggest that our residuals are approximately normal. Plus, skewness improved and kurtosis dropped, meaning the extreme values are no longer a major concern. 

Slide 8: 
To predict forecast GDP growth with ARDL, we used the optimal lag of independent and dependent variables obtained to train our ARDL model. With the trained ARDL model, we then predicted the forecast for 2025 quarter on quarter GDP growth, and the results are shown here. Our model predicts that economic contractions will not happen in 2025.

Slide 9:
Apart from ARDL, we also used a random forest model. Firstly, we converted real_gdp to gdp_qq to show quarter on quarter growth, and we included financial market variables due to their leading nature for greater insight into forecasting GDP growth. We then split the data into train and test sets. Lastly, we removed features highly correlated to gdp_qq before fitting train data to our model.

Slide 10: 
Feature selection was done using importances, and the top 9 variables (in green) were selected for fitting with the train data. The top contributor was corporate bond yield, followed by other important indicators including housing permits and consumer sentiments. 

Slide 11: 
Model evaluation was done using 4 different metrics, including R2, mean absolute percentage error and root mean squared error. These were used to check for model fit and accuracy in predicting in-sample values for gdp growth. The model managed to capture variations in the train data relatively well, with a R score of 0.744 and RMSE of 0.3. However, test data performance was much worse, with only 0.004 for our R score. 

Slide 12: 
This is the figure for train data, where most fluctuations are captured, though not as pronounced as the real dataset. This suggests that our model does not over-fit the train data. 
For this, we chose the number of estimators to be 15, to balance between over and underfitting. 

Slide 13: 
For test data, we can see that the sudden drastic changes in real GDP growth occurred in 2020-2021, in the height of COVID-19. This is the main reason for the seemingly poor performance of the model. However, disregarding the anomalous COVID-19 values, the model still tracks relatively well with actual data. 

Slide 14: 
To forecast GDP growth, we employed the use of ARIMA to create future values for exogenous variables before predicting using our random forest model. This is because the Random Forest model lacks the ability to forecast future values without exogenous inputs as it is dependent on past data and cannot predict on its own without known future variables
We would ideally use the entire dataset up to 2024. However, the COVID-19 values would disrupt the model predictions, and bring inaccuracy to our forecasts. Hence, 2 instances of ARIMA forecasting was used. First to forecast the 2020-2021 values, then again for 2025 values. For our ARIMA model, we utilised the auto_arima function which automatically selects the optimal ARIMA parameters. After fitting the model, we use it to predict the the next 5 quarters of data for the independent variables. The 5 quarters includes Q4 of 2024 and all 4 quarters of 2025. We then use our random forest model to forecast GDP growth for these 5 quarters.

Slide 15: 
So these are the GDP growth values of the next 5 quarters generated by our model. In general, we observe small but positive GDP growth. These projections also align with other positive economic indicators. In conclusion, The forecast indicates a strengthening economy, with no significant downturn anticipated in the near term.

Slide 16: 
We then generated a plot to visualise the actual test data in blue, predicted test data in yellow, and the future forecast generated by the Random Forest model, which is shown in red. The future forecast shows moderate fluctuations, indicating steady growth.

Slide 17: 
To improve our ARDL model, we can address the non-linearity in the model by exploring other models such as Threshold ARDL or Nonlinear ARDL that are better able to capture complex macroeconomic dynamics. To improve our random forest model, we can optimize its accuracy by implementing ensemble methods such as bagging and boosting. We can also enhance the validation process by methods such as the rolling window to account for changing economic conditions and ensure robust model performance over time.

Slide 18: 
For the first question, we identified these as possible key macroeconomic indicators for predicting downturns. They include both leads (such as stock market trends) and lags such as rising unemployment rates. This gives a relatively holistic view of future price predictions.

Slide 19: 
Each indicator also possesses its own forecast horizon, with most of them being relatively short term (maybe up to 6 months in advance). The inversion of yield curve however, which can be estimated using corporate and treasury bond yields, may be able to provide long-term insights as well (up to 1 or 2 years). In general, all of these are closely linked through similar ideas of demand. A fall in demand and spending inadvertently leads to a fall in economic output. Some of these variables were also selected for during implementation of our random forest model. 

Slide 20: 
Regarding stock markets and consumer confidence, the change in expectations of the future may lead to more prudent spending and investment actions, leading to lower overall transactions. This relates to productivity, as the fall in transactions signify a fall in demand. Businesses may respond with retrenchments, leading to higher unemployment rates. A multiplier effect worsens the extent of the demand fall, as the unemployment results in even lower disposable income for consumers. Economic contraction hence occurs as a result of multiple cycles of declining demand. 

Slide 21: 
The inversion of the yield curve occurs when short term interest rates exceed long term interest rates, and may arise from a number of reasons, resulting in higher bond yield for short term bonds rather than long term bonds. A trigger such as sudden spike in inflation would also result in higher interest rate and borrowing costs. This deters both consumers and businesses from spending or investing respectively. For businesses, they are discouraged from investing in expansions or new start-ups. For consumers, the heightened borrowing cost may affect their purchasing power, discouraging spending as well. Both of these hence result in a contraction once again.

Slide 22: 
Before answering this question, we have to first understand Singapore’s economy. Singapore is a small, open economy, and is heavily reliant on international trade, finance, and investments. From our forecast, it predicts that GDP growth is projected to hover around between 0.563% and 0.752%.There will be 2 significant dips during June and December 2025, which suggests the economy might face headwinds during these periods. We can also see that fluctuations for the forecast are less comparable to the actual test from 2022 to 2024.

Slide 23: 
When considering Singapore’s policy responses, we can break them down into three main categories: monetary, fiscal, and structural policies. For monetary policy, if inflation remains low and steady, the Monetary Authority of Singapore (MAS) can maintain or loosen the S$NEER policy band slightly to support exports. However, if inflation continues to rise alongside GDP growth, MAS may tighten the policy band to prevent overheating. Given Singapore’s status as a global trading hub, finding the right balance is crucial to sustaining stable growth. Fiscal Policy can play a crucial role by increasing government spending in areas like healthcare and infrastructure to boost long-term productivity. This can help enhance human capital and innovation capacity, which drive future economic potential. However, if inflation is already rising, policymakers might choose to hold back fiscal stimulus to avoid exacerbating price pressures. Structural Policies focus on long-term growth by investing in workforce upskilling, digital transformation, and R&D incentives. Workforce upskilling addresses skills mismatches, digital transformation boosts efficiency, while R&D incentives encourage technological advancements, creating new high-value industries. In a high-cost, knowledge-driven economy like Singapore’s, continuous innovation and human capital development are essential to maintain global competitiveness. 

Slide 24: 
Each policy approach carries its own risks, which policymakers must carefully navigate. For Monetary Policy, over-tightening the S$NEER band could harm Singapore’s export competitiveness, reducing foreign demand and slowing growth. On the other hand, over-loosening the band might cause imported inflation, raising costs for businesses and consumers. This trade-off between supporting growth and controlling inflation is particularly delicate for Singapore, where global price fluctuations quickly affect domestic markets. Fiscal Policy risks include crowding out private investments. Given Singapore’s small, open economy, fiscal measures might have a smaller impact on growth compared to larger, more closed economies where domestic demand plays a bigger role. Additionally, rising inflation could force MAS to tighten the policy band, counteracting the intended effects of fiscal stimulus and creating policy misalignment. Finally, Structural Policies can be costly, take significant time to bear fruit and may cause short-term disruptions. Reskilling programs, while beneficial long-term, require workers to invest time and resources, and not all displaced workers may successfully transition. By carefully coordinating these policy tools, Singapore can navigate economic uncertainty, promoting stable growth while mitigating potential risks. A balanced approach — combining short-term stabilization with long-term transformation — will be key to sustaining Singapore’s economic success.

Slide 25: 
For question 3, Donald Trump’s proposed tariffs include raising import tariffs on other countries such as Mexico, Canada, China and the EU, as well as industry-specific tariffs such as steel, aluminium, automobiles, semiconductors and pharmaceuticals. He is also considering a 10% reduction tariff on exports. 

Slide 26: 
With an increase in tariffs on imports, countries are less willing to export to US as cost of imported goods rises. This results in overall imports to decline. Similarly, as tariffs on exports decreases, countries are more willing to purchase US goods, leading to an increase in demand for US exports. Overall exports will increase. 

Slide 27: 
There are other impacts of tariffs on the economy. When tariffs on industries rises, they face higher production costs and will be less willing to produce goods and services. They will think of ways to cut costs and maintain their profits. They might retrench employees, leading to higher unemployment rates and average weekly hours to decrease. Due to lower company earnings, corporate bonds will be riskier and this pushes the yields higher. Moreover, industries might pass on the higher costs to consumers in the form of higher prices. This leads to a reduction in consumers’ purchasing power. Consumer sentiment will be lowered, further contributing to economic uncertainty. 

Slide 28: 
For the ML model, we can adjust the values from December 2024 onwards accordingly. We will set a higher value than September 2024 if the feature increases after tariffs and vice versa. If there is no noticeable change in the feature value after tariffs, we will set the same value as September 2024. 






