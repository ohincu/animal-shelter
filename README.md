# Outcomes for Animals in Shelter

This project aims to predict the outcome of each pet that gets into the animal shelter. 
The possible outcomes are: return to owner, adoption, transfer, euthanasia or death.

## Case Problem & Solution
This case presents two opportunities for shelter employees:
1. When the adoption likelihood for an animal is deemed low, it presents an opportunity for shelter employees to offer additional support in finding them a new home. 
2. To ooptimize their human, financial and time resources according to the likelihood of adoption. For example, if the adoption
likelihood is low in the current situation, more efforts could be added.

## Data
The data is from an [animal shelter](https://www.austintexas.gov/austin-animal-center) in Austin, US and it includes information on animals ending up in the shelter: breed, color, sex, age, etc.
The original data can be found on [Kaggle](https://www.kaggle.com/competitions/shelter-animal-outcomes).

## Limitations
* No intake dates - it's known when the animal is adopted or returned to owner, but not when they enter the animal shelter.
That makes hard to calculate how much time it takes till e.g. adoption. and ...
* No population data - going with the latter limitation, it makes difficult understanding the animal population volumes at specific times. If there are many animals currently in the shelter, it probably lowers the adoption probability.

## Requirements
* pandas, numpy, re - for reading in and manipulations
* plotly - for visualizations
* scikit-learn - for modeling 

## Methodology
The project includes 1) feature engineering 2) EDA 3) modeling in Random Forest.

### Key Insights
**Most people like to adopt young puppies and kitties, and the adoption probability of older animals is lower.**

![](plots/outcome_age)

**Having a name is connected to being returned to the owner of being adopted.**
![](plots/outcome_name)

**Procedures such as neutering or spaying the animals could potentially increase the adoption likelihood.**
![](plots/outcome_type_by_reproduction)

### Model Results

![](plots/confusion_matrix_outcome_type)

## Conclusions

Additional data points:
- intake - could allow adjust the model and predict how much time the pet is to stay in the shelter. This could be used by shelter employees to plan their resources. 
- the circumstances the animal arrived to the shelter
- animal's conditions