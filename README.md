# Healthcare-in-Different-States
In this project, I used boxplots to investigate the way hospitals in different states across the United States charge their patients for medical procedures.


import pandas as pd
from matplotlib import pyplot as plt

healthcare = pd.read_csv("healthcare.csv")
# print(healthcare.head())
# print(healthcare["DRG Definition"].unique())

chest_pain = healthcare[healthcare['DRG Definition'] == '313 - CHEST PAIN']

alabama_chest_pain = chest_pain[chest_pain['Provider State'] == "AL"]

costs = alabama_chest_pain[' Average Covered Charges '].values

states = chest_pain["Provider State"].unique()
datasets = []
for state in states:
  datasets.append(chest_pain[chest_pain['Provider State'] == state][' Average Covered Charges '].values)

plt.figure(figsize=(20,6))
plt.boxplot(datasets, labels = states)
plt.show()
