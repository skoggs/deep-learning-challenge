Machine Learning With Alphabet Soup

# Purpose

This exercise in machine learning seeks to create a model that can predict successful projects for the nonprofit Alphabet Soup. Trained with data and results of 34,000 past applicants and powered by an algorithm, we seek to improve Alphabet Soup's future rate of success by being able to classify future applicants as likely successes or failures.

# The Data

![A quick look at Alphabet Soup data](/images/data.png "The CSV As Viewed in Google Colab")

## The Target Variable 
Since the goal of our data is to determine successful applicants, the target variable for our analysis is "IS_SUCCESSFUL". As a dependent variable, it will be separated from the rest of the data to test the impact of other variables on it.

## The Features
The features are comprised of everything we have determined could be useful in predicting the value of the target variable. These include: 

- APPLICATION_TYPE (Application type defined by Alphabet Soup)
- AFFILIATION (Whether the project is company affiliated or independent)
- CLASSIFICATION (Classification as a government organization)
- USE_CASE (The specified  purpose for the project)
- ORGANIZATION (The legal type of the organization i.e. a trust)
- STATUS (Whether the project is currently active or not)
- INCOME_AMT (How much income the project takes in, classified into buckets)
- SPECIAL_CONSIDERATIONS (Special considerations for the project, if applicable)
- ASK_AMT (How much funding is requested from Alphabet Soup for the project)

## Removed Variables
The two following variables were removed from the machine learning analysis, as their purpose is for identification and have no analytic value: 

- EIN (The employer identification number, used for tax purposes)
- NAME (The name of the organization)

# The Model

![A model screenshot](/images/model.png "Initial draft of the model, with a nixed additional layer.")

## Compiling and Training the Data. 

We attempted to play it relatively safe with the initial draft of the model for the purpose of just getting it running. Thus, it just runs a single activation function, "relu", for its hidden layer, and a "sigmoid" activation function for its output layer. While the relu function is somewhat interchangable, the sigmoid function is difficult to replace as its use of method of taking in many inputs to predict a binary outcome fits neatly into this exercise's goal. Additionally, a total number of nien neurons was selected to reflect our number of features in the data.

## Accuracy Target
The target accuracy goal for the model sat at 75%. The initial model sat at 72.3%, which is fine for an initial draft but clearly improvement to meet said goal. We used a few different methods in an attempt to further optimize the model. 

![The accuracy score](/images/accuracy.png "The accuracy score of the initial model. Optimizations would stay at aorund this figure.")

### Optimization 1
An additional hidden layer was added with functionality similar to the first, with the hopes that the extra computing power would be of use the model optimzation. This had a neglible effect, setting the accuracy to 72.4%.

### Optimization 2 
A "softplus" activation function was run in lieu of the "relu" function. Once again, there was no discernable difference in accuracy, with a score of 72.4%.

### Optimization 3
STATUS, ORGANIZATION, and SPECIAL_CONDSIDERATIONS were removed from the data set. This was done to remove some possibly confounding variables that may or may not have much predictive value. This had both a limited and negative effect at 72.2%, suggesting another dead end. 

## Results

Our overall results for the model were middling, with an accuracy score of 72.3%, falling multiple points short of the initial 75% goal and not really getting any closer via our optimization methods. While a 2.7% shortfall does not sound like a lot, it adds up fairly quickly when individual projects number in tens of thousands and demand thousands of dollars of funding each. Considering the apparent dead end, the prudent move might actually be to start over with a completely different model. By utilizing the same data set and running it through an alternative machine learning service like Amazon's SageMaker, perhaps better results can be achieved with some tinkering. 