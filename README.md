# Spaceship Titanic

A machine learning project for the [Kaggle Spaceship Titanic competition](https://www.kaggle.com/competitions/spaceship-titanic/overview).

## Project Overview

This project predicts whether passengers were transported to an alternate dimension during the Spaceship Titanic's collision with a spacetime anomaly. Using passenger records and luxury amenity spending data, an XGBoost classifier achieves competitive accuracy through careful feature engineering and hyperparameter optimization.

## Data Description

### Dataset Files

- **train.csv**: Personal records for ~8,700 passengers (two-thirds of total) used for model training
- **test.csv**: Personal records for ~4,300 passengers (one-third of total) used for predictions
- **sample_submission.csv**: Template file in the correct submission format

### Feature Descriptions

#### Passenger Information
- **PassengerId**: Unique identifier in format `gggg_pp` where `gggg` is the group number and `pp` is the passenger number within that group. Group members are often (but not always) family members traveling together.
- **Name**: First and last name of the passenger
- **Age**: Age of the passenger in years
- **HomePlanet**: Planet of departure, typically the passenger's permanent residence (Earth, Europa, Mars)
- **Destination**: Destination planet where the passenger will disembark (TRAPPIST-1e, PSO J318.5-22, 55 Cancri e)

#### Journey Details
- **CryoSleep**: Boolean indicating if the passenger was in suspended animation for the voyage. Passengers in cryosleep are confined to their cabins and cannot use amenities.
- **Cabin**: Cabin assignment in format `deck/num/side` where:
  - `deck`: Cabin deck (A-G, T)
  - `num`: Cabin number
  - `side`: Port (P) or Starboard (S)
- **VIP**: Boolean indicating if the passenger paid for special VIP service

#### Luxury Amenity Spending
Amount billed at various Spaceship Titanic luxury amenities (all numerical):
- **RoomService**: Room service charges
- **FoodCourt**: Food court purchases
- **ShoppingMall**: Shopping mall expenses
- **Spa**: Spa and wellness services
- **VRDeck**: Virtual reality deck entertainment charges

#### Target Variable
- **Transported**: Boolean indicating whether the passenger was transported to an alternate dimension during the spacetime anomaly. **This is the prediction target.**

## Key Findings

- **CryoSleep** is highly correlated with being transported
- **Deck** and **Side** of cabin show significant patterns
- Children (age ≤ 10) have different transportation distributions
- Passengers with zero spending show distinct behavior
- Group size influences transportation probability

## Model Performance

- Cross-validation accuracy: Reported in notebook
- Hyperparameter optimization: 25 trials using Optuna
- Feature importance analysis using Mutual Information scores
