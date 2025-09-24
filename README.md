### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 24/09/2025
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
#### Program 1:
```
import pandas as pd
df=pd.read_csv("C:\\Users\\admin\\Downloads\\clustervisitor.csv")
df
```
#### Output:
<img width="344" height="732" alt="Screenshot 2025-09-19 181402" src="https://github.com/user-attachments/assets/40d8e080-1b88-4d53-88c4-c1a41206770c" />

```
cluster = {
    'Young': df['Age'] <= 30,
    'Middle-aged': (df['Age'] > 30) & (df['Age'] <= 50),
    'Elderly': df['Age'] > 50
}
cluster

```

#### Output:
<img width="278" height="736" alt="Screenshot 2025-09-19 181414" src="https://github.com/user-attachments/assets/40ba7805-259c-44b0-a883-8924690bb7b8" />

```
count=[]
for group, condition in cluster.items():  
    visitors_in_group = df[condition]
    count.append(len(visitors_in_group))
    print(f"Visitors in {group} age group:")
    print(visitors_in_group)
    print(count)
```
#### Output:
<img width="449" height="680" alt="Screenshot 2025-09-19 181424" src="https://github.com/user-attachments/assets/0d0bb6d9-03ed-4221-9b25-a3493eade469" />


```
import matplotlib.pyplot as plt
plt.bar(cluster.keys(),count,data=df)
plt.xlabel('Age Group')
plt.ylabel('Number visitors')
plt.show()
```
#### Output:
<img width="617" height="451" alt="Screenshot 2025-09-19 181430" src="https://github.com/user-attachments/assets/6859f8af-46b2-456b-8d09-a5b340eb59e8" />

#### Program 2:
```
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

sc=StandardScaler()
df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
newdf=sc.fit_transform(df3)
newdf
```
#### Output:
<img width="343" height="534" alt="Screenshot 2025-09-19 181436" src="https://github.com/user-attachments/assets/6b012ccb-d78e-49f1-adeb-f78f94c85dbc" />


```
kmean=KMeans(n_clusters=4,random_state=42)
df3['cluster']=kmean.fit_predict(newdf)
df3
```
#### Output:
<img width="304" height="733" alt="Screenshot 2025-09-19 181445" src="https://github.com/user-attachments/assets/59239450-d668-42c4-b112-5cf163c28fa6" />


```
plt.scatter(df3['Age'],df3['Income'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income in thousands')
plt.show()
```
#### Output:
<img width="661" height="451" alt="Screenshot 2025-09-19 181452" src="https://github.com/user-attachments/assets/67ee144e-f482-4e5f-870b-aabd3a5a13c3" />




### Result:
Thus , The implement of Cluster and Visitor Segmentation for Navigation patterns in Python executed Successfully.
