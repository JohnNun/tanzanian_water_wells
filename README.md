# Tanzanian Water Wells
by Jonathan Nunez

# Overview
The country of Tanzania struggles with providing clean water to its population of 57,000,000. As it is now, there are many water points that have already been built throughout the country, with some needing repairs while others have failed altogether. By using the data collected on the Tanzanian water wells, and K-Nearest Neighbors (KNN) classification algorithm I build a classification model to predict the condition of a water point as either 'functional' or 'non-functional'. Through the use of this predictive model, the government of Tanzania may be able to effectively and efficiently allocate the resources to locations that are in desperate need of repairs.

# Business and Data Understanding
As a developing country, Tanzania struggles with providing clean water to its population of over 57,000,000. As it is now, there are many water points that have already been built throughout the country, but some need repair while others have failed altogether. The government of Tanzania may not have the necessary resources to be able to effectively and efficiently check and repair all pumps, and wells at the same time. By using a predictive classifier model the Tanzania government hopes to be able to predict which pumps or wells may need repairs to effectively send out technicians to complete said repairs.

By using information about the kind of pump, year of installation, etc. I am to build a prediction classifier to predict the condition of a water well or pump as either 'functional' or 'non-functional'. Through the predictions of the model, the government of Tanzania may be able to effectively and efficiently allocate the necessary resources to locations that are in desperate need of repairs.

The data used for this project was gathered from **[Taarifa](https://taarifa.org/)** and **[Tanzanian Ministry of Water](https://www.maji.go.tz/)**. The information that can be found in this data set **ranges from the year the pump, water well, etc. was first constructed, to who funded the construction of that specific water source**. This dataset also provides an abundance of categorical data, for example longitude/latitude, type of water being pumped, etc. In total this dataset holds **information on over 50,000 plus water sources ranging from first constructed in 1966 up to 2010**, and even water sources that are yet to be fully constructed. Since I am trying to predict which pumps and wells are in need of repairs to provide clean water to its population, I will be primarily be focusing on rows and columns for pumps and water wells that have a civilian population who heavily rely on these pumps and wells for water. 

# Modeling
The model used for this project is **K-Nearest Neighbors (KNN)**. I went with this classifier as its non-parametric, meaning it doesn’t make assumptions based on how the data is distributed. KNN can also adapt fairly easily to new examples or data points. Because data is stored in memory, when there is new data present, it will adjust and incorporate the new information into future predictions.

As stated above, this data is full of categorical values, so in order to be able to use this data properly with a KNN classifier, I first turn categorical data into numerical values. Since our current data is heavily weighted towards 'functional', this can easily cause biases in the model's prediction result. To help lower the model bias as much as possible I use Synthetic Minority Over-sampling Technique (SMOTE) to generate synthetic data based off the data already present to make the data as even as possible. Since KNN is a distance-based machine learning algorithm, I scale the data with a Min Max scaler. I went with a min max scaler to ensure all features are taken into consideration equally and to further lower the potential of a model bias.

# Evaluation
For this project, the **"non functional" category is seen as the positive outcome, and "functional" as the negative** since we are trying to find which pumps and/or wells are in need of repairs. The final model in the [Tanzanian Water Wells Jupyter Notebook](tanzanian_water_wells_notebook.ipynb), gives the lowest false negatives, and almost the lowest false positive. In this case, a lower false negative is beneficial because that means **the model is able to properly categorize between "functional" or "non functional"**. As for the false positives, the final model appears to be putting about 10% as "non functional" but may be actually "functional", considering the overall size of the of the dataset of 50k+ rows, a total of 5k of “non functional” but may possibly actually “functional”.

In terms of performance, the final model got an **average of 83 for its classification scores with the test data**, these results are very similar with those of the training data. With the model’s precision, recall, and f1-scores being almost exact, this tells us the model generalized the data well and is very unlikely to overfit new or unseen data. The final model got an ROC curve score of .92, further solidifying this model’s ability distinguishing between 'functional' and 'non functional' predictions. For cross validation scores, the final model's lowest score showed an **accuracy of 70, while the highest score calculated was an 82** so this model will do fairly well with new data when it is presented.

# Conclusion
As it is now, the final model **is able to properly categorize between "functional" or "non functional"**. When testing the model with both training and test data, the model’s precision, recall, and f1-scores were almost the exact same, this tells us the model generalized the data well making it unlikely to overfit with new or unseen data. That being said, its very possible **the model could still be fine-tuned or even tweaked further to increase the model’s precision with its predictions**. Overall, the Final KNN model is a good start when it comes to predicting which water pumps are "functional" and "non functional".

## Repository Structure
- images
- README.md
- [Presentation](tanzanian_water_wells_presentation.pdf)
- [Jupyter Notebook](tanzanian_water_wells_notebook.ipynb)
