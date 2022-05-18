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
mean_steps_per_participant = df2.mean()
df3 = df.assign(stepsper=mean_steps_per_participant)
print(df3.head())
