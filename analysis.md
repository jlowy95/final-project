# Methods and Analysis

## Abstract

The correct valuation of a home or residence can be critical to the finances of any family or business. However, this problem is much more complicated than counting beds and baths. The use of machine learning enables us to model intricate relationship problems such as home valuation with relative ease. By using detailed home listing data, we have trained a model specific to the Sacramento area to predict home price or rental price based on an assortment of property features. Property price estimation is a much greater problem than what our model and selection of features can grasp, but we aim to use this model as a starting point and reference for future assessment.

## Materials

Data from this project was originally sourced from Trulia (Trulia.com). Rental listing price and property purchase listing prices were acquisitioned along with all provided listing details. Approximately 4600 records total were used, all specific to the Sacramento region.

## Methods

**Preprocessing and Cleanup**

All cleanup and preprocessing operations were performed in Python Jupyter notebooks with the use of the Pandas library. Listings were denoted 'BUY' or 'RENT' based on their original distinction. The 'details' information was then grouped and analyzed to establish the most common and consistent property features across both buy and rent listings. With these lists of features, the 'details' were parsed, and all inconsistencies were removed or corrected. The clean data was then encoded using Pandas get_dummies one-hot-encoding feature. For numeric features (i.e. number of bedrooms, square footage, year built) the median value was imputed over null records. The median was chosen due to the presence of outliers in the data and the small amount of records available.

**Modeling**

Linear regression was the problem model we chose to use as listing price was our single desired output. Basic sklearn linear regression performed with less than desired results (R^2 = 0.74) so we opted to explore other modeling libraries. Tensorflow has options for deep linear regression through their Keras API which gave us more utility to adjust and tinker with our model. Primarily using brute-force tactics we remained relatively unsatified with the results of our models. Rental listings in the Sacramento region float between $300 to $3000 (2 standard deviations from the mean($1735)) and we were aiming for mean average errors at or below $150. None of our models were producing MAE values better than $380, so again we attempted to explore models. After unsuccessfully training accurate models using gradient boosting techniques and XGBoost, we felt convinced the problem lied more with data than with our modeling techniques. For this reason we chose to only focus on modeling rent listing prices for the remainder of our time. Our currently implemented model was built using Tensorflow libraries.

## Analysis

**Models**

We attribute the undesireable performance of our models to the size of our dataset. Our rent listing data consisted of only just over 1,000 records. We were attempting to model price based on approximately ~30 different features of a property, which felt approachable. However, those 30-some features consisted of over 220 unique identifiers which added significant complexity to our problem. With a much larger dataset, we think any of our models could have attained more desireable accuracy. More data was not acquisitioned due to our deadline. Other data sources were also explored, however, again for time related reasons for cleanup/preprocessing these were abandoned.

**Data**

The data we sourced was accumulated by Trulia from its proprietary sources. We cannot speak to its accuracy in any respect whether that be the price or the presence of a feature. We therefore assumed we had true positives, but not necessarily true negatives. This adds great ambiguity to our modeling problem. We also understand the assumed value a specific feature adds to a listing price is highly variable. A pool on one property may differ greatly from a pool on another. Grouping/specificity of location features is also unknown from our data. Trulia does not outline neighborhood or zipcode boundaries, so these features which we felt were important to include in our modeling include some ambiguity and possibly redundancy we could not account for.

## Conclusion

Our currently implemented model still accepts 32 different feature inputs with over 200 identifiers. It's performance is lackluster, but still consistently operates with an MAE of ~$400. With more data to train with, we have confidence this value could be brought below $200 or less.
