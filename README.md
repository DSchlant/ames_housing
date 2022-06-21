## Housing Price Regression Modeling

### Background
I assumed the role of data scientist located in beautiful Ames, Iowa who is interested in providing staff of a local academic institution, Iowa State University, with data-driven advice on how best to improve home values prior to sale. The prescribed changes are intended to be able to be done quickly (before the start of next term) and somewhat painlessly - taking large projects off the table.

### Data Problem
Using residential real estate transactions in Ames from 2006-2010 (the famed Ames, Iowa housing dataset), I performed regression analyses in order to develop the home (value) improvement recommendations. There are 79 house characteristics available to analyze on close to 3,000 transactions.

I intended to create a linear regression model that incorporates:

* features of a home that cannot be changed, such as neighborhood, lot size and age such that home prices can be predicted accurately
* features that can be relatively easily changed in the few short months that employees have before they must sell property

Combining these elements would create a strong model that can provide clear recommendations to clients. The strength of a model will be assessed via a model's validation R-squared and mean squared error.

### Data Cleaning
To arrive at a clean dataset, the Data Cleaning notebook contains the process of dropping extraneous columns, consolidating columns, and imputing missing data. Numeric values for ordinal features added as well, incorporating the ranking systems provided in the data dictionary. Several outliers in training set are removed.

### EDA
I studied the correlation between sale price and the numeric features available in order to get a sense for the relationship between these features and price, with an eye for what to include in the final regression analysis. I also perform additional analysis on categorical variables to provide further insights.

### Preprocessing and Modeling
Using feature reduction processes, 27 features were selected for inclusion in regression models that produced low error and served to contribute to recommendations that can be offered to the college staff. Utilizing pipeline transformations, the selected data was scaled and one-hot-encoded. The target data was also log transformed, which produced better fitting models.

I proceeded to run a series of permutations of regression analyses in order to find the regression model that best limits the mean squared error. The model that ultimately was selected was **Ridge regression using an alpha of 0.5** (level of regularization).

The model produced R-squared values of .9334 on the training data, **.9147 on the validation set** and **.9185 in K-Folds cross validation (using 5 folds)**. The mean squared error for this regression was 376,760,643. This is much better than the mean-squared-error of 4,417,414,053 produced by the baseline model (using the mean price of the validation set), and better than the Linear and Lasso Regression models that we calculated.


### Recommendations for Homeowners:
Using this regression analysis, the below advisements can be made to homeowners who consult with us (keeping in mind that these values are to be interpreted as the change in home value if all other variables were held equal).

* Installing central air can add ~6% to home price.
* Paving driveway can add ~5.5% to home price.
* Fences (of any kind) slightly hurt value of home.
* Having a garage that is in poor quality can decrease a home price by 18% versus not having a garage. 
* Conversely, a garage of good quality can add ~8% to a home value.
* Improving kitchen quality (surfaces, appliances) from poor to good can increase house price by 6%, from poor to excellent can improve a house price by 12%.
* Improving heating quality from poor to fair can increase home price 44%.
* Improving overall condition of house from poor to average can increase your house price by ~20%.
* If 1 bathroom in above ground living area, adding a second full bathroom only increase house price by ~5%, may not be worth cost and hassle.
* The exterior of the house is very important. If your house has asbestos shingles or common brick as one of its primary exterior materials, considering replacing it. Asphalt shingles, brickface, stucco, and cinderblock is best.

### For Further Research 
* Improve and Refine Code
* Add additional regressor models to study to try to improve performance