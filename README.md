# Churn Prediction for a ride share company

Summary: A ride-sharing company (Company X information witheld for privacy issues) was interested in predicting rider retention.
To help explore this question, I have been given sample dataset of a cohort of users who signed up for an account in January 2014. 

# Key Findings

1) I noticed that high-income users are less likely to churn: feature variables such as iphone, living in "King's Landing" (and "Winterfell" though to a lesser extent (codenames of actual cities)), and riding luxury cars are negatively associated with the churn probability.

2) Users who ride on both weekdays and weekend days are less likely to churn, as compared to users who ride only during weekdays or only during the weekend.

3) Users who experiement low shares of rides with surge are less likely to churn. However, this trend is more evident in which suggests that surge seems to have a short-term effect on user's behavior. Ratings and average distance of rides do not seem to be associated with churn.


# Suggestions
The best strategy to be adopted will depend on the stage and priorities of the company.

1) If the churn definition is aggressive (i.e. a user is considered to have churned if he/she has not used the service in 30 days), the company can make a profit of up to $8 per user by sending out $20 per year in promotions to users predicted to churn.

2) If the churn definition is standard (i.e. 90 days), the company can make a profit of up to $4 per user by sending out $20 per year in promotions to users predicted to churn.

# Data 

city: city this user signed up in phone: primary device for this user signup_date: date of account registration, in the form YYYYMMDD
last_trip_date: the last time this user completed a trip, in the form YYYYMMDD
avg_dist: the average distance (in miles) per trip taken in the first 30 days after signup
avg_rating_by_driver: the rider’s average rating over all of their trips
avg_rating_of_driver: the rider’s average rating of their drivers over all of their trips
surge_pct: the percent of trips taken with surge multiplier > 1
avg_surge: The average surge multiplier over all of this user’s trips
trips_in_first_30_days: the number of trips this user took in the first 30 days after signing up
luxury_car_user: TRUE if the user took a luxury car in their first 30 days; FALSE otherwise
weekday_pct: the percent of the user’s trips occurring during a weekday

# Methodology

Feature engineering

Churn: The models try two definitions for churn:
   Standard: A user is considered to have churned if he/she has not taken a ride in the last 90 days. This definition is broadly in line with the industry standard.

Aggressive: A user is considered to have churned if he/she has not taken a ride in the last 30 days. This definition is suitable for a company in an expansive stage, when it is willing to pay a relatively high retention cost to keep a user.

Exogenous features

Categorical features with missing values were filled in with the mode for their specific group (by city and luxury_car_user). Missing value sin continuous features were filled in with the median value for such groups.
Categorical features, such as city, phone, and luxury_car_user were converted to dummy variables.
Continuous features that exhibited a log-normal distribution were logarized.
user_lifespan and user_rated_driver were created.
