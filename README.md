# Phase-1-Analysis-of-Multivariate-Data

Project Objective:
The data is derived from a manufacturing company. The attributes of the process represents different manufacturing parameters. Given data has 209 attributes and 533 observations. The objective of this process is to develop an anomaly detection algorithm that detects any deviation from quality control standards. 

Approach:
The very first approach is to look for missing values and outliers. Since the data given has no missing values, I looked for the outliers in data. The company has specified that if there are any outliers, it has to treated as deviation in parameter and not error in measurement. Also the objective is to develop an anomaly detection algorithm so removing outliers doesn't make any sense.
Now I looked forward to calculate ranges of each attributes. This is very crucial step given the fact that each parameter has different unit and some parameters can provide redundunt information. To tackle this problem I have applied multivariate analysis on this data.
Another problem with this data is that it doesn't has high n/p ratio (i.e not sufficient observations). To tackle this problem I have applied Principal Componant Analysis for dimention reduction and to remove curse of dimentionality.
After applying PCA, I have leveraged pareto chart to select important Principal Components. I have selected 4 PCs that explains 93% of variation of original the data. Hence I reduced the dimentionality from 209 parameters to 4 PCs while retaining 93% information.  
For anomaly detection I have applied concepts of T2 Hotelling control chart and multivariate CUSUM (Cumulative Sum) approach. I idea behind applying two concepts is to provide ability to detect two types of anomaly: 
1) Gradual but small change 
2) Sudden but sharp change

m-CUSUM chart enables the algorithm to detect type 1 kind of anomaly because m-CUSUM chart has cumulative memory which helps to track gradual deviation from the QC standards. m-CUSUM uses memory of mean of each parameter hence it will enable the algorithm to detect deviation in mean.
T2 hotelling chart enables the algorithm to detect type 2 kind of anomaly because T2 chart uses statistical distance instead of cartesian distance. Statistical distance has variation term in it which helps to detect changes in variation of data eventhough the mean remains the same. This is critical from the point of view of maintaining variation of system under control. 
Since both of this charts are used simultaneously, the quality control department has ability to detect any kind of anomaly in process.
The upper control limit has significance level of 95% (alpha = 5%) which produces Average Run Length (ARL0=500) which means that on average the chats will send an alarm after 500 instances. ARL=500 is good from the fact that the false positive rate is low. The UCL follows Chi Squared distribution which depends on Alpha. Hence for tighter QC, one can increase significance level of the charts.
