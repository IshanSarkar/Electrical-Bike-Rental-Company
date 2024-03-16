![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/e784613b-32e8-4853-9783-f6d2d033773f)![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/453bf80c-dbbb-43b5-aca0-3f34b9ccd11c)# Data Analysis of Electrical-Bike-Rental-Company
- Language: Python
- Libraries: numPy, pandas, matplotlib, seaborn, scipy.stats (ttest_ind, f_oneway, shapiro, levene, kruskal, chi2_contingency, pearsonr, spearmanr), statsmodels.graphics.gofplots - qqplot

## Business Problem:
- The company wants to identify which variables play significant roles in predicting the demand for shared electric cycles in the market. By determining the key variables influencing demand, the company can prioritize resources and strategic initiatives to optimize their business operations and meet customer needs effectively.
 - Additionally, the company aims to evaluate how well these identified variables describe the demand for electric cycles. Understanding the descriptive power of these variables will provide insights into the factors driving consumer behavior and preferences in the market, enabling the company to tailor its offerings and marketing strategies accordingly.

## Dataset Characteristics
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/fa63078f-fa9d-4ece-848a-360c3e559032)<br>
#### Column Analysis:
- datetime: Date and Time (datetime needs to in datetime format)
- season: Season as in 1: spring, 2: summer, 3: fall, 4: winter
- holiday: Whether day is a holiday or not (0 or 1)
- workingday: If day is neither weekend nor holiday is 1, otherwise is 0
- weather:<br>
1: Clear, Few clouds, partly cloudy, partly cloudy<br>
2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist<br>
3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds<br>
4: Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog <br>
- temp: Temperature in Celsius
- atemp: Feeling temperature in Celsius
- humidity: Humidity
- windspeed: Wind speed
- casual: Count of casual users
- registered: Count of registered users
- count: Count of total rental bikes including both casual and registered <br>
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/5c527aea-e1c5-46b2-9ddb-d42e69569a2e)<br>
- Date and Time: 
	- The dataset spans from January 1, 2011, to December 19, 2012 with 1 hr interval.
	- 50th percentile for datetime suggests it's around January 1st, 2012, 20:30.
	- The 75th percentile for datetime indicates it's likely early summer (July).
- Temperature: 
	- The average temperature is around 20.23°C, with a standard deviation of 7.79°C, indicating some variability in temperature.
	- The minimum temperature is 0.82°C, and the maximum is 41°C.
	- 25% of the time, the temperature is below 13.94°C, and 75% of the time, it's below 26.24°C.
- Humidity:
	- The average humidity is about 61.89%, with a standard deviation of 19.25%, suggesting moderate variability.
	- The minimum humidity is 0%, which seems like an anomaly. The maximum humidity is 100%.
	- 25% of the time, the humidity is below 47%, and 75% of the time, it's below 77%.
- Count of Rental Bikes:
	- The mean count of bike rentals is 191.57, with a standard deviation of 181.14, indicating a wide range of rental counts in the dataset.
	- There's a minimum count of 1 bike rental and a maximum of 977 rentals.
	- 25% of the rentals have a count below 42, and 75% have a count below 284.
- Wind Speed: 
	- Wind speed ranges from 0 to 56.99.
	- Average windspeed is approximately 12.8.
- Season: 
	- Average season is around 2.5, which would approximately indicate the transition between spring and summer.
	- The 25th percentile for the season indicates it's likely early summer (June).
- Holidays: 
	- Very few holidays on average (mean holiday value is close to zero).
- Working Day: 
	- Around 68% of the days are working days.
- Weather: 
	- The average weather condition is around 1.4, indicating generally clear weather.
- Count of Casual and Registered:
	- There are about 155 casual bike rentals and 191 registered bike rentals on average.
