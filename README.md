## Devloped by: AKASH CT
## Register no: 212224240007

# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 19/8/25

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

data = pd.read_csv("IMDB Top 250 Movies (1).csv")

data['year'] = pd.to_numeric(data['year'], errors='coerce')
data = data.sort_values('year')

data['rating_diff'] = data['rating'].diff()


data['rating_sea_diff'] = data['rating'] - data['rating'].mean()


data['votes_log'] = np.log(data['rating'])


data['votes_log_diff'] = data['votes_log'].diff()


data['votes_log_sea_diff'] = data['votes_log'] - data['votes_log'].mean()
```
```
import matplotlib.pyplot as plt

fig, axes = plt.subplots(6, 1, figsize=(12, 15))

plt.subplot(6, 1, 1)
plt.plot(data['year'], data['rating'], label="Rating")
plt.legend(loc='best')
plt.title('Original Ratings over Years')
plt.xlabel('Year')
plt.ylabel('Rating')

plt.subplot(6, 1, 2)
plt.plot(data['year'], data['rating_diff'], label="Diff(Rating)")
plt.legend(loc='best')
plt.title('Rating Differencing')
plt.xlabel('Year')
plt.ylabel('Diff(Rating)')

plt.subplot(6, 1, 3)
plt.plot(data['year'], data['rating_sea_diff'], label="Rating - Mean")
plt.legend(loc='best')
plt.title('Seasonal Adjustment (Deviation from Mean)')
plt.xlabel('Year')
plt.ylabel('Rating - Mean')

plt.subplot(6, 1, 4)
plt.plot(data['year'], data['votes_log'], label="Log(Votes)")
plt.legend(loc='best')
plt.title('Log Transformation of Votes')
plt.xlabel('Year')
plt.ylabel('Log(Votes)')

plt.subplot(6, 1, 5)
plt.plot(data['year'], data['votes_log_diff'], label="Diff(Log(Votes))")
plt.legend(loc='best')
plt.title('Log Transformation + Differencing')
plt.xlabel('Year')
plt.ylabel('Diff(Log(Votes))')

plt.subplot(6, 1, 6)
plt.plot(data['year'], data['votes_log_sea_diff'], label="Log(Votes) - Mean")
plt.legend(loc='best')
plt.title('Log Transformation + Seasonal Adjustment')
plt.xlabel('Year')
plt.ylabel('Log(Votes) - Mean')

plt.tight_layout()
plt.show()

# Extra trend plot
data.plot(x='year', y='rating', kind='line', figsize=(12,6), title="Ratings Trend")
plt.show()
```




### OUTPUT:
### Original Data:
<img width="1323" height="267" alt="image" src="https://github.com/user-attachments/assets/45e389d9-4153-4c3a-b50f-7198258de3d5" />

### REGULAR DIFFERENCING:
<img width="1272" height="253" alt="image" src="https://github.com/user-attachments/assets/89bffb7f-2dce-4590-ae1a-5d446bc65a05" />



### SEASONAL ADJUSTMENT:
<img width="1321" height="284" alt="image" src="https://github.com/user-attachments/assets/26c5fafe-7b82-4582-858e-a24f59ebfe26" />


### LOG TRANSFORMATION:
<img width="1307" height="269" alt="image" src="https://github.com/user-attachments/assets/7cfded20-c489-4de7-bb65-63fc0c1626f6" />

### LOG TRANSFORMATION+ DIFFERNECING:
<img width="1281" height="262" alt="image" src="https://github.com/user-attachments/assets/51689191-1cc2-4c32-8499-91dbe769e014" />

### LOG TRANSFORMATION + SEASONAL ADUJUSTMENT:
<img width="1260" height="268" alt="image" src="https://github.com/user-attachments/assets/7cc47f15-f9d8-4121-8f33-caa70b4b5fd8" />

### Ratings Trend:
<img width="1343" height="718" alt="image" src="https://github.com/user-attachments/assets/3ab05278-e06f-45ae-b042-071731807212" />







### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
