# Taxi_Fare_Prediction
This is a challenge to predict the fare amount of a taxi ride in New York city, given the pickup and drop off locations. 

While you can get a basic estimate based on just the distance between the two
points, this will result in an RMSE (Root Mean Square Error) of $5-$8, depending on the model used. 

# The Data

File descriptions
-  [train.csv](https://www.dropbox.com/s/mnty1y72gweqjj1/train.csv?dl=0) - Input features and target fare_amount values for the training set (about 55M rows).
- [test.csv](https://www.dropbox.com/s/7cvc0s50u9350lo/test.csv?dl=0) - Input features for the test set (about 10K rows). Your goal is to predict fare_amount
for each row.
- [sample_submission.csv](https://www.dropbox.com/s/euh08kcj7khs89b/sample_submission.csv?dl=0) - a sample submission file in the correct format (columns key and fare_amount). This file 'predicts' fare_amount to be $11.35 for all rows, which is the mean fare_amount from the training set.

# Data fields

### ID

- key - Unique string identifying each row in both the training and test sets. Comprised of pickup_datetime plus a unique integer, but this doesn't matter, it should just be used as a unique ID field. Required in your submission CSV. Not necessarily needed in the training set, but could be useful to simulate a 'submission file' while doing cross-validation within the training set.


### Features

- pickup_datetime - timestamp value indicating when the taxi ride started.
- pickup_longitude - float for longitude coordinate of where the taxi ride started.
- pickup_latitude - float for latitude coordinate of where the taxi ride started.
- dropoff_longitude - float for longitude coordinate of where the taxi ride ended.
- dropoff_latitude - float for latitude coordinate of where the taxi ride ended.
- passenger_count - integer indicating the number of passengers in the taxi ride.

### Target

- fare_amount - float dollar amount of the cost of the taxi ride. This value is only in the training set; this is what you are predicting in the test set and it is required in your submission CSV.

## Additional Info

There are additional regulations for Taxis in NYC:

- Initial charge for most rides (excluding from JFK and other airports) is $2.50 upon entry. After that there $0.5 every unit where the unit is defined as 1/5th of a mile or when the Taxicab is traveling 12 Miles an hour or more.
- $0.5 of additional surcharge between 8PM - 6AM.
- Peak hour weekday surcharge of $1 Monday-Friday between 4PM-8PM.
- There is a $0.5 MTA State Surcharge for all trips that end in New York City or Nassau, Suffolk, Westchester, Rockland, Dutchess, Orange or Putnam Counties.
- There is a $0.3 Improvement surcharge

There are various other rules. You may find them all by following this link [NYC Taxi Fare](https://www1.nyc.gov/site/tlc/passengers/taxi-fare.page).

Thus, the based on the location, time of day and day of week we will need to deduct these fixed charges (i.e. Initial charge of $2.5 and other surcharges) from the fare amount and use that to model the relations.
