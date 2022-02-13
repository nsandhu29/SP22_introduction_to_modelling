# Data terminology

In this lesson, we'll talk about many of the different
types of data you might encounter in analytics.
And just as importantly, we'll go through some of the
terminology that analytics and data science
professionals use for different types of data.

Usually people in analytics talk about data as if
it's in a table, in this table, **every row is called
a data point**, it's a single observation of information.

credit score |income |zip code |repaid?  
--|---|---|--
 745 |$55,000 |30324 |100%  
 620 |$40,000 |55783 |100%  
 700|$92,500  |57197 |50%  

For example, if we're looking at past loan applicants to
see which future applicants might be good credit risks
than each applicant would be a data point.

daily sales |Day of the week | holiday  
--|---|---
  11,235 | Monday |no  
  13,030 | Tuesday | no  
  24,134| Wednesday  | no  

Or if we're analyzing daily sales to predict what
future sales will be, then each day would be a data point.

Each column of the table is a piece of information
about every data point, for example, in the credit risk
table, one column of data might contain each applicant's
credit score, another column might contain each applicant's
household income and a third might
contain each applicant's zip code.

In the sales prediction example, one column of data
might contain the number of sales on that day,
a second might contain the day of the week
and a third might indicate whether
or not the day was a holiday.
**Every row is called the data point.**

For columns, there are lots of different names.
They're often called **attributes or features**
and depending on how the data is being used,
they might also be called **covariates or predictors.**

There's also a special type of column known as the **response
or outcome**, you can think of this column as being
the answer for each data point.
For loan applicants, it's the observation of whether they
repaid the full loan or not or it could be the fraction
of the loan they repaid from zero to 100%.
For sales, the response could be the
number of sales recorded on each day.

## Data Types
### Structured and Unstructured data
- Structured
  - structured data is what most people envision when we think of data, there are some formal technical definitions of 
    structured data but essentially, **it's data that can be described and stored in a nice structured way**
  - Example(Quantitative), credit score,
age, number of sales, etc are all stored as numbers.
  - Example(Categorical), M/F, Hair Color et cetera.


- Unstructured
  - **unstructured data isn't easily described and stored**
  - Example written text

### Common types of structured Data

- Quantitative
  - numbers with meaning
     - Example age, sales, temperature, income
     - Higher means more, lower means less


- Categorical
  - Numbers without meaning
    - Example Zip code
    - Higher/lower is not meaningful
  - Non - numeric:
    - Example hair colour
    

- Binary data (Subset of Categorical data)
   - Can only take two values
     - Example Male/Female, repaid in full (Y/N), ON/OFF
     - In some cases we treat this as a Quantitative measure


- Unrelated data
   - No relationship between data points
     - Example different customers, loan applicants, etc .

- Time series data
  - Data is related in time.For example, let's go back to our daily sales data. Each data point refers to one day and we have an attribute that records each day's sales, one after the other. If we put those data points in chronological order, then reading down the column of data shows the number of sales made day by day, one after another.
  - Same data recorded over Time
  - Often recorded at equal intervals (Doesn't have to be)
  - Example Daily sales, stock prices, child's height on each birthday.
