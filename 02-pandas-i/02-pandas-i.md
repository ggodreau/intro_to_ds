<!--
---
title: Pandas I
type: lesson
duration: "1:00"
creator: [Joseph Nelson](https://twitter.com/josephofiowa)
---
-->

## ![](http://nagale.com/ga-python/images/GA_Cog_Medium_White_RGB.png)  {.separator}

<h1>Pandas I</h1>


<!--

## Overview
This lesson introduces the Pandas library and the beginnings of Exploratory Data Analysis. The majority of the lesson should be spent going through code -- whether that is via Jupyter Slides or a Jupyter Notebook demonstration.

To present this content, begin with `02-pandas-i.md` to introduce Pandas as a library and data integrity. Transition to the Jupyter Notebook to introduce reading in data, column manipulation, filtering and sorting; conclude with exercises.


## Important Notes or Prerequisites

- Review the Iowa liquor dataset [here](https://data.iowa.gov/Economy/Iowa-Liquor-Sales/m3tr-qhgy)
- Be aware that the dataset you are examining is a **subset** of that dataset: it is only May 2017 and May 2018. **New columns** have been created to delineate: `is_may_2017` and `is_may_2018`. These are demonstrated for the purposes of showing filters.
- There are **Class Questions** littered throughout the notebook. Use as much/little time on these as you see fit relative to how your class is pacing
- There is an **Independent Exercise** at the end of this lesson. It is aspirational to have time to let students work entirely independently on this time-wise, so consider doing a guided code-along or paired programming. Answers are included.


## Learning Objectives
In this lesson, students will:
- Use Pandas to read in a dataset.
- Investigate a dataset's integrity.
- Filter, sort, and manipulate DataFrame series.


## Duration
60 minutes

## Suggested Agenda

| Time | Activity |
| --- | --- |

## Suggested Agenda

|    Time     | Activity | Purpose |
|-------------|----------|---------|
| 0:00 - 0:03 | Welcome |
| 0:03 - 0:07 | Pandas and EDA |
| 0:07 - 0:15 | Data Sets and Integrity |
| 0:15 - 0:17 | NOTE: Switch to Notebook |
| 0:17 - 0:25 | Basic Pandas |
| 0:25 - 0:35 | Columns |
| 0:35 - 0:44 | Filtering and Sorting |
| 0:44 - 0:58 | Independent Exercise |
| 0:58 - 1:00 | Summary |

## Materials and Preparation
- Send out the presentation link.
- Students will need the data sets and notebook. Consider having a zip file of all notebooks and data sets for the rest of the unit that you hand out at the beginning of this lesson. Alternatively, link them directly in GitHub - remember that they haven't learned GitHub, so you'll need to help them download the files.
- The presentation is also at the top of the Notebook, so students can later reference in one place. Jump down to `Importing Pandas`.

## Differentiation and Extensions

- If students are excelling in the first half, consider deeper discussions surrounding five number summaries, data integrity, off-the-cuff filters and sorts
- If students are struggling, work on the code more heavily than the **Class Questions** portions. Make the Independent Exercises be Collective Exercises (as a class)

## In Class: Materials
- Projector
- Internet connection
- Jupyter Notebooks
- Python3
-->


---

## Learning Objectives
*After this lesson, you will be able to:*

- Use Pandas to read in a dataset.
- Investigate a dataset's integrity.
- Filter, sort, and manipulate DataFrame series.

<aside class="notes">
**Talking Points**:
This lesson introduces the Pandas library and the beginnings of Exploratory Data Analysis. The majority of the lesson should be spent going through code -- whether that is via Jupyter Slides or a Jupyter Notebook demonstration.

To present this content, begin with `02-pandas-i.md` to introduce Pandas as a library and data integrity. Transition to the Jupyter Notebook to introduce reading in data, column manipulation, filtering and sorting; conclude with exercises.

**Teaching Tips**:
- Review the Iowa liquor dataset [here](https://data.iowa.gov/Economy/Iowa-Liquor-Sales/m3tr-qhgy)
- Be aware that the dataset you are examining is a **subset** of that dataset: it is only May 2017 and May 2018. **New columns** have been created to delineate: `is_may_2017` and `is_may_2018`. These are demonstrated for the purposes of showing filters.
- There are **Class Questions** littered throughout the notebook. Use as much/little time on these as you see fit relative to how your class is pacing
- There is an **Independent Exercise** at the end of this lesson. It is aspirational to have time to let students work entirely independently on this time-wise, so consider doing a guided code-along or paired programming. Answers are included.
- Pause after learning objectives and level-set for what students will get out of the lesson
</aside>

---

## What is Pandas?

- A group of adorable bears 🐼﻿🐼﻿🐼﻿
- A Python library for data manipulation.

<iframe src="https://giphy.com/embed/EatwJZRUIv41G" width="480" height="270" frameborder="0" class="giphy-embed" allowfullscreen=""></iframe>

<aside class="notes">
**Teaching Tips**:

- Get them excited to learn this.
- The iframe is just this gif:![](https://media.giphy.com/media/EatwJZRUIv41G/giphy.gif)
- Show your favorite Pandas gifs [Seriously](https://media.giphy.com/media/z6xE1olZ5YP4I/giphy.gif)
- Describe exploratory data analysis as an **ongoing** process, and cite an example from your experience.

**Talking Points**:

- As we learned, Python libraries are collections of functions and methods that allow us to perform lots of actions without writing as much of our own code.
- The pandas library is written specifically for data manipulation and analysis in Python
</aside>

---

## So, Pandas the Library


The Swiss Army Knife of data manipulation!

Pandas:

- Is *the* library for exploratory data analysis (EDA).
- Formats, wrangles, cleans, and prepares our data.

Quick Backstory from 2009:

- A humble open source project for Panel Data (hence "Pandas") from Wes McKinney.
- Now the most used Python-related tag on Stack Overflow.


<aside class="notes">
**Teaching Tips**:

- Explain what you mean by Swiss Army knife as not all students may understand that metaphor
- Remind students of the meaning of exploratory data analysis (EDA)

**Talking Points**:

"Pandas is the most prominent Python library for exploratory data analysis (EDA). The functions Pandas supports are integral to understanding, formatting, and preparing our data. Formally, we use Pandas to investigate, wrangle, munge, and clean our data. Pandas is the Swiss Army Knife of data manipulation!"
"Pandas began as a humble open source project for Panel Data (hence "Pandas") in 2009 by Wes McKinney. It has grown to be the most use Python-related tag on Stack Overflow."
- Pandas is one of the most useful data manipulation libraries. Its utilities, on the outset, replace many things we know how to do in Excel. However, we also produce a script for creating reproducible steps **and** Excel is limited to 1.3M rows. Pandas is not.
</aside>

---

## Exploratory Data Analysis (EDA)


The process of understanding our dataset and producing our first level of insights.

This includes:

- Reading in data: "Import dog population."
- Checking data types. "Is the population count in integers?"
- Renaming columns: "`dog_breed` is more helpful than `Biological Family`"
- Joining together data: "Join the dog population data with the cat population data."
- Looking for missing data: "It doesn't mention corgis."
- And more!

Today, we will focus on the most 'mission critical' elements of EDA.


<aside class="notes">
**Teaching Tips**:

- Point out from the bulleted list what is mission critical
- Time permitting, ask students to share a similar example of a dataset

**Talking Points**:

- "Exploratory Data Analysis (EDA) is the process of understanding our dataset, and producing our first level of insights. This includes reading in the data, understanding our data dictionary, checking data types, assessing descriptive statistics, renaming columns, joining together data, looking for missing data, and so much more. That sounds like a lot, but today, we will just focus on the most 'mission critical' elements of EDA."
- It's common to get later in the data science workflow, only to realize unclean data or a feature could be engineered earlier in the process.
- Hypothesis-driven EDA is essential to productive EDA -- otherwise we will ceaselessly torture our data for answers.
</aside>

---

## Quick Review

- Exploratory Data Analysis (EDA) is the process of understanding our dataset, and producing our first level of insights.What does this include?
- Pandas is a prominent Python library used for exploratory data analysis


<aside class="notes">
**Teaching Tips**:

- Pause to gather students' answers about what EDA includes.
- Answer any clarification questions!
</aside>

---

## What dataset are we exploring?


- Iowa liquor sales!

- Stores report daily transactions of all alcohol they sell.

- Iowa makes this data available.
  - It is an excellent, structured dataset for analysis!

Take a look at the data source [page](https://data.iowa.gov/Economy/Iowa-Liquor-Sales/m3tr-qhgy).


<aside class="notes">

**Teaching Tips**:

- Open this page in a new window.

**Talking Points**:

- For today's Pandas exercises, we will be using a real dataset from the state of Iowa government on liquor sales. Due to state licensing laws, stores must report daily transactions of all alcohol they sell to the Iowa Department of Commerce's Alcoholic Beverages Division. The state of Iowa makes this data available for analysis -- and it is an excellent, structured dataset for our use!

[Go down the list for students.]

Let's take a closer look at the data dictionary, or what is included:

- **Invoice/Item Number** - Concatenated invoice and line number associated with the liquor order. This provides a unique identifier for the individual liquor products included in the store order
- **Date** - Date of order
- **Store Number** - Unique number assigned to the store who ordered the liquor.
- **Store Name** - Name of store who ordered the liquor.
- **Address** - Address of the store that ordered the liquor
- **City** - City where the store who ordered the liquor is located
- **Zip Code** - Zip Code of where the store that ordered is located
- **Store Location** - Location of store who ordered the liquor. The Address, City, State and Zip Code are geocoded to provide geographic coordinates. Accuracy of geocoding is dependent on how well the address is interpreted and the completeness of the reference data used.
- **County Number** - Iowa county number for the county where store who ordered the liquor is located
- **County** - County where the store who ordered the liquor is located
- **Category** - Category code associated with the liquor ordered
- **Category Names** - Category of the liquor ordered.
- **Vendor Number** - The vendor number of the company for the brand of liquor ordered
- **Vendor Name** - The vendor name of the company for the brand of liquor ordered
- **Item Name** - Item number for the individual liquor product ordered.
- **Item Description** - Description of the individual liquor product ordered.
- **Pack** - The number of bottles in a case for the liquor ordered
- **Bottle Volume (mL)** - Volume of each liquor bottle ordered in milliliters.
- **State Bottle Cost** - The amount that Alcoholic Beverages Division paid for each bottle of liquor ordered
- **State Bottle Retail** - The amount the store paid for each bottle of liquor ordered
- **Bottles Solde** - The number of bottles of liquor ordered by the store
- **Sale (Dollars)** - Total cost of liquor order (number of bottles multiplied by the state bottle retail)
- **Volume Sold (Liters)** - Total volume of liquor ordered in liters. (i.e. (Bottle Volume (ml) x Bottles Sold)/1,000)
- **Volume Sold (Gallons)** - Total volume of liquor ordered in gallons. (i.e. (Bottle Volume (ml) x Bottles Sold)/3785.411784)
</aside>


---

## Discussion: What Could We Examine?

- What are some potential insights you'd like to uncover given Iowa liquor data?

- What if you are examining it from the standpoint of the Iowa government?

- What if you are a potential liquor store business owner?

<aside class="notes">
**Teaching Tips**:

- Walk through these questions one by one. Encourage discussion - there's no wrong answer!
- For the standpoint of the Iowa government and business owner, ask why?

</aside>
---

## Our Modified Iowa Liquor Dataset


The full dataset is  all liquor sales from 2012 to present.

There are more than 13 million rows (13,948,103+ at the time of writing)!

We will work with a modified dataset.

Key changes:

- Only sales from May 2017 and May 2018
- Intentionally deleted:
    - A number of values, to practice missing data.
    - An arbitrary subset of entire observations, to shrink it.
    - A few columns, to simplify.


<aside class="notes">

**Teaching Tips**:
- The first portion explains why we are using a modified version of this dataset
- Describe how messy, long, and sometimes complicated actual datasets can be
- Encourage students to conceptualize how they could use the dataset from the State of Iowa's perspective as well as a prospective liquor store owner. This invests students in potential conclusions from EDA.
- Walkthrough the dataset directly on the Iowa gov't [page](https://data.iowa.gov/Economy/Iowa-Liquor-Sales/m3tr-qhgy).

**Talking Points**:
- The raw dataset itself is nearly 4GB, so we have trimmed the dataset to be *just* May 2017 and May 2018. Your RAM is welcome!
- The State of Iowa may be most interested in incoming tax revenue, and predicting how much to expect
- A prospective liquor store owner may be interested in seeing top selling areas in the state -- but using a separate (not included) dataset on population to identify regions where per capita consumption is high, yet liquor supply is comparatively low. Moreover, liquor store owners may care most about bottles sales compared to bottle retail prices (all in the dataset!)
- Like EDA, data integrity checks are an ongoing process.
- Key changes:
  - Only sales from May 2017 and May 2018
  - A number of values have been deliberately deleted.
    - Practice working with missing data!)
  - An arbitrary subset of entire observations have been deleted.
    - Reduce the file size from 119MB to <100MB.
  - A few columns were removed (invoice, address, vendor number, category as a number, county number)
</aside>

---

## The First Few Rows

![](https://s3.amazonaws.com/ga-instruction/assets/python-fundamentals/dataset-screenshot-1.png)


<aside class="notes">

**Teaching Tips**:

- Walk through this to familiarize them with how a dataset looks.

</aside>

---

## The First Few Rows (Ctd)

![](https://s3.amazonaws.com/ga-instruction/assets/python-fundamentals/dataset-screenshot-2.png)


<aside class="notes">

**Teaching Tips**:

- Walk through this to familiarize them with how a dataset looks.

</aside>


---


## Data Integrity


The first thing we check! Assuring our data can be trusted to produce meaningful insights.

Correctly formatted datatypes.

- "Decimals are floats, not strings."

Representative sample for the underlying population of interest.

- "Did we sample sales in cities or across the whole state?"

Missing Data

- "Why do we only have even days of the month?"

No sampling or human bias.

- "Did we only consider liquor sales of specific varieties?"



<aside class="notes">
**Talking Points**:

- Ask how you might keep data integrity top of mind to maintain a clean data set
- Give examples here.

**Teaching Tips**:

- Pause here to ask if students have any questions
</aside>

---

## Clean Truth about Dirty Data

- Assessing data integrity isn't a one-stop step.

- Much like EDA itself, it's an ongoing process!

- We uncover additional potential problems and anomalies to remedy along the way.

<aside class="notes">
**Talking Points**:

- Ask how you might keep data integrity top of mind to maintain a clean data set
- Give examples here.

**Teaching Tips**:

- Give examples here.

</aside>

---

## Launch our notebook

We'll work in the Notebook
- We're fledgling data scientists!

The `.ipynb` file you will open is called " `pandas-i.ipynb` ".


Open it up!

Jump down to `Importing Pandas`.


<aside class="notes">
**Teaching Tips**:

- Make sure everyone gets to the notebook successfully.
- Have students assist one another and walk around the room to ensure everyone gets to the notebook successfully
- Make sure all students can open and run their Notebooks. It's only the second time they've done so!
- The presentation is also at the top of the Notebook, so students can later reference in one place. Jump down to `Importing Pandas`.
</aside>

---

## Additional Resources

- Pandas [documentation](https://pandas.pydata.org/pandas-docs/stable/)
- DataSchool [30-video series](http://www.dataschool.io/easier-data-analysis-with-pandas/) (by a former GA instructor!)