- Notably, the standard deviation for registered and casual rentals is quite high, indicating significant variability in rental patterns.<br>
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/15264a6e-11de-46b4-bfdc-e17d17c2fc4f)<br>
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/e2dfb6f0-52ac-41d2-a8cf-5b8cfabbcb91)<br>
#### Insight and Analysis:
- **Season:** It seems that data collection might have been fairly balanced across seasons, except for Season 1, which has slightly fewer instances compared to the others. This could be due to various reasons such as data collection biases, seasonality of the activity being recorded, or simply chance.
- **Holiday:** The dataset is heavily skewed towards non-holiday days. This is because the data span is of 2 years and naturally count of holidays and non-holidays will differ where holidays are very less.
- **Workingday:** Similar to the holiday variable, there's an imbalance in the data with more instances of working days compared to non-working days. This suggests that the dataset might not be equally representative of both types of days, which could skew any analysis or predictions made using this data.
- **Weather:** Most of the data appears to come from days with relatively clear or mist weather conditions (categories 1 and 2). There are very few instances of extreme weather conditions (categories 3 and 4), which could indicate either a bias in data collection towards good weather days or simply the rarity of extreme weather like snowing events depending on the time period covered by the dataset. <br>
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/7e2692c2-e66d-4948-80f6-75d88452f6ff)<br>
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/dffc8b9e-6bfb-4556-8fe2-b9f2a6428c7e)<br>
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/fcc62295-338b-42de-9054-be0082f9a833) <br>
#### Insight and Analysis:
- **Temperature and Feeling Temperature:** Both temperature and feeling temperature exhibit a bimodal distribution, suggesting peak bike rentals occur around 20 and 30 degrees Celsius, indicating a preference for moderate temperatures. Temperature skewness is slightly right-skewed (0.003691), indicating occasional higher temperatures. Feeling temperature skewness is slightly left-skewed (-0.102560), suggesting occasional instances of colder-than-expected conditions. <br>
*People like renting bikes when it's not too hot or too cold, but just right, with the most rentals happening around 20 and 30 degrees Celsius. Sometimes, it might feel a bit warmer than usual, and other times, it might feel cooler than expected.*
- **Humidity:** The data shows that bike rentals tend to peak when humidity levels are around 60%, suggesting people prefer renting bikes when humidity isn't too high. The negative skewness (-0.086335) indicates a slightly left-skewed distribution, implying occasional instances of lower humidity compared to the majority of data. <br>
*When humidity levels are around 60%, that's when people seem to rent bikes the most. It looks like they prefer it when it's not too humid. Sometimes, though not often, the humidity might be lower than usual, making it feel a bit drier.*
- **Wind Speed:** People prefer to rent bikes when the wind speed is low. The histogram for wind speed is right-skewed, indicating that there are several instances of relatively high wind speeds compared to the majority of the data. The positive skewness value (0.588767) confirms the right-skewed distribution of wind speed, emphasizing the prevalence of higher wind speeds in the dataset. <br>
*It means that most people like to rent bikes when there isn't much wind. But looking at the data, we see that there are quite a few instances when the wind is stronger than usual, which might affect bike rentals. So, businesses or planners should consider the wind speed when predicting bike rental demand.*
- **Casual and Registered Renters:** We have right-skewed histograms for both, indicating that most users rent bikes less frequently. However, the distribution of registered users is less skewed than casual users, suggesting that registered users might rent bikes more regularly. The skewness value for casual users is very high (2.495748), indicating a heavily right-skewed distribution, suggesting occasional instances of extremely high casual bike rentals compared to the majority of the data. Similarly, the skewness value for registered users is relatively high (1.524805), indicating a heavily right-skewed distribution, suggesting occasional instances of extremely high registered bike rentals compared to the majority of the data. <br>
*Most people rent bikes less often. There are a few instances where people rent a lot of bikes, but most of the time, they rent fewer. Registered users tend to rent bikes more regularly than casual users. For both casual and registered users, there are a few instances where people rent a ton of bikes, much more than usual. This could be during special events or unusual circumstances.*
- **Count of Rental Bikes**: The skewness value for the count of rental bikes is relatively high (1.242066), indicating a heavily right-skewed distribution. This suggests that most of the time, bike rentals are moderate, but occasionally there are instances of extremely high rentals, which skew the overall distribution to the right meaning, *These "super busy" days make the overall pattern of bike rentals lean towards the right side, making it look like there are more rentals than there actually are on most days.* <br>
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/1699ed87-669f-4dda-b859-18e9200f6d5d) <br>
#### Insight and Analysis:
- **Temperature:**
    - There's a moderate positive correlation between temperature and both casual users and feeling temperature. This implies that as temperature increases, the number of casual users and feeling temperature also tends to increase.
    - The correlation between temperature and the count of rented bikes is also positive but weaker compared to the correlation with casual users. This suggests that temperature might influence the number of bike rentals, but not as strongly as it influences casual users directly.
