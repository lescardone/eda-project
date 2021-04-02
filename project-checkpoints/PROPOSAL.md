# Eda Project: MTA DATA

## Question/need:
*What is the framing question of your analysis, or the purpose of the model/system you plan to build?*
- Per station, which days of the month and time of the day has the least amount of traffic?
- Are there any trends in low traffic patterns?
- Which stations experience the most amount of traffic each month?

*Who benefits from exploring this question or building this model/system?*
- MTA: scheduling maintenance/upkeep
- MTA: keeping train schedules efficient
- SEE [MTA Subway Operating Cost](https://ny.curbed.com/2017/10/13/16455880/new-york-city-subway-mta-operating-cost-analysis)


## Data Description:
*What dataset(s) do you plan to use, and how will you obtain the data?*
- [MTA Turnstile DATA](http://web.mta.info/developers/turnstile.html) from the year 2019 (pre-Covid)

*What is an individual sample/unit of analysis in this project? What characteristics/features do you expect to work with?*

**INDIVIDUAL TURNSTILES**

- C/A      = Control Area (A002)

- UNIT     = Remote Unit for a station (R051)

- SCP      = Subunit Channel Position represents an specific address for a device (02-00-00)

**DATE & TIME**

- DATE     = Represents the date (MM-DD-YY)

- TIME     = Represents the time (hh:mm:ss) for a scheduled audit event

**STATION & LINE**

- STATION  = Represents the station name the device is located at

- LINENAME = Represents all train lines that can be boarded at this station
           Normally lines are represented by one character.  LINENAME 456NQR repersents train server for 4, 5, 6, N, Q, and R trains.
           
**TRAFFIC**

- ENTRIES  = The cumulative entry register value for a device

- EXIST    = The cumulative exit register value for a device

**OTHER**

- DIVISION = Represents the Line originally the station belonged to BMT, IRT, or IND   

- DESC     = Represent the "REGULAR" scheduled audit event (Normally occurs every 4 hours)
           1. Audits may occur more that 4 hours due to planning, or troubleshooting activities. 
           2. Additionally, there may be a "RECOVR AUD" entry: This refers to a missed audit that was recovered. 

## Tools:
*How do you intend to meet the tools requirement of the project?*

**Tools**

- Ingesting the raw data into a SQL database and querying from that database into Python via SQLAlchemy is required; exploratory analysis and data cleaning in SQL is optional

1. Download .txt files from MTA website
2. Group rename to .csv
4. [CSV to SQLite](https://pypi.org/project/csv-to-sqlite/) script to initialize a SQLite database and bring in all .csv files as tables to database
5. SQLAlchemy to readin SQLite database

- Exploratory data analysis in pandas is required
1. Data cleaning

- Python visualization libraries (such as matplotlib and seaborn) are required; Visualization tools could include more advanced Python libraries such as Bokeh and Plotly or resources outside of python such as Tableau

*Are you planning in advance to need or use additional tools beyond those required?*
- No, not at the moment.

## MVP Goal:
*What would a minimum viable product (MVP) look like for this project?*
- Show steps taken to clean database/database is 'clean' to what extent?
- Visualizations:
1. all traffic at all stations during the year: any months with low traffic?
2. 10 'busiest' stations/amount of traffic AND 10 'quietest' stations/amount of traffic: how big of a difference? which lines? which areas of NYC?
4. Traffic by month AND by day of week for the 10 'busiest' stations
- Ideas for another potential relevant database?
- Am I starting to see any trends based on the above visualizations?
