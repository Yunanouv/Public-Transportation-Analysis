# Public Transportation Analysis -  Capacity Planning for Future Growth in Transjakarta

## Business Background  
Public transportation systems are the lifelines of modern urban environments, and understanding their intricacies is crucial for improving efficiency and user satisfaction. 
Transjakarta is a Bus Rapid Transit (BRT) and non-BRT-based transportation mode that has been operating since 2004 in Jakarta and the surrounding. Transjakarta is a form of integrated and traffic-free management of public transportation in Jakarta. Transjakarta aims to break down congestion, provide easy access, and become the choice of public transportation for Jakarta residents. 

Through this project, I've utilized Python for data analysis and Tableau for visualization to uncover valuable insights into Transjakarta's operations. My objective is to demonstrate how data-driven strategies can enhance performance and better serve the citizens of Jakarta by defining the business problem itself. 

## Business Problem  
![Transjakarta Overcrowded](https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/9ee5c728-cec9-45c4-913b-4264725d5f89)


Jakarta's population has steadily increased, leading to greater demand for public transportation services like Transjakarta. This population growth exacerbates overcrowding issues during peak commuting hours. 
Some corridors or periods experience consistently high demand or overcrowding issues, leading to suboptimal service quality and customer satisfaction. The public transportation system needs to anticipate and accommodate future increases in passenger demand to ensure adequate capacity and service quality.  

## Goals 

- **Identify High-Demand Corridors**  
  Identify corridors and time periods with consistently high levels of demand or overcrowding based on historical data analysis.
- **Forecast Future Demand**  
Develop accurate forecasts of passenger demand for different corridors and time periods based on historical data analysis.
- **Plan for Capacity Expansion**
Identify corridors and time periods with projected increases in demand and plan for capacity expansion accordingly, including the addition of new routes, vehicles, or infrastructure.

## Data Overview   

| Feature Name | Description |
| --- | --- |
|**1.	transID** | Unique transaction id for every transaction |
|**2.	payCardID** | Customers main identifier. The card customers use as a ticket for entrance and exit|  
|**3.	payCardBank** | Customers card bank issuer name|
|**4.	payCardName** | Customers name that is embedded in the carde|
|**5.	payCardSex** | Customers sex that is embedded in the card |
|**6.	payCardBirthDate**|Customers birth year |
|**7.	corridorID** |Corridor ID / Route ID as key for route grouping |
|**8.	corridorName** | Corridor Name / Route Name contains Start and Finish for each route |
|**9.	direction** | 0 for Go, 1 for Back. Direction of the route |
|**10.	tapInStops** | Tap In (entrance) Stops ID for identifying stops name  |
|**11.	tapInStopsName** | Tap In (entrance) Stops Name where customers tap in |
|**12.	tapInStopsLat** | Latitude of Tap In Stops |  
|**13.	tapInStopsLon** | Longitude of Tap In Stops |
|**14.	stopStartSeq** | Sequence of the stops, 1st stop, 2nd stops etc. Related to direction |
|**15.	tapInTime** | Time of tap in. Date and time |
|**16.	tapOutStops** | Tap Out (Exit) Stops ID for identifying stops name|
|**17.	tapOutStopsName** | Tap out (exit) Stops Name where customers tap out|  
|**18.	tapOutStopsLat** | Latitude of Tap Out Stops |
|**19.	tapOutStopsLon** | Longitude of Tap Out Stops |
|**20.	stopEndSeq** | Sequence of the stops, 1st stop, 2nd stops etc. Related to direction |
|**21.	tapOutTime** |Time of tap out. Date and time |
|**22.	payAmount** | The number of what customers pay. Some are free. Some not |
<br>

