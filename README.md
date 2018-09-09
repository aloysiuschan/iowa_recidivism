# iowa_recidivism
The Jupyter notebook contains code to predict 3-year recidivism for offenders released from prisons in the State of Iowa. Features used to predict recidivism include age, race, and nature of the offence committed.

I first use a random forest to solve the binary classification problem. However, I find that the random forest is heavily biased towards the majority class (in the dataset, non-recidivists are twice as common as recidivists), leading to extremely high specificity (99%) and extremely low sensitivity (2%) when predictions were generated for the test dataset.

Since sensitivity is more important than specificity when it comes to predicting recidivism, we want to overcome the class imbalance problem and improve the sensitivity of the random forest model. To achieve this, I assign higher weights to the minority class; this improves the sensitivity of the random forest model to 64%, and reduces the specificity to 55%. Note that upsampling the minority class or downsampling the majority class in the training set will lead to approximately the same outcome (code omitted for brevity).

I also note that although sensitivity was improved to 64%, there is still much room for improvement. We can probably improve the model's sensitivity (and specificity) if better features (e.g. history of drug abuse, history of psychological disorders) are made available.

The data, which spans from 2010 to 2017 and contains 21646 observations, was obtained from the State of Iowa's data portal: https://data.iowa.gov/Public-Safety/3-Year-Recidivism-for-Offenders-Released-from-Pris/mw8r-vqy4
