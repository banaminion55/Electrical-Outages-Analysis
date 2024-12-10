# Power Outages Analysis and Modeling

## Step 1: Introduction and Question Identification

The power outages dataset contains data from the major outages in the United States, including features such as weather information and characteristics about the states and people affected by the outages.

#### Central Question:

What risk factors may an energy company want to look into when predicting the severity of its next major power outage?

This dataset and question are important because when an outage occurs, it is important to understand the extent of the outage, whether in terms of customers affected or total power loss.

#### Number of Rows:
1534

#### Relevant Columns:

YEAR: Year outage occurred

MONTH: Month outage occurred

U.S._STATE: State where outage occurred

CLIMATE.REGION: U.S. Climate region determined by National Centers for Environmental Information, with 9 total regions

CLIMATE.CATEGORY: Cold, warm, or normal climate

OUTAGE.START.DATE: Start date of outage

OUTAGE.START.TIME: Time of day of outage start

OUTAGE.RESTORATION.DATE: End date of outage

OUTAGE.RESTORATION.TIME: Time of day of outage end

CAUSE.CATEGORY: Cause of outage as identified by authorities

OUTAGE.DURATION: Total time duration of outage

DEMAND.LOSS.MW: Estimated total electrical power demand lost during the outage

CUSTOMERS.AFFECTED: Total customers affected by outage

## Step 2: Data Cleaning and Exploratory Data Analysis

#### Data Cleaning:

1. First, I removed initial rows in the dataset that were just descriptions of the dataset. I then used the 'variables' row as the columns for the dataset. I also dropped the unnecessary 'OBS' column.

2. I kept only the necessary columns, as specified in Step 1.

3. I combined OUTAGE.START.TIME with OUTAGE.START.DATE to create a new column called OUTAGE.START, which I converted to pd.Timestamp. I als combined OUTAGE.RESTORATION.TIME with OUTAGE.RESTORATION.DATE to create a new column called OUTAGE.RESTORATION, which I converted to pd.Timestamp.

4. I replaced the year and month columns with the respective year and month attributes from OUTAGE.START.DATE to ensure data consistency. I also added a 'DAY' column that contains the day of the week of the outage.

5. I converted all numerical values to floats.

6. Lastly, I replaced all 0 values with np.nan because 0 data, in this case, represents values with no information.

Here is a sample of the cleaned dataframe, with selected columns.

| U.S._STATE   | CAUSE.CATEGORY     | CLIMATE.REGION     |   CUSTOMERS.AFFECTED |   OUTAGE.DURATION |
|:-------------|:-------------------|:-------------------|---------------------:|------------------:|
| Minnesota    | severe weather     | East North Central |                70000 |              3060 |
| Minnesota    | intentional attack | East North Central |                  nan |                 1 |
| Minnesota    | severe weather     | East North Central |                70000 |              3000 |
| Minnesota    | severe weather     | East North Central |                68200 |              2550 |
| Minnesota    | severe weather     | East North Central |               250000 |              1740 |

#### Univariate Analysis:

<iframe
  src="assets/Hist_Customers_Affected.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Pictured above is a histogram of the number of customers affected by each outage. The data appears slightly right-skewed, with most of the data concentrated below about 200,000 people per outage. On the right side of the distribution, there are several extreme outages where millions of customers were affected.

#### Bivariate Analysis:

<iframe
  src="assets/Box_Plot.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Pictured above is a box plot of the number of customers affected by the outage based on the cause category of the outage. For severe weather, system operability disruption, and equipment failure, there seem to be larger values for the number of customers affected overall. 

#### Interesting Aggregates:

|     CLIMATE.CATEGORY          |     cold |   normal |     warm |
|:------------------------------|---------:|---------:|---------:|
| equipment failure             |   327.5  |  3201.43 |   505    |
| fuel supply emergency         | 17433    |  7658.82 | 22799.7  |
| intentional attack            |   709.54 |   505.44 |   317.77 |
| islanding                     |   259.27 |   142.18 |   209.83 |
| public appeal                 |  2125.91 |  1376.53 |   596.23 |
| severe weather                |  3293.79 |  4082.53 |  4416.69 |
| system operability disruption |   637.26 |   941.02 |   494.69 |
| Total Average                 |  2901.35 |  2666.11 |  2837.37 |


Pictured above is a table showing the average outage duration based on climate category (columns of the table) and cause category (rows). Overall, it appears that fuel supply emergencies, public appeals, and severe weather outages have a greater average duration. It also appears that average outage durations are fairly evenly distributed among cold, normal, and warm climates based on the 'Total Average' row.


## Step 3: Assessment of Missingness

#### NMAR Analysis:

#### Missingness Dependency:


## Step 4: Hypothesis Testing:


## Step 5: Framing a Prediction Problem


## Step 6: Baseline Model


## Step 7: Final Model


## Step 8: Fairness Analysis