- **Casual Users:**
    - Casual users have a moderate positive correlation with both temperature and feeling temperature. This indicates that warmer weather and higher feeling temperatures tend to attract more casual users to rent bikes.
    - There's a negative correlation between humidity and casual users. This suggests that as humidity increases, the number of casual users decreases. This might imply that uncomfortable weather conditions deter casual users from renting bikes.
- **Registered Users:**
    - Feeling temperature has a weak positive correlation with registered users. This suggests that feeling warmer might have a slight influence on registered users, but it's not as pronounced as with casual users.
    - There's a weak positive correlation between windspeed and registered users. This could imply that higher windspeeds might slightly increase the number of registered users renting bikes.
- **Count of Rented Bikes:**
    - There's a moderate positive correlation between temperature and the count of rented bikes, indicating that warmer weather generally leads to more bike rentals.
    - Feeling temperature also has a positive correlation with the count of rented bikes, but it's weaker compared to the correlation with temperature.
    - Both humidity and windspeed have negative correlations with the count of rented bikes, though the correlations are relatively weak. This suggests that higher humidity and windspeeds might slightly decrease the number of bike rentals.

<br>*Overall, these correlations suggest that temperature, feeling temperature, humidity, and windspeed all play roles in influencing the number of bike rentals and the behavior of both casual and registered users. Warmer and more comfortable weather tends to attract more users, while adverse weather conditions like high humidity and windspeed might deter users from renting bikes. However, the relationships are not overly strong, indicating that other factors not included in this analysis might also be influencing bike rental patterns.* <br>
## Checking if there is any significant difference between the no. of bike rides on Weekdays and Weekends?
#### Conclusion:
- **ride_weekdays, ride_weekends (two-sided):**
Rejecting the null hypothesis indicates that there is a significant difference between the number of bike rides on weekdays and weekends. However, this result does not specify whether the difference is in favor of weekdays or weekends.
- **ride_weekdays, ride_weekends (right-tailed):**
Rejecting the null hypothesis in a right-tailed test suggests that the mean number of bike rides on weekdays is significantly greater than the mean number of bike rides on weekends. This implies that weekdays tend to have more bike rides compared to weekends.
- **ride_weekdays, ride_weekends (left-tailed):**
Failing to reject the null hypothesis in a left-tailed test suggests that there is no significant evidence to conclude that the mean number of bike rides on weekdays is significantly less than the mean number of bike rides on weekends. In other words, it suggests that weekends do not have significantly fewer bike rides compared to weekdays.
## Check if the demand of bicycles on rent is the same for different Weather conditions?
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/1b2b820f-5221-42c2-9301-cd4cb8f8e6db) <br>
As from the graph, the data needs to on red line (reference line) or close to it between -3 and +3 (standard deviation) of Theoratical Quantile as for Gaussian, 99.7% data fall on it<br>
**ND Checking:** Reject null hypothesis. Data not Gaussian <br>
**Via both (visual and statistical) test we can conclude that count column of dataset in not Gaussian.** <br>
**Variance Checking:** Reject null hypothesis. Variances are not Equal <br>
**As we can see that 2 assumptions for doing One-Way Anova is not met, so prefered choice is Kruskal-Wallis Test.** <br>
**Kruskal-Wallis:** Reject null hypothesis. Atleast one group has different Median <br>
It suggests that weather conditions have an impact on the number of bike rides.<br>
**Doing One-Way Anova just to check what it can answer.** <br>
Reject null hypothesis. Atleast one group has different Mean <br>
It suggests that weather conditions have an impact on the number of bike rides. <br>
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/37932fa4-414a-43e3-abd8-f90d1448d1cd)<br>
#### Insights and Analysis:
- Weather 1 and Weather 2 have the highest median bike rental counts, indicating that these weather conditions are more favorable for biking.
- Weather 3 has a lower median bike rental count compared to Weather 1 and Weather 2, but it also exhibits high outliers. This suggests that while the overall demand is lower during Weather 3, there are specific conditions within this weather category when bike rentals are unusually high, possibly during periods of scattered clouds or light rain.
- The presence of high outliers in Weather 3 indicates that there are certain conditions within this weather category where bike rentals spike unexpectedly. These outliers could be due to special events, holidays, or other factors that influence people's biking behavior during adverse weather conditions.
- Weather 4 experiences very low demand for bike rentals, indicating that these severe weather conditions deter people from biking.
#### Conclusion:
- Weather conditions significantly influence the demand for bike rentals, with clear or partly cloudy conditions (Weather 1) and misty conditions (Weather 2) being the most favorable.
- Weather 3 experiences lower overall demand for bike rentals but exhibits high outliers, indicating sporadic spikes in demand during specific conditions within this weather category.
- Weather 4 sees minimal demand for bike rentals due to severe weather conditions such as heavy rain, snow, and fog.
#### Business Recommendation:
- Company can adjust their inventory management strategies based on weather forecasts and historical rental patterns. They can ensure that they have an adequate number of bikes available during periods of high demand, such as clear or partly cloudy conditions (Weather 1), and scale back inventory during periods of low demand, such as heavy rain or snow (Weather 4).
- Offering promotions, discounts, or package deals during peak demand periods can attract more customers and increase revenue.
- Implementing flexible pricing models that adjust rates based on weather conditions and demand levels can optimize profitability.
- Tourism agencies and businesses can leverage insights into weather-related biking trends to tailor their marketing efforts and attract tourists interested in outdoor activities. <br>
## Check if the demand of bicycles on rent is the same for different Seasons?
**Kruskal:** Reject null hypothesis. Atleast one group has different Median. It suggests that Season have an impact on the number of bike rides.
**One-Way Anova:** Reject null hypothesis. Atleast one group has different Mean
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/3403a559-b475-44d0-8f00-d580d5b42ce7) <br>
#### Insights and Analysis:
- **Season 1 (Spring):** It has the lowest median count of bike rentals, indicating that, on average, fewer bikes are rented during spring compared to other seasons. The small interquartile range (IQR) suggests less variability in the data, meaning that the majority of bike rental counts in spring are relatively consistent. However, the presence of very high outliers suggests occasional spikes in bike rentals, which are significantly higher than the typical rental counts for spring.
- **Season 2 (Summer) and Season 4 (Winter):** They exhibit almost similar bike rental counts, indicating that during both summer and winter, a comparable number of bikes are rented on average. However, the smaller IQR in Season 4 suggests less variability in rental counts compared to Season 2. This means that the rental counts in winter are more consistently distributed around the median compared to summer.
- **Season 3 (Fall):** It has the highest count of bike rentals among all seasons, indicating that fall sees the most activity in terms of bike rentals. The higher median counts and larger IQRs compared to other seasons suggest that there is both a higher average number of bike rentals and greater variability in rental counts during fall.

