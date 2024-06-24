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
1. Demographic Analysis

2. Business Analysis 
