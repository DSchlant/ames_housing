### Data Science Problem:

I am affiliated with the Home Valuation Consultative Services, Office for Faculty and Staff Housing Support at Iowa State University. 

It is a small data consultancy housed within the Iowa State University Office of the Provost, which provides free consulatative services to ISU employees. 

Faculty come here thinking they will stay in beautiful Ames Iowa forever after landing their dream job at ISU. They buy a home and settle in. They may start making renovations to their house, after all, this is where they will be hosting their retirement party! 

However, a few years down the line, they get a call from The University of Nebraska, Minnesota, or God forbid, Iowa. They are made an offer they cannot refuse, and one thing leads to another, and they are headed to greener pastures come next fall. This leaves them with less than a year to get their house in condition to be sold, be it to the new crop of ISU professors looking for the house they will retire in, a family interested in moving out of the hustle and bustle of Des Moines, or otherwise.

Part of what our team does is consult with professors who are interested to learn what they can do in order to try to maximize the price they can ask for their home. We do this free of charge, as part of what we offer faculty to entice them to join Iowa State in the first place.

Our team utilizes past transactions in Ames, from 2006-2010, in order to run regression analyses to develop the recommendations that we pass on to the individuals who utilize our services. There are 79 house characteristics available to analyze.

The process that our team endeavors to take on is to create a model that incorporates features of a home that cannot be changed, such as neighborhood, lot size, age so that we can accurately predict home prices, and also include features that can be relatively easily changed in the few short months that employees have before they must sell the house. This allows us to build a strong model that can provide clear recommendations to our clients.


### Data Cleaning and EDA

To arrive at a clean dataset, you will find in the Data Cleaning notebook our process of dropping extraneous columns, consolidating some columns, and imputing missing data. We add the numberic values for our ordinal feautures as well, incorporating the ranking systems provided in the data dictionary. Several outliers in our training set are removed.

We split our training dataset into training and validation sets, and proceed to analyze our training set further.

We studied the correaltion between salesprice and the numeric features available in order to get a sense for the relationship between these features and price, with an eye for what to include in the final regression analysis that we perform.

We also perform edsome additional analyses on categorical variables to provide further clarity.


### Preprocessing and Modeling

Using a bit of a trial and error process, with an eye for our overall data science problem, we selected 27 features to analyze in our regression models that produced low error and served to contribute to recommendations that we can offer to the college staff. Utilizing pipeline transformations, the selected data was scaled and one-hot-encoded. The target data was also log transformed so it could be normalized, which produced better fitting models.

We proceeded to run a series of permutations of regression analyses in order to find the regression model that best limits the mean squared error. 

The model that ultimately was selected was the Ridge CV regression usin:
* the 27 selected features
* log transformation of target
* an alpha of 0.2

This model produced the below R-Square Values:

* Train: 0.9334
* Validation: 0.9147
* K-Folds (5 Folds): 0.9187

The Mean Sqaured Error for this regression was 376,816,821. This is much better than the mean-squared-error of 4,417,414,053 produced by our Baseline Model, and better than the Linear and Lasso Regression models that we calcualted.


### Recommendations for Homeowners:

We can make the below advisements to homeowners who consult with us (keeping in mind that these values re to be interpreted as the change if all other variables were held equal).

* Installing Central Air can add ~6% to home price.
* Pavig driveway can add ~5.5% to home price.
* Fences (of any kind) slghtly hurt value of home.
* Having a garage that is in poor quality can decrease a home price by 18% versus not having a garage. Conversely, a garage of good quality can add ~8% to a home value.
* Improving kitchen quality (surfaces, appliances) from poor to good can increase house price by 6%, from poor to excellent can improve a house price by 12%.
* Improving heating quality from poor to fair can increase home price 44%.
* Improving overall condition of house from poor to average can increase your house price by ~20%.
* If 1 bathroom in above ground living area, adding a second full bathroom only increase house price by ~5%, may not be worth cost and hassle.
* The exterior of the house is very important. If your house has asbestos shingles or comon brick as one of its primary exterior materials, considering replacing it. Asphalt shingles, brickface, stucco, and cinderblock is best.