#### Conclusion:
- Spring has the lowest median count with relatively consistent rental counts but occasional spikes in rentals.
- Summer and winter have similar median counts, but winter shows less variability in rental counts compared to summer.
- Fall stands out as the season with the highest median counts and the greatest variability in rental counts.

#### Recommendation:
- **Spring:** Despite the lower median counts, the presence of high outliers suggests potential opportunities for targeted promotions or events to capitalize on peak rental periods. Offer discounted rates or special deals during seasons with lower median counts in this season to incentivize rentals and mitigate the impact of lower demand. Participate in seasonal events, festivals, and community initiatives to increase brand visibility and attract potential customers.
- **Summer and Winter:** Given the similar median counts, efforts should be made to maintain consistent rental patterns in summer and take advantage of the more stable demand during winter. Offer complementary services such as guided tours, bike maintenance, or outdoor gear rentals to attract customers during off-peak seasons.
- **Fall:** Since fall has the highest median counts and greater variability, it may be beneficial to focus marketing efforts and resources during this season to maximize rental revenue. Increase the availability of bikes during peak seasons in this season to meet the higher demand and reduce the likelihood of stockouts. <br>
## Check if the Weather conditions are significantly different during different Seasons?
Reject null hypothesis. The weather conditions are significantly different during different seasons. This result suggests that weather patterns vary significantly across different seasons. <br>
![image](https://github.com/IshanSarkar/Electrical-Bike-Rental-Company/assets/160044904/1cb48fb0-30a1-49a2-a713-f45b140551ad)<br>
#### Insights and Analysis:
- The data indicates that weather conditions vary significantly across different seasons. This finding is supported by the statistical analysis that suggests rejecting the null hypothesis, indicating significant differences in weather patterns between seasons. For example, Season 1 (spring) has higher counts of Weather Condition 1 (Clear, Few clouds, partly cloudy) compared to other seasons, while Season 4 (winter) has higher counts of Weather Condition 3 (Light Snow, Light Rain + Thunderstorm + Scattered clouds).
- Season 1 (spring) and Season 2 (summer) show relatively higher counts of Weather Condition 1 (Clear, Few clouds, partly cloudy), indicating more favorable weather conditions during these seasons.
- Season 3 (fall) exhibits higher counts of Weather Condition 2 (Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist), suggesting more prevalent misty and cloudy weather during the fall season.
- Season 4 (winter) shows higher counts of Weather Condition 3 (Light Snow, Light Rain + Thunderstorm + Scattered clouds), indicating colder and potentially snowy or rainy conditions during the winter season.

#### Implications for Business and Operations:
- Company can use this information to anticipate demand fluctuations and adjust operational strategies accordingly.
- During seasons with more favorable weather conditions (e.g., spring and summer), businesses may expect higher demand for bike rentals and should ensure sufficient inventory and staffing levels to meet customer needs.
- Conversely, during seasons with less favorable weather conditions (e.g., fall and winter), businesses may need to implement promotional strategies or diversify offerings to attract customers despite potential lower demand for outdoor activities. <br>
## Overall Report:
- **Weather Conditions and Bike Rentals Analysis:**
    - Temperature and feeling temperature exhibit a bimodal distribution, with peak bike rentals occurring around 20 and 30 degrees Celsius, indicating a preference for moderate temperatures.
    - Humidity levels around 60% coincide with peak bike rentals, suggesting a preference for moderate humidity.
    - Bike rentals peak during low wind speeds, although there are occasional instances of higher wind speeds affecting rentals.
    - Casual and registered users show right-skewed distributions, with occasional spikes in rentals.
    - The count of rental bikes also exhibits a heavily right-skewed distribution, with occasional extremely high rental counts skewing the overall distribution.
- **Correlation Analysis:**
    - Temperature and feeling temperature have moderate positive correlations with casual users and the count of rented bikes, indicating that warmer weather attracts more casual users and increases bike rentals.
    - Humidity negatively correlates with casual users, suggesting that higher humidity deters casual users from renting bikes.
    - Feeling temperature has a weak positive correlation with registered users, implying a slight influence on their rental behavior.
    - Wind speed has a weak positive correlation with registered users, indicating a potential minor increase in rentals during higher wind speeds.
- **Weather Categories and Rental Patterns:**
    - Weather conditions significantly influence bike rental demand, with clear or partly cloudy conditions being the most favorable.
    - Weather 3 experiences lower overall demand but exhibits high outliers, suggesting sporadic spikes in demand during specific conditions.
    - Severe weather conditions in Weather 4 deter people from biking, resulting in minimal demand for bike rentals.
- **Seasonal Analysis:**
    - Spring has lower median rental counts but occasional spikes, indicating potential opportunities for targeted promotions.
    - Summer and winter show similar median counts, but winter exhibits less variability, suggesting more consistent rental patterns.
    - Fall stands out with the highest median counts and greater variability, indicating high demand and potential for maximizing rental revenue.
- **Weather Variability Across Seasons:**
    - Significant differences in weather patterns across seasons influence bike rental demand.
    - Seasons with more favorable weather conditions experience higher rental counts, while less favorable conditions may require promotional strategies to maintain customer interest.
- **Extras:**
    - Bike rentals peak on working days, indicating the influence of weekdays on rental counts.
## Recommendations:
- **Inventory Management:**
    - Utilize weather forecasts and historical rental patterns to adjust inventory levels accordingly.
    - Ensure an adequate number of bikes are available during periods of high demand, such as clear or partly cloudy conditions, while scaling back inventory during adverse weather conditions like heavy rain or snow.
- **Promotional Strategies:**
    - Offer promotions, discounts, or package deals during peak demand periods to attract more customers and increase revenue.
    - Develop targeted marketing campaigns that highlight the benefits of biking in favorable weather conditions, enticing customers to rent bikes during peak seasons.
- **Flexible Pricing Models:**
    - Implement flexible pricing models that adjust rates based on weather conditions and demand levels.
    - Offer tiered pricing structures where rental rates increase during peak demand periods and decrease during off-peak times, encouraging customers to rent bikes during less busy periods.