1. This dataset has 37,900 records with 22 features about transportation (Transjakarta).  
2. There are 10 features containing null values, the `corridorID`, `corridorName`, `tapInStops`, `tapOutStops`, `tapOutStopsName`, `tapOutStopsLat`, `tapOutStopsLon`, `stopEndSeq`, `tapOutTime`, and `payAmount`.    
3. After exploring and deep analysis, the `corridorID` and `corridorName` have a correlation where the corridor ID has its corresponding name, and the same thing also applied to `tapInStops` - `tapInStopsName` and `tapOutStops` - `tapOutStopsName, so we can map the null values using its corresponding name. 
4. `payAmount` has 3 types of amount, there are :  
   - 0 : JakLingko  
   - 3500 : Transjakarta  
   - 20000 : Royal Trans
  We also found that `payAmount` has correlation with `corridorID` where `corridorID` has its own pay amount. 
  
<br>  

## Data Analysis  
### 1. Demographic Analysis  
**a. Age Group Distribution** <br>
<img width="800" alt="image" src="https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/5d57f300-953f-4814-a1ab-1dc9778f942f">  
<br>  
Based on [this source](https://www.mentalfloss.com/article/609811/age-ranges-millennials-and-generation-z), we can group the age of passengers to see the age distribution.  
Age Group by Generation:  

- Baby Boomer : 1946 - 1964  
- Gen X : 1965-1980  
- Millenials : 1981-1996  
- Gen Z : 1997-2012

Based on the age group distribution analysis presented in the bar chart and pie chart:

- Millennials as the Largest User Group
The bar chart shows that Millennials (born between 1981 and 1996) are the largest user group of Transjakarta services, with a total count of 17,847 transactions. This indicates that nearly half of the users fall within this age group. The pie chart confirms this, showing that Millennials constitute 48.9% of the total transactions.

- Significant Usage by Gen Z Gen Z (born between 1997 and 2012) follows as the second-largest group, with 11,574 transactions, accounting for 31.7% of the total transactions. This indicates that younger users are also a major segment of Transjakarta's user base.

- Moderate Use by Gen X Gen X (born between 1965 and 1980) represents a smaller portion of the user base, with 6,284 transactions, which translates to 17.2% of the total transactions. This suggests that middle-aged users are moderately using the services.

- Minimal Use by Baby Boomers Baby Boomers (born between 1946 and 1964) are the smallest user group, with only 798 transactions, making up 2.2% of the total transactions. This indicates that older users are the least likely to use Transjakarta services.

**b. Vehicle Type Distribution**  <br> 
<img width="800" alt="image" src="https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/6364a313-26a9-4d8d-9589-1327da624234">
<br>
Based on the vehicle type distribution analysis presented in the bar chart and pie chart:  
**Trans Jakarta Dominance** from the bar chart shows that the majority of transactions are attributed to Trans Jakarta, with a total count of 18,393 transactions. This indicates that Trans Jakarta is the most utilized vehicle type among passengers.

**Significant Use of Jak Lingko Jak Lingko** follows closely with 16,423 transactions. This suggests that Jak Lingko also plays a significant role in the public transportation network, catering to a substantial portion of the passenger demand.

**Limited Use of Royal Trans Royal Trans** has the least number of transactions, with only 1,687 transactions. This indicates that Royal Trans is the least utilized vehicle type among the three, possibly due to its fare amount since its the highest.

Proportional Representation The pie chart provides a clear visual representation of the ratio of vehicle types:

- Trans Jakarta constitutes 50.4% of the total transactions.
- Jak Lingko accounts for 45.0% of the total transactions.
- Royal Trans makes up a smaller proportion with 4.6% of the total transactions.  

**c. The Comparison Between Gender Based on Vehicle Type**  <br>  
<img width="750" alt="image" src="https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/4b693af5-7286-4c4b-b71f-75814f5bef9f">
<br>  

Jak Lingko is more frequently used by females compared to males.  
Both genders have a relatively low and almost equal usage of Royal Trans, with females slightly higher.  
Trans Jakarta has a higher usage by females compared to males, similar to Jak Lingko.   

Overall Insights

Across all vehicle types, female users tend to have higher transaction counts compared to male users. The highest usage for both genders is observed in Trans Jakarta, followed by Jak Lingko, and the least usage is in Royal Trans. The pattern indicates that public transport services might consider focusing on improving and tailoring their services towards the preferences and needs of female users, especially since they form a significant proportion of the user base.  
<br>

**d. Pay Card Bank and Vehicle Type** <br>  
<img width="750" alt="image" src="https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/07b63842-bdc1-425c-897d-790692dd1b1e">
<br>  

- **High Transaction Volume for Specific Banks:**
DKI and BRI (BRIZZI) have the highest transaction volumes among the paycard banks, with DKI leading significantly for both Transjakarta and Jak Lingko vehicles.
E-MONEY also shows a considerable number of transactions, especially for Transjakarta.  

- **Vehicle Type Preferences:**
The chart indicates a strong preference for Transjakarta vehicles when using the DKI and E-MONEY paycards.  
Jak Lingko vehicles see a high transaction volume with DKI and BRIZZI paycards.  
Royal Trans has the lowest transaction volume across all paycard banks, indicating it is the least used vehicle type among the three.

**e. Peak Hours Analysis**  <br>  
<img width="750" alt="image" src="https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/49cf3617-b3a8-4026-8557-62d0f96c37cc">
<br>  
**Peak Usage Times**   
The busiest times for Transjakarta are during the morning (5-9 AM) and evening (4-7 PM) rush hours, indicating high commuter traffic during these periods.  
**Off-Peak Times**  
Midday (10 AM - 2 PM) sees significantly lower usage, suggesting these hours could be used for maintenance or service adjustments.
These insights can help in planning service frequency and capacity to meet high demand during peak hours and optimize operations during off-peak times.

### 2. Business Analysis  

**a. Peak Days Identification**  <br>  
<img width="850" alt="image" src="https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/7886f68d-2fa2-4eff-a8d5-3c9daa0f4913">
<br>   
**Weekday vs. Weekend Usage**   
Transjakarta sees higher usage during weekdays compared to weekends, suggesting that it is predominantly used for commuting purposes.
**Special Attention to Peak Days**   
The spike on April 14th could be due to a special event or increased commuter activity, warranting further investigation to understand the cause and prepare for similar future occurrences.

**b. Peak Hours Identification based on Peak Dates**  <br>  
<img width="850" alt="image" src="https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/ba432427-fdb1-4749-8229-ff0443f6eddf">
<br>  
**Morning Peak**
The highest transaction volume occurs at 6 AM, with a sharp peak exceeding 1,400 transactions.  
There is a noticeable drop in transactions following the 6 AM peak, stabilizing around 700-800 transactions by 7 AM.  

**Evening Peak**  
Another significant peak occurs at 5 PM, with transactions spiking again to around 1,200 transactions.  
Post-5 PM, there is a gradual decline in transactions through the evening.  

**Low Activity Periods**
The lowest transaction volumes are observed during the midday hours, specifically between 10 AM and 3 PM.  

**Consistent Patterns on Peak Dates**
The transaction trends for the peak dates (April 13, 14, 17, 18, and 19) consistently show two main peaks at 6 AM and 5 PM.  
<br>

**c. Crowded Corridors**  <br>  
<img width="850" alt="image" src="https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/5df5760b-d5e9-470d-b905-7e08001af647">  
<br>  

From graph and also analysis for most active corridors, the crowded corridor goes to Rusun Flamboyan - Cengkareng with 2021 total transactions in 29 active days.  
<br>  

**d. Rusun Flamboyan-Cengkareng** <br>  
  **1. Daily Transcations in Rusun Flamboyan-Cengkareng**  <br>
  <img width="850" alt="image" src="https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/3043f61a-fb71-4fae-a62e-0a83d7dd04e7">
<br>

    - Peak Transaction Day  
    The highest transaction volume was observed on April 19, with over 100 transactions. This indicates a significant spike in activity on this day.  
    
    - Consistent Highs and Lows  
    There are several other days with high transaction volumes exceeding 80 transactions, notably at the beginning of the month (April 3 and 5) and mid-month (April 17).
    The lowest transaction volumes are generally observed on weekends, particularly around April 7-8 and April 21-22, where transactions drop close to zero.   
    
    - Weekend Trends  
    The graph shows noticeable dips in transaction activity during weekends, suggesting that fewer people are using Transjakarta services on these days.  
    
    - Weekday Patterns    
    Weekdays show more consistent transaction volumes, with fluctuations indicating varying levels of daily usage but generally higher than weekends.
<br>

  **2. Hourly Transaction Count by Vehicle Type**  <br>
  <img width="850" alt="image" src="https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/8acfb338-c651-4afb-9866-a16ad8152690">
<br>
  The graph above shows the transaction in Rusun Flamboyan - Cengkareng based on vehicle type. Jaklingko shows the highest transaction, follows by Transjakarta and Royal Trans.

  **3. Forecast Future Demand** <br>
  <img width="850" alt="image" src="https://github.com/Yunanouv/Public-Transportation-Analysis/assets/146415555/c3cc6b1c-46f9-4c69-a037-aa88ecf61c30">
<br>  
  From the previous graph where we know the total transactions for each vehicle type, we can forecast future demand based on capacity for each vehicle type.  
Based on the [official Twitter](https://x.com/PT_Transjakarta/status/1396816204652703745) of TransJakarta, the capacity of Transjakarta is 30 people.   
Based on [this article](https://poskota.co.id/2022/01/29/angkot-ac-mikrotrans-resmi-beroperasi-di-jakarta-begini-spesifikasi-mewahnya), the capacity of Jak Lingko is 11 people at max.  
Based on [this article](https://www.ranselaryani.com/royal-trans-jurusan-bekasi-barat-blok-m-dan-rute-terbaru/), the capacity of Royal Trans is 43 people at max.  

<br>  

## Business Recommendation  

Based on the analysis of the hourly vehicle needed data for the "Rusun Flamboyan - Cengkareng" corridor, we can make the following business recommendations:  
  
### 1. Peak Hours Optimization  
Identify the peak hours when the demand for vehicles is high. During these hours, ensure that there are enough vehicles available to meet the demand. Consider deploying additional vehicles or adjusting schedules to accommodate the peak demand.   

### 2. Resource Allocation  
Allocate resources efficiently based on the hourly variation in vehicle demand. Prioritize the allocation of vehicles to hours with the highest vehicle needed to ensure optimal utilization of resources.  

### 3. Service Improvement  
Monitor the vehicle needed trends over time and identify any patterns or recurring issues. Use this information to improve service quality and ensure that vehicles are available when needed, enhancing customer satisfaction.  

### 4. Capacity Planning  
Use the insights from the analysis to inform capacity planning decisions. Consider investing in additional vehicles or adjusting the capacity of existing vehicles to align with the demand fluctuations observed throughout the day.  

By implementing these recommendations, the transportation service can improve operational efficiency, enhance customer satisfaction, and optimize resource utilization, ultimately leading to a more sustainable and profitable business model.  

Please checkout my Transjakarta [dashboard](https://public.tableau.com/app/profile/yuna.nouv/viz/TransJakarta_17176923334730/MainDashboard?publish=yes) and [story](https://public.tableau.com/app/profile/yuna.nouv/viz/TransJakarta_17176165985990/TJStory?publish=yes).  
Thank You!
