![Map with Price Data Header](https://github.com/thegrandblooms/dsc-phase-2-project-v2-3/blob/68f06f1770bb0b4f79a4c7864f9349ed9b9a39a2/Graphics/price_map_header.jpg)
### Seattle Real-Estate Analysis

Author: Blake McMeekin

## Overview

The main focus of this project was to use multi-linear regression in a professional level analysis and presentation. The goal was to create a predictive model for real-estate valuation which could be used to help make purchasing decisions. If the predictive model imagines that a house should cost $500,000 and instead the list is $300,000, this could be forwarded to decisionmakers for further analysis because there's the potential to profit $200,000 (+- the accuracy of the model). There are some obvious dangers to this kind of decisionmaking if it were automated, but the goal here is merely to filter down the number of choices to allow humans to vet the remaining options.

The pipeline is to filter, clean, and process data using Python, transform numeric data to log numeric, and transform categoric information into dummy columns - then this prepared data was fed into a multiple-linear regression model and a few iterations were done to optimize the results. A couple findings were the importance of location, home size, and home quality in price.

## Business Problem

The problem here is, how do you decide which homes to buy/invest in? There is lots of opportunity in real-estate, but making decisions with an abundance of choice and information can be overwhelming. We can't entirely automate the process, but we might be able to make tools and find predictors that make the decisionmaking easier for humans.

## Data

The data in this project is real-estate information from King County with over 20000 rows and 21 columns. The data was transformed and cleaned in a number of ways, such as splitting the data into numeric, categoric, and location data, transforming the numeric data to log numeric, splitting the categories to dummy columns, and dropping columns that seem like bad predictors in a linear regression (like latitude and longitude).

## Methods

To build our predictive model, we perform a 75-25 split into train and test sets and run a multiple linear regression using ordinary-least squares to estimate prices. When we run this model on all of our data, it becomes clear that some of the p-values (which measure confidence) and correlation coefficients (impact) of some columns are less useful, so a few iterations are made to clean up these inputs.

## Validation

We want to make sure the model is accurate before we use it for anything. This can be measured by R-squared and mean-squared error. The final predictive power here had an R-squared of 0.85 and a mean-squared error of 0.04 on unseen log data. We also want to make sure that the big assumptions for linear regression are not ignored, such as linearity, normality, and heteroscedasticity. Linearity and heteroscedasticity are specific to every feature, but a sense of the normality can be seen in the QQ plot.

![QQ Plot](https://github.com/thegrandblooms/dsc-phase-2-project-v2-3/blob/68f06f1770bb0b4f79a4c7864f9349ed9b9a39a2/Graphics/QQ_plot.png)

## Findings

In building our model, a few predictors stood out as much more important than others. Location data like certain Zip Codes predicted the most about a property’s price, for example having a house in in Medina correlated with more than a doubling in price.

Waterfront properties correlated with an almost 50% increase in price, while homes categorized as having excellent views were predicted to be about 35% more valuable.

Square Footage of living space was perhaps the most consistent numeric predictor, with a doubling of square footage representing a 68% increase in predicted property value. Bedrooms, bathrooms, and floors were surprisingly negligible in predicting price, most were later removed from the model to reduce redundant information (or multicollinearity).

Homes described as “Excellent” (+30%), “Luxury” (+43%), or “Mansion” (+70%) naturally correlated with price increases, while poor home condition was reflected by a 36% decrease in home value. Positive descriptions of home condition were not as impacting as negative ones.

To make it easier to act on these findings, we can compare estimated prices with actual list prices to show homes which seem like good deals. The 500 estimated “best deals” were colored by this value and displayed on an interactive map which could be shared or built into applications:

![Interesting Real Estate Map](https://github.com/thegrandblooms/dsc-phase-2-project-v2-3/blob/69ce930c1a72a00b77b9be88a732131b8b09b117/Graphics/Interesting_properties.png)

## Conclusions

The biggest business recommendations from this exercise were:
- More validation should be done to see to what degree this sort of prediction can realistically steer investments
- More feedback should be collected from those within the industry on how they currently make decisions
- Giving Tools such as the map to existing developers, home-buyers, and real-estate offices

## Next Steps

- More geographic data (schools, hospitals, parks, etc) could improve the model accuracy
- Data across time is particularly interesting
- More tools could be built and integrated into the workflow of existing decision-makers

## For more information

See the full analysis in the Jupyter Notebook or review the presentation in the pdf.

For additional information, contact Blake McMeekin at blakemcme@gmail.com

## Repository Structure

```
├── data
│   └── kc_house_data.csv
├── Graphics
├── Flatiron Files
├── Presentation.pdf
├── README.md
└── Student.ipynb
```
