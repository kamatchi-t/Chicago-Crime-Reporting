# Chicago-Crime-Reporting
To obtain insights into the crimes happened in Chicago and future predictions
Objective:
  To provide actionable insights that can shape our crime prevention strategies, ensuring a safer and more secure community. 

  Conducting a thorough analysis of this data, support strategic decision-making, improve resource allocation, and contribute to reducing crime rates and enhancing public safety.

Libraries Used:
  - import pandas as pd
  - import numpy as np
  - import seaborn as sns
  - import matplotlib.pyplot as plt
  - import plotly.express as px  
  - from sklearn.preprocessing import LabelEncoder 
  - from sklearn.svm import SVC
  - from sklearn.linear_model import LogisticRegression
  - from sklearn.neighbors import KNeighborsClassifier
  - from sklearn.model_selection import train_test_split
  - from sklearn.metrics import accuracy_score,precision_score,recall_score,f1_score,classification_report
  - from sklearn import tree
  - from sklearn.tree import DecisionTreeClassifier

Approach:
  1. #Reading the given dataset and writing it into a pandas dataframe 
  2. #dropping the unnecessary columns
  3. #dropping records with null values in the columns Latitude and Longitude since the location is crucial for analysis
  4. #The null values in the Location Description column are replaced with the value 'OTHER'
  5. Temporal Analysis: A box plot showing the different types of crimes (Primary Type) over the Years.
Insights:
The years 2022 and 2023 have seen the most cases reported especially in the categories-Motor Vehicle Theft,Offensive Involving Children, Criminal Sexual Assault,Battery.
    -#Percentage of crimes based on time of the day
Insights:
  Pecentage of Crimes from 12AM to 11:59 AM : 0.03825081168831169
  Pecentage of Crimes from 12PM to 11:59 PM : 0.061181006493506496
  7. #A Scatter plot showing the distribution of crimes over the years and the number of arrests taken place for the same.
Insights:
The number of cases resulting in arrest are very less compared to that without any arrest
  8. Geospatial Analysis:
     - picking the necessary columns and creating a new dataframe for district/ward level crime distribution analysis
     - #The distribution of arrests across different wards: sns.scatterplot(data=df,x='Ward',y="Primary Type",hue="Arrest")
     - #Plotly heatmap to show the crimes distributed across various districts
          fig2 = px.density_heatmap(df, x="Primary Type", y="District",hover_name ="District",
                          width=600,height=800,color_continuous_scale ='Greens')

  9. Crime Type Analysis- Distribution of Crime Types: Analyze the frequency of different 'Primary Type' and 'Description' fields to understand the most common types of crimes.
     Scatter Plot showing the different subtypes of Primary Type Crimes and their counts
     fig = px.scatter(df_desc_gp, x="Description", y="Crime count",color="Primary Type", width=1300,height=1000)
  10. A histogram showing the arrest for crimes classified as domestic and non domestic in various crime types
      fig = px.histogram(df_dom_gp, x="Primary Type",y='Crime count',color='Domestic',pattern_shape='Arrest',       width=1000,height=1000,hover_data=df_dom_gp.columns)
  11. Histogram showing the distribution of crimes according to time of the day it occured and the arrest done
  12. Location-Specific Analysis- Location Description Analysis: Investigate the most common locations for crimes (e.g., streets, parking lots, apartments) and see how crime types vary by location.
  13. A Histogram showing locations with high occurances of crimes
fig = px.histogram(df_locn_gp, x="Primary Type",y='Crime count',color='Location Description', width=1200,height=1000,hover_data=df_locn_gp.columns)
  14. The Percentage of Arrests in the given sample
Arrest_Percentage=(len(df[df2['Arrest']==True]))/(len(df2))
print("Percentage of Arrests: ",Arrest_Percentage)
  #Percentage of Arrests:  0.0159
  15. Predictive Modeling and Risk Assessment- Predictive Analysis: Develop models to predict future crime incidents based on historical data, time, location, and other relevant factors.
      -Risk Assessment: Assess the risk of different areas and times for specific types of crimes to help in resource allocation for law enforcement.
    16. The sample dataset is split into test and train datasets and the various classification model such as LogisticRegression(),KNeighborsClassifier(),SVC(),DecisionTreeClassifier() and their accuracy_score,precision_score,recall_score,f1_score are calculated.




