# Outcomes for Animals in Shelter

This project aims to predict the outcome of each pet that gets into the animal shelter. 
The possible outcomes are: return to owner, adoption, transfer, euthanasia or death.

## Case Problem & Solution
This case offers shelter employees two valuable opportunities:

**1. Suport for animals with low adoption likelihood**  
When an animal is predicted to have a low likelihood of adoption, it provides an opportunity for shelter employees to extend additional support in the effort to find them a new home. This approach ensures that animals with lower adoption probabilities receive extra attention and care.  

**2. Resource optimization based on adoption likelihood**  
The predictive model enables shelter employees to optimize their human, financial, and time resources based on the likelihood of adoption. For instance, if the model indicates a low adoption likelihood for particular animals, the shelter can allocate more efforts and resources to increase the chances of successful adoptions.

## Data
The data is from an [animal shelter](https://www.austintexas.gov/austin-animal-center) in Austin, US and it includes information on animals ending up in the shelter: breed, color, sex, age, etc.
The original data can be found on [Kaggle](https://www.kaggle.com/competitions/shelter-animal-outcomes).

## Limitations
* No intake timestamps - it's known when the animal is adopted or returned to owner, but not when they enter the animal shelter.
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
When it comes to outcomes, there are still outcomes when animals transfers and returns to owners are mistaken as adoption and vice versa.
Additionally, predicting rare cases like deaths proves to be impractical.
![](plots/confusion_matrix_outcome_type)

I suspect what shelter employees want to find out is whether animals will stay in shelter or will leave.
Therefore, as an extra step, I decided to group the outcomes into groups, to account for the similiarities between adoption and return to owner and the rare case of deaths.
The 3 groups are:
1) Owner Found - returns to owners, adoptions
2) Owner in Search - transfer
3) Owner not Found - euthanasia and death

While this grouping might simplify the classification for resource management, it aligns well with the objective of identifying cases where owners are less likely to be found.
![](plots/confusion_matrix_outcome)


## Conclusions
As mentioned, additional data points would help in making better decisions:
- intake timestamps - could allow adjust the model and predict how much time the pet is to stay in the shelter. This could be used by shelter employees to plan their resources. 
- animal's conditions - an animals who was lost by the owner could be in a totally different conditions from an animal that was found on the street.

Note: there are still quite some False Positives, predicting more animals being returned and adopted. The model could be refined to increase the level of False Negatives, as a shelter employee would be better off not being overly optimistic. 