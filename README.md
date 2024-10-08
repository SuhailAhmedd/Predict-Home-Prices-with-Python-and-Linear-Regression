# Predict Home Prices with Python and Linear Regression

**Prerequisites:** Python fundamentals  
**Versions:** Anaconda Online  

## Introduction

Have you ever wanted to know how much an apartment or house costs to rent or own in your area? How do machine learning and statistics work with a powerful programming language like Python?

Machine learning is a major field that lets computers take in data and learn patterns to make predictions and decisions. We will be using Python to learn about one of the fundamentals of predictive modeling in machine learning and, more specifically, linear regression. To help us out, we will use a few data science libraries:

- Scikit-learn
- Pandas
- NumPy
- Matplotlib

## Linear Regression

In statistics, linear regression is used to model relationships between independent x variables (e.g., house sizes) and a dependent y variable (e.g., house prices) by fitting a linear equation to observed data. Put simply, we are drawing a straight line through a dataset to map out and predict. In data science, linear regression is widely used for tasks such as predicting sales, analyzing economic trends, and understanding the impact of variables on an outcome.

In this project, we will create a linear regression model to predict house prices based on house sizes. Using a scatterplot of test data, the model will form a relationship between the two variables and then make predictions.

## Getting Set Up with Anaconda

This project will show you how to use predictive modeling on the Anaconda Online editor. We are eliminating the need for local installations. Anaconda Online uses integrated Jupyter Notebooks and powerful package management that make running complex programs, including linear regression, super easy.

**Note:** To use the editor, make sure you've signed up for a free account.

1. Begin by opening your web browser and visiting Anaconda Online.
2. Next, sign into your account to get to the homepage.
3. Then, select "Launch Notebook" under the "Code Online" section.

## Our Tools of Choice

Libraries! Gotta love 'em. In this project, we will be using the following Python libraries for data analysis, data visualization, and machine learning:

- **NumPy** offers a robust foundation for numerical operations and data analysis.
- **Pandas** lets you analyze, clean, explore, and manipulate data from different sources.
- **Matplotlib** transforms your data into compelling visuals like 2D graphs and bar charts.
- **Scikit-learn**, commonly known as Sklearn, provides a user-friendly interface for all kinds of machine learning.

If you ever wondered how “prediction” charts are created in Python, the odds are that 1 of these 4 tools was involved. They make it easy for beginners to unlock the power of Python in data science.

After launching Notebook on Anaconda, open a new project.

## Getting Started

In this project, we will be using a data set that compares house size and house prices of properties recently sold in Brooklyn's Dumbo neighborhood to predict the cost of houses based on size.

**Note:** This data was gathered from Zillow.

To get started, let's import the libraries. Remember that since you are using an online emulator there is no need for local installations. This is a simple setup for linear regression using the scikit-learn library.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
```

For a quick refresher, we imported the following libraries:

- **numpy** for numerical operations (aliased as np).
- **pandas** for reading and analyzing data (aliased as pd).
- **matplotlib.pyplot** for plotting graphs of the data (aliased as plt).
- **train_test_split** from **sklearn.model_selection** for training and testing the model.
- The **LinearRegression** class from **sklearn.linear_model** for implementing linear regression.

Next, let's import some data. You will need to download the data set and upload it to Anaconda.

This CSV file contains 59 pairs of data points. After uploading it, let's add the following code:

```python
# Load data from CSV file
data = pd.read_csv('home_dataset.csv')
 
# Extract features and target variable
house_sizes = data['HouseSize'].values
house_prices = data['HousePrice'].values
```

We are using `pd.read_csv()` to read the CSV file. Next, we are extracting the values corresponding to the features on the data sheet. In this case, the data from the column named “HouseSize” is being added to the house_size variable.

Let's now get started on plotting the data via the plt object from Matplotlib.

First, we use `plt.scatter()` to create a scatter plot of house prices vs. house size. Next, we assign a title and labels for the x- and y-axes. Then, we use `plt.show()` to display the graph.

```python
# Visualize the data
plt.scatter(house_sizes, house_prices, marker='o', color='blue')
plt.title('House Prices vs. House Size')
plt.xlabel('House Size (sq.ft)')
plt.ylabel('House Price ($)')
plt.show()
```

At this point, we can run our code to see this scatter plot by selecting the "run" button at the top of the notebook file.

## Train Test

Now that we have extracted our data and plotted it on a graph, it's time for the linear regression part.

A train-test splits the generated data into training and testing sets using the `train_test_split()` function from Sklearn.

The train test split is a model validation procedure commonly used in predictive machine learning to simulate how a model will work with new/unknown data. It is commonly used with large data sets or when you need a quick estimate.

Let's now add the following:

```python
# Split the data into training and testing sets
x_train, x_test, y_train, y_test = train_test_split(house_sizes, house_prices, test_size=0.2, random_state=42)
```

The code above splits the data 80/20:

- 80% of the data will be used to train the algorithm in `x_train` and `y_train`.
- The other 20% will be used for testing the algorithm in `x_test` and `y_test`.

In this next step, we are creating and training the model to make predictions with the following code:

```python
# Reshape the data for NumPy
x_train = x_train.reshape(-1, 1)
x_test = x_test.reshape(-1, 1)

# Create and train the model
model = LinearRegression()
model.fit(x_train, y_train)
```

After preparing our data for Numpy with `.reshape()`, we can create the linear regression model with `LinearRegression()` and train it using our `x_train` and `y_train` data.

## Predicting

The model we just trained will now be able to make predictions on the test set `x_test` and `y_test`. The results are stored in the `predictions` variable.

We are now going to plot our results from our predictive modeling:

```python
# Predict prices for the test set
predictions = model.predict(x_test)

# Visualize the predictions
plt.scatter(x_test, y_test, marker='o', color='blue', label='Actual Prices')
plt.plot(x_test, predictions, color='red', linewidth=2, label='Predicted Prices')
plt.title('Dumbo Property Price Prediction with Linear Regression')
plt.xlabel('House Size (sq.ft)')
plt.ylabel('House Price (millions $)')
plt.legend()
plt.show()
```

With our plt object, we use a scatter plot to visualize the actual and predicted prices. Selecting the "run" button will show the results with blue dots and a red regression line.

![scatterplot](scatterplot.png)

## Conclusion

That's it, you have now officially trained and visualized a predictive modeling algorithm!

To take your skills to the next level, consider sourcing data and utilizing linear regression for visualization. Kaggle is a great place to find data sets that have already been proven but you can also import any data. You can use linear regression to predict so many things:

- Video game sales based on reviews.
- Social media engagement based on follower growth.
- Grades based on study time, and even recovery time based on medical data.

The possibilities are endless! Get creative and remember to format your data for easy access.

## More Resources

For additional learning and exploration, here are some resources to deepen your understanding:

- 👀 [Source code for this project](#)
- 📊 [Kaggle Datasets](https://www.kaggle.com/datasets): Explore diverse datasets for various machine learning projects.
- 🤖 [Scikit-Learn Documentation](https://scikit-learn.org/stable/documentation.html): Dive into detailed information on machine learning.
- 📖 [Pandas Documentation](https://pandas.pydata.org/pandas-docs/stable/): Learn more about data manipulation and analysis.
- 📈 [Matplotlib Documentation](https://matplotlib.org/stable/contents.html): Explore the Matplotlib documentation for creating captivating visualizations.
