# week-1-2-3

assignment data learning week 1,2,3
import pandas as pd
import pandas as pd
import seaborn as sns
steps = pd.read_csv("steps.csv", sep=';')
survey = pd.read_csv("survey.csv")

print (steps)
print (survey)
df = pd.merge(survey, steps, on="id")
print (df)
print (df.dtypes)

sns.displot(df["weight"])
def above_200(x):
    if(x > 200.0):
        return float('NaN')
    else:
        return x
def under_40(x):
    if(x > 40.0):
        return float('NaN')
    else:
        return x
    
df["weight"]=df["weight"].apply(above_200).apply(under_40)
df2 = df.loc[:, "20-6-2013" : "13-5-2014"]

# The mean, otherwise known as the average is the sum of all values devided by the number of values
## The mean steps per participant is the average amount of steps per day
mean_steps_per_participant = df2.mean()

df3 = df.assign(stepsper=mean_steps_per_participant)
print(df3.head())
## new dataframe check!
sns.violinplot(x=median_steps_per_participant, data=df2)

mean1 = mean_steps_per_participant.mean()
mean1
## The mean of the mean steps per day is the average of the average steps per day, the average of the average steps could be referred to as the total average  
### The mean of the mean steps per day is '8202' steps, this means the average amount of steps per day is 8203 (rounded off), 1 step is approximately 0.762 metres. This means that 8203 steps equal 6.25 km.
median1 = mean_steps_per_participant.median()
median1
# The median is the middle value in a series of values, this means that when there is an even number of values, the median is the average of the two middle values
## The median of the mean steps per participant is therefore the middle value of the average steps per day
### The median is 7856 which is quite close to the mean(average) of the mean steps per day. 
sns.boxplot(mean_steps_per_participant)
# In this boxplot you can see the mean steps per participant, you see that the boxplot ranges from 5.000 to 10.000, but there are a few outliers that range from somewhat under 5.000, to 30.000 steps. This is quite a big range. In kilometres this means it ranges from about 3,8 kilometres to 22,8 kilometres. 

df3.corr()
# In this correlation matrix you can see the correlation between the variables. Anything between 0.8 and 1, and -0.8 and -1, is statistically significant, meaning there is a correlation between the two variables. 
significance = [df3.corr() >= 0.8], [df3.corr() <= -0.8]
significance
## After filtering out the statistically insignificant values, we have now created an overview of only the statistically significant correlation. All correlations that are significant now say true. 
sns.relplot(x=median_steps_per_participant, y=mean_steps_per_participant, data=df2)
