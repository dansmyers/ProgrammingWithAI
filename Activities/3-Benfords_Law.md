# Benford's Law

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Rozklad_benforda.svg/1920px-Rozklad_benforda.svg.png" width="400px" />

## Overview

Benford's Law is one of the all-time great "I can't believe this is a thing" results. It states that, in many real-world quantitative data sets, **1 is by  far the most common leading digit**. Specifically, slightly more than 30% of the numbers in the data set should start with a leading 1.  About 17% of data values should start with 2, and about 13% start with 3. Leading 9's occur less than 5% of the time. 

This is surprising, because you might expect the distribution of leading digits to be uniform, with about 11% of entries starting with 1, another 11% with 2, and so forth.

The law is named after physicist Frank Benford, who called it *The Law of Anomalous Numbers* in a 1938 paper. Benford's Law has applications to fraud detection and accounting, because it can be used to identify fake data that has an unnatural distribution.

You're going to write a program to validate Benford's Law against a real-world data set: the county-level population estimates produced by the U.S. Census Bureau.

## Setup

Use the same setup steps as the previous activity. Start by using the `cd` command in your terminal to move to your `1-Generation` directory:
```
cd 1-Generation
```
You can then create a file named `benford.py`:
```
touch benford.py
```

## Install Pandas

Pandas is the Python framework for data analytics. It includes functions that can read, process, and analyze data sets in most common formats. AI is *great* at writing Pandas code for analytics projects.

Install Pandas using the `pip` command:
```
pip install pandas
```
You'll also need to install matplotlib for plotting:
```
pip install matplotlib
```


## Get the data

County-level population estimates are availble on the Census Bureau's web site:

https://www.census.gov/data/tables/time-series/demo/popest/2020s-counties-total.html

Scroll down to find the file `co-est2024-alldata.csv` near the bottom of the page and then upload it to your `1-Generation` directory. If you open the file, you'll see a series of lines link the following:

```
SUMLEV,REGION,DIVISION,STATE,COUNTY,STNAME,CTYNAME,ESTIMATESBASE2020,POPESTIMATE2020,POPESTIMATE2021, POPESTIMATE2022
040,3,6,01,000,Alabama,Alabama,5024356,5031362,5049846,5074296
050,3,6,01,001,Alabama,Autauga County,58802,58902,59210,59759
050,3,6,01,003,Alabama,Baldwin County,231761,233219,239361,246435
050,3,6,01,005,Alabama,Barbour County,25224,24960,24539,24706
050,3,6,01,007,Alabama,Bibb County,22300,22183,22370,22005
```

The first line lists the names of each field. The data is organized alphabetically by state, then by county within each state. The first line of data is the population for the entire state of Alabama, followed by the estimate for Autauga county, and so forth. The first entries on each line are some numerical encodings used by the census bureau to identify each county (notice that the entire state has a `COUNTY` code of `000`).

Notice that individual fields are separated by commas with no spaces. If you've worked with Excel, you may have used this type of **comma-separated value** (CSV) file to encode spreadsheet data in text format: each line corresponds to one row in the spreadsheet and each comma-separated value to a column within the row.

## Chat about the analysis

Go to your Claude chat.

Drop the CSV file into your chat window, then ask about analyzing it:
```
I need to analyze the county level population estimates from this file to check if they obey Benford's Law. The column I want to check is POPESTIMATE2024. I would like you to generate a Python script that will open this file using Pandas, extract that column, then output a bar chart showing the frequency of occurrence of each leading digit in the population estimates. Save the chart to a .png file.

Ask me if you have questions, then generate the Python script. You don't need to run the analysis, just give me the code.
```
Claude may ask a few questions. If it does, answer them, then copy the code it generate into your `benford.py` file on Codespaces.

## Run the program

Try running `benford.py`:
```
python3 benford.py
```
If you get errors:

- Make sure you've installed the required packages using `pip`, as discussed above
- Check the line that loads the data in `benford.py`. It may show a long file path that doesn't match up with the location on your system. If so, change it to `'co-est2023-alldata.csv'`

### UnicodeDecodeError
Once you get past those problems, you may get another error that seems unusual:
```
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xf1 in position 13791: invalid continuation byte
```
Huh?

Take this error and paste it into Claude and ask for an explanation.

- What is UTF-8 and what is its relation to Unicode?
- What is the likely cause of this error?

### Solution
It turns out that the data in the CSV file is encoded using a standard called ISO-8859-1, which is not the default that Pandas expects. Ask Claude to update the solution, or manually change the `read_csv` line to the following:
```
df = pd.read_csv('co-est2024-alldata.csv', encoding='iso-8859-1')
```

**Here's a key idea**: Using AI doesn't remove the need to think occasionally fix problems and understand what the program is really doing. Fortunately, AI is also good at helping you diagnose bugs and explain their likely causes.


### Ouptut

You should now be able to open the CSV, read its data, and have your program output the bar chart.

Take a look at the chart and verify that the results you see match up with the example distribution given above.
