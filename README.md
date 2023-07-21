# Shark attacks - Ironhack mini project
## Introduction
This project evolves around the dataset about registered (police records, newspaper articles) information about shark attacks around the world. 

**Dataset source:** https://www.kaggle.com/datasets/felipeesc/shark-attack-dataset
(can also be found in the files folder in the repository)

<img src="https://cdn11.bigcommerce.com/s-xf1j2e32mt/images/stencil/1280x1280/products/7778/9437/5d-diamond-painting-funny-shark-attack-kit-7191528898663__77437.1631110217.jpg?c=1" width = 250 alt="step1" title="Step 1" />

**Goal:** Analyse the circumstances of shark attacks and build the model which will help us to determine whether the shark attack was fatal or not. 


## Data cleaning
Provided dataset required a lot of data cleaning. Below I will explain the main steps of this process. 

### 1. Removing unnecessary columns
First of all, the original dataset consisted of 24 columns out of which many didn't provide any additional information important for our model. 
In order to avoid problems with our model I removed columns which I considered irrelevant. 

**Disclaimer:** I decided to focus on few chosen key factors for which we have the most reliable data.

For the data to be considered reliable I consider that it needs to:
- have enough information per each attack (hence dropping rows with too many NaN values - explained below)
- contain information which provides a descriptive (informs about the context) yet possible to be categorized information
- contain a quality information (for that reason I removed the column about species as in majority of cases the species weren't provided.)

I have decided to focus my model around the data regarding: 
- location
- gender
- activity
- injury
- result of the attack (fatal or not).

**Other columns were  removed from the dataset.** 

### 2. Dealing with NaNs
The initial dataset contained **too many NaN variables**. 

1. The first step was to remove the rows where there are more than 5 NaN values. I consider that for those attacks we don't have enough information to be relevant for the model. 

2. For gender, activity, injury, fatal and species columns I replaced NaN values with value "ukn" (for *unknown*). 

3. For country information I looked at the other two columns (*area, location*) to see if the information provided in there allowed me to fill in the information for country. After that I was able to remove those two columns, **leaving only country column**. 

4. Knowing the column fatal will be the target of the model, I tried to ensure as much as information there are possible. Therefore I looked at the column *injury* in order to determin wheter the attack was fatal or not. Then I removed the rows where we didn't know the result of the attack. 


### 3. Categorizing values in order to lower the value count
Since the dataset gathered information from many different sources, data wasn't standardized, a lot of columns contained very descriptive information. That led to a very high value count on most of the columns which needed to be treated to **avoid the Curse of Dimentionality**. 

For the values where it was possible to determine a pattern, I gathered the data under different labels, e.g. :
- for every injury where there was a mention of *foot*, *leg*, *knee* etc. I assigned them a value *foot or leg injury*
- for every activity where the surfing was mentioned I assigned the value *surfing*. 

## EDA
I created countplots to display the overview of data and contingency table to see the relations between columns. 

## Data processing
The next step was to prepare the data to be treated by the model. It required dummifying the categorical data. 

## Logistic regression model - training and improving
Since my final dataframe contains only categorical values, I used logistic regression model to determine whether the attack was fatal or not. 
Data isn't perfectly balanced - we have way more information about the attacks which weren't fatal so the model, even after balancing is mostly predicting that the attack will not be fatal. 

## Final conclusions

- Luckily, the probability of getting attacked by a shark with a fatal result is low. Most of the attacks are more likely not to be fatal and many end up with no injuries. 
- The highest amount of fatal shark attacks was registered in Australia. The second country is USA, followed by South Africa. 

- While many incidents happen while surfing, those have smaller fatality rate than swimming. 

- Men are more often victims of shark attacks (with both fatal and not result). 
- Leg or foor injuries are the most common results amongst all the injuries due to shark attacks. 



<img src="https://i.pinimg.com/564x/96/27/d2/9627d2075a676b12a6f5af822bb6037e.jpg" width = 300 alt="step1" title="Step 1" />



