# Future-slum-prediction
This code is used for predicting future slum growth based on LULC change in Kibera and Katanga using a Python-based regression model.
#start with Kibera, Nariobi , kenya
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
from sklearn.linear_model import LinearRegression

# years = (Kibera slum)
years = np.array([2000, 2003, 2006, 2009, 2012, 2015, 2018, 2021, 2024]).reshape(-1, 1)

data = {
    'BL': [14.2, 7.5, 2.2, 1.8, 0.1, 2.7, 0.9, 2.7, 4.9],
    'BA': [82.7, 86.7, 91.2, 93.0, 95.1, 95.8, 96.0, 94.7, 93.0],
    'VC': [1.3, 4.3, 5.8, 5.2, 4.9, 3.5, 3.1, 2.6, 2.1],
    'WD': [1.8, 1.5, 0.8, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
}

classes = ['BL', 'BA', 'VC', 'WD']
colors = ['blue', 'green', 'red', 'purple']
titles = ['BL Class', 'BA Class', 'VC Class', 'WD Class']

plt.figure(figsize=(12, 7))
for i, cls in enumerate(classes):
    y = np.array(data[cls])
    model = LinearRegression()
    model.fit(years, y)
    trendline = model.predict(years)
    year_2030 = np.array([[2030]])
    prediction = model.predict(year_2030)[0]

    ax = plt.subplot(2, 2, i+1)
    ax.plot(years, y, 'o-', color=colors[i], label='Observed')
    ax.plot(years, trendline, '--', color=colors[i], label='Trendline')
    ax.plot(2030, prediction, 'ro', label=f'2030 Prediction: {prediction:.2f}%')

    ax.set_title(f"{titles[i]} Built-up Area (2000–2030)")
    ax.set_xlabel("Year")
    ax.set_ylabel("Built-up Area (%)")

    # Grid removed (no ax.grid call here)
    ax.legend()

plt.tight_layout()
plt.savefig("Kibera_2030_predictions.png", dpi=300)
plt.show()
# second, Katanga,kampala,UGanda.
import matplotlib.pyplot as plt
import numpy as np
from sklearn.linear_model import LinearRegression

# Years (Katanga slum)
years = np.array([2000, 2003, 2006, 2009, 2012, 2015, 2018, 2021, 2024]).reshape(-1, 1)

# Percentage data from your table for BL, BA, VC, WD
data_percent = {
    'BL': [0, 0, 0, 21.2, 2.7, 12.5, 6.6, 1.8, 2.18],
    'BA': [64.5, 65.1, 67.7, 67.9, 69.9, 70.3, 70.7, 90.4, 93.15],
    'VC': [29.3, 28.9, 32.3, 10.9, 27.4, 17.1, 22.7, 3.8, 4.67],
    'WD': [6.2, 5.9, 0, 0, 0, 0, 0, 0, 0]
}

classes = ['BL', 'BA', 'VC', 'WD']
colors = ['blue', 'green', 'red', 'purple']
titles = ['BL Class', 'BA Class', 'VC Class', 'WD Class']

plt.figure(figsize=(12, 7))
for i, cls in enumerate(classes):
    y = np.array(data_percent[cls])
    model = LinearRegression()
    model.fit(years, y)
    trendline = model.predict(years)
    year_2030 = np.array([[2030]])
    prediction = model.predict(year_2030)[0]

    ax = plt.subplot(2, 2, i+1)
    ax.plot(years, y, 'o-', color=colors[i], label='Observed')
    ax.plot(years, trendline, '--', color=colors[i], label='Trendline')
    ax.plot(2030, prediction, 'ro', label=f'2030 Prediction: {prediction:.2f}%')

    ax.set_title(f"{titles[i]} Built-up Area (2000–2030)")
    ax.set_xlabel("Year")
    ax.set_ylabel("Built-up Area (%)")

    # No grid lines
    ax.legend()

plt.tight_layout()
plt.savefig("Kibera_2030_predictions_newdata.png", dpi=300)
plt.show()
