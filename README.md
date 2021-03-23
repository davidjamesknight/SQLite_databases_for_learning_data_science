# SQLite Databases for Learning Data Science

The Iris, Titanic, and other [seaborn example datasets](https://github.com/mwaskom/seaborn-data) in `.db` format for practicing SQL queries, exploratory analysis, machine learning, etc. 

Each database starts with an `Observation` table, which contains only boolean and numeric types. Text data are split off into related tables.

## Contents
- [Example: Querying the Iris dataset with Python](#example)
- [Schemata](#schemata)
    - [x] [`anscombe.db`](#anscombe.db)
    - [x] [`attention.db`](#attention.db)
    - [ ] `brain_networks.db`
    - [x] [`car_crashes.db`](#car_crashes.db)
    - [x] [`diamonds.db`](#diamonds.db)
    - [x] [`dots.db`](#dots.db)
    - [x] [`exercise.db`](#exercise.db)
    - [x] [`flights.db`](#flights.db)
    - [x] [`fmri.db`](#fmri.db)
    - [x] [`gammas.db`](#gammas.db)
    - [x] [`iris.db`](#iris.db)
    - [x] [`mpg.db`](#mpg.db)
    - [x] [`planets.db`](#planets.db)
    - [x] [`tips.db`](#tips.db)
    - [x] [`titanic.db`](#titanic.db)
- [Credits](#credits)

## Example

```python
# Querying the Iris dataset with Python

import sqlite3
import pandas as pd

db = sqlite3.connect('iris.db')
sql = """
    SELECT 
        O.petal_length, 
        O.petal_width, 
        O.sepal_length, 
        O.sepal_width, 
        S.species
    FROM Observation AS O
    JOIN Species AS S ON S.species_id = O.species_id
"""
df = pd.read_sql_query(sql, db)
df.head()
```

| | petal_length | petal_width | sepal_length | sepal_width | species |
| :-- | :-- | :-- | :-- | :-- | :-- |
| **0** | 1.4 | 0.2 | 5.1 | 3.5 | setosa |
| **1** | 1.4 | 0.2 | 4.9 | 3.0 | setosa |
| **2** | 1.3 | 0.2 | 4.7 | 3.2 | setosa |
| **3** | 1.5 | 0.2 | 4.6 | 3.1 | setosa |
| **4** | 1.4 | 0.2 | 5.0 | 3.6 | setosa |


## Schemata
### anscombe.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Dataset | dataset_id | BIGINT |
| Dataset | dataset | TEXT |
| Observation | x | FLOAT |
| Observation | y | FLOAT |
| Observation | dataset_id | BIGINT |


### attention.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Attention | attention_id | BIGINT |
| Attention | attention | TEXT |
| Observation | "Unnamed: 0" | BIGINT |
| Observation | subject | BIGINT |
| Observation | solutions | BIGINT |
| Observation | score | FLOAT |
| Observation | attention_id | BIGINT |


### car_crashes.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Abbrev | abbrev_id | BIGINT |
| Abbrev | abbrev | TEXT |
| Observation | total | FLOAT |
| Observation | speeding | FLOAT |
| Observation | alcohol | FLOAT |
| Observation | not_distracted | FLOAT |
| Observation | no_previous | FLOAT |
| Observation | ins_premium | FLOAT |
| Observation | ins_losses | FLOAT |
| Observation | abbrev_id | BIGINT |


### diamonds.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Clarity | clarity_id | BIGINT |
| Clarity | clarity | TEXT |
| Color | color_id | BIGINT |
| Color | color | TEXT |
| Cut | cut_id | BIGINT |
| Cut | cut | TEXT |
| Observation | carat | FLOAT |
| Observation | depth | FLOAT |
| Observation | "table" | FLOAT |
| Observation | price | BIGINT |
| Observation | x | FLOAT |
| Observation | y | FLOAT |
| Observation | z | FLOAT |
| Observation | cut_id | BIGINT |
| Observation | color_id | BIGINT |
| Observation | clarity_id | BIGINT |


### dots.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Align | align_id | BIGINT |
| Align | align | TEXT |
| Choice | choice_id | BIGINT |
| Choice | choice | TEXT |
| Observation | time | BIGINT |
| Observation | coherence | FLOAT |
| Observation | firing_rate | FLOAT |
| Observation | align_id | BIGINT |
| Observation | choice_id | BIGINT |


### exercise.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Diet | diet_id | BIGINT |
| Diet | diet | TEXT |
| Kind | kind_id | BIGINT |
| Kind | kind | TEXT |
| Observation | "Unnamed: 0" | BIGINT |
| Observation | id | BIGINT |
| Observation | pulse | BIGINT |
| Observation | diet_id | BIGINT |
| Observation | time_id | BIGINT |
| Observation | kind_id | BIGINT |
| Time | time_id | BIGINT |
| Time | time | TEXT |


### flights.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Month | month_id | BIGINT |
| Month | month | TEXT |
| Observation | year | BIGINT |
| Observation | passengers | BIGINT |
| Observation | month_id | BIGINT |


### fmri.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Event | event_id | BIGINT |
| Event | event | TEXT |
| Observation | timepoint | BIGINT |
| Observation | signal | FLOAT |
| Observation | subject_id | BIGINT |
| Observation | event_id | BIGINT |
| Observation | region_id | BIGINT |
| Region | region_id | BIGINT |
| Region | region | TEXT |
| Subject | subject_id | BIGINT |
| Subject | subject | TEXT |


### gammas.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Observation | timepoint | FLOAT |
| Observation | subject | BIGINT |
| Observation | "BOLD signal" | FLOAT |
| Observation | "ROI_id" | BIGINT |
| Roi | "ROI_id" | BIGINT |
| Roi | "ROI" | TEXT |


### iris.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Observation | sepal_length | FLOAT |
| Observation | sepal_width | FLOAT |
| Observation | petal_length | FLOAT |
| Observation | petal_width | FLOAT |
| Observation | species_id | BIGINT |
| Species | species_id | BIGINT |
| Species | species | TEXT |


### mpg.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Name | name_id | BIGINT |
| Name | name | TEXT |
| Observation | mpg | FLOAT |
| Observation | cylinders | BIGINT |
| Observation | displacement | FLOAT |
| Observation | horsepower | FLOAT |
| Observation | weight | BIGINT |
| Observation | acceleration | FLOAT |
| Observation | model_year | BIGINT |
| Observation | origin_id | BIGINT |
| Observation | name_id | BIGINT |
| Origin | origin_id | BIGINT |
| Origin | origin | TEXT |


### planets.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Method | method_id | BIGINT |
| Method | method | TEXT |
| Observation | number | BIGINT |
| Observation | orbital_period | FLOAT |
| Observation | mass | FLOAT |
| Observation | distance | FLOAT |
| Observation | year | BIGINT |
| Observation | method_id | BIGINT |


### tips.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Day | day_id | BIGINT |
| Day | day | TEXT |
| Observation | total_bill | FLOAT |
| Observation | tip | FLOAT |
| Observation | size | BIGINT |
| Observation | sex_id | BIGINT |
| Observation | smoker_id | BIGINT |
| Observation | day_id | BIGINT |
| Observation | time_id | BIGINT |
| Sex | sex_id | BIGINT |
| Sex | sex | TEXT |
| Smoker | smoker_id | BIGINT |
| Smoker | smoker | TEXT |
| Time | time_id | BIGINT |
| Time | time | TEXT |


### titanic.db

| Table | Column | Type |
| :-- | :-- | :-- |
| Alive | alive_id | BIGINT |
| Alive | alive | TEXT |
| Class | class_id | BIGINT |
| Class | class | TEXT |
| Deck | deck_id | BIGINT |
| Deck | deck | TEXT |
| EmbarkTown | embark_town_id | BIGINT |
| EmbarkTown | embark_town | TEXT |
| Embarked | embarked_id | BIGINT |
| Embarked | embarked | TEXT |
| Observation | survived | BIGINT |
| Observation | pclass | BIGINT |
| Observation | age | FLOAT |
| Observation | sibsp | BIGINT |
| Observation | parch | BIGINT |
| Observation | fare | FLOAT |
| Observation | adult_male | BOOLEAN |
| Observation | alone | BOOLEAN |
| Observation | sex_id | BIGINT |
| Observation | embarked_id | BIGINT |
| Observation | class_id | BIGINT |
| Observation | who_id | BIGINT |
| Observation | deck_id | BIGINT |
| Observation | embark_town_id | BIGINT |
| Observation | alive_id | BIGINT |
| Sex | sex_id | BIGINT |
| Sex | sex | TEXT |
| Who | who_id | BIGINT |
| Who | who | TEXT |

## Credits

These databases are based on the .csv files in the [data repository](https://github.com/mwaskom/seaborn-data) for `seaborn.load_dataset`. They were converted to SQLite using Pandas and SQLAlchemy. The datasets themselves are all either open source or in the public domain.
