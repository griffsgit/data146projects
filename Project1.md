
1. Describe what is a package? Also, describe what is a library? What are the two steps you need to execute in order to install a package and then make that library of functions accessible to your workspace and current python work session? Provide examples of how you would execute these two steps using two of the packages we have used in class thus far. Be sure to include an alias in at least one of your two examples and explain why it is a good idea to do so.

A package is a directory of modules. Modules are just python files with specific functions or code. A library is collection of related functions for use in other programs, to be called and referred to at various times. The two steps you need to execute are to first install a package. You can do this in Pycharm by going to ‘file>settings>python interpreter’ then selecting and adding a specific package. Then, the next step in order to then make these packages accessible in your current work session is importing them. To import packages, you have to write out the command to do so. The way I would do this is seen below in two examples:

>import datetime
>import pandas as pd

I included an alias, “pd”, for pandas because repeatedly referring to pandas as “pd” is much shorter and more convenient than having to use the full name when referencing it each time. 



2. Describe what is a data frame? Identify a library of functions that is particularly useful for working with data frames. In order to read a file in its remote location within the file system of your operating system, which command would you use? Provide an example of how to read a file and import it into your work session in order to create a new data frame. Also, describe why specifying an argument within a read_() function can be significant. Does data that is saved as a file in a different type of format require a particular argument in order for a data frame to be successfully imported? Also, provide an example that describes a data frame you created. How do you determine how many rows and columns are in a data frame? Is there an alternate terminology for describing rows and columns?

A data frame is a data structure composed of rows and columns, and is two-dimensional. One library that is particularly useful for working with dataframes is Pandas. In order to read a file in its remote location within the file system of my operating system, I would use the command “pandas.read_csv()”. You first need to import pandas, then use the command “pandas.read_csv()”, in order to read a file and import it into your work session. An example of how to read a file and import it in order to create a new data frame is below. An additional line of code that is needed to clarify the file path to access this data.

Import pandas as pd
data_path = 'C:/Users/griff/PycharmProjects/pythonProject/gapminder.tsv'
readstuff = pd.read_csv(data_path, sep=’\t’)



Specifying an argument within a read_() function can be significant because in order to import data from these files, you will need to specify the specific format. The argument within this function is used to clarify which format is used. For instance, if the data file is separated with tabs it is necessary to use “sep = ‘\t’”, but if the file is separated with spaces, using “sep = ‘\s’”. As can be seen, different formats use different arguments, and are necessary to ensure that information can be properly accessed. 

An example that describes a data frame I created is:

Import pandas as pd
data_path = 'C:/Users/griff/PycharmProjects/pythonProject/gapminder.tsv'
readstuff = pd.read_csv(data_path, sep=’\t’)

To describe the data, you can use readstuff.describe(), or readstuff.head().

In order to determine how many rows and columns are in a dataframe, you can use  readstuff.shape() in order to get the number of rows and columns. This returns the number of rows and columns in a dataframe, in parentheses separated by a comma.

An alternate terminology for describing rows and columns would be “variables” for rows, and “observations” for columns.

3. Import the gapminder.tsv data set and create a new data frame. Interrogate and describe the year variable within the data frame you created. Does this variable exhibit regular intervals? If you were to add new outcomes to the raw data in order to update and make it more current, which years would you add to each subset of observations? Stretch goal: can you identify how many new outcomes in total you would be adding to your data frame?

Here I imported the data set and created a new data frame:

import pandas as pd

path_to_file = 'C:/Users/griff/PycharmProjects/pythonProject/gapminder.tsv'
data = pd.read_csv(path_to_file, sep='\t')


Interrogate and describe the year variable within the data frame you created: 

years= data['year']
print(years)


In return, I got:
0       1952
1       1957
2       1962
3       1967
4       1972
        ... 
1699    1987
1700    1992
1701    1997
1702    2002
1703    2007


It appears that the years are recorded in intervals of 5.

If I were to add new outcomes to the raw data in order to update and make it more current, I would add 2012, 2017, and (next year) 2022.



4. Using the data frame you created by importing the gapminder.tsv data set, determine which country at what point in time had the lowest life expectancy. Conduct a cursory level investigation as to why this was the case and provide a brief explanation in support of your explanation.

Using the data frame you created by importing the gapminder.tsv data set, determine which country at what point in time had the lowest life expectancy: 

new_object_with_idxmin_lifeexp = data['lifeExp'].idxmin()

print(data.loc[new_object_with_idxmin_lifeexp])

What I got in return was:

country          Rwanda
continent        Africa
year               1992
lifeExp          23.599
pop             7290203
gdpPercap    737.068595
Name: 1292, dtype: object


I think the reason Rwanda had the lowest life expectancy in 1992 of anywhere was because of the ongoing Rwandan Civil War. Looking at this period in Rwanda in the early 1990s, it appears they had a problem with internal conflict, which would likely contribute to a life expectancy by creating dangerous and destabilized living conditions. Only two years later, there would be the Rwandan Genocide.



5. Using the data frame you created by importing the gapminder.tsv data set, multiply the variable pop by the variable gdpPercap and assign the results to a newly created variable. Then subset and order from highest to lowest the results for Germany, France, Italy and Spain in 2007. Create a table that illustrates your results (you are welcome to either create a table in markdown or plot/save in PyCharm and upload the image). Stretch goal: which of the four European countries exhibited the most significant increase in total gross domestic product during the previous 5-year period (to 2007)?

|      | Country | Continent | Year | lifeExp | pop      | gdpPercap   | gdp          |
|------|---------|-----------|------|---------|----------|-------------|--------------|
| 1427 | Spain   | Europe    | 2007 | 80.941  | 40448191 | 28821.06370 | 1.165760e+12 |
| 779  | Italy   | Europe    | 2007 | 80.546  | 58147733 | 28569.71970 | 1.661264e+12 |
| 539  | France  | Europe    | 2007 | 80.657  | 61083916 | 30470.01670 | 1.861228e+12 |
| 575  | Germany | Europe    | 2007 | 79.406  | 82400996 | 32170.37442 | 2.650871e+12 |



6. You have been introduced to four logical operators thus far: &, ==, | and ^. Describe each one including its purpose and function. Provide an example of how each might be used in the context of programming.


&, : This is the bitwise ‘and’ operator. This is used to verify that both conditions are true, and will return a true if so. A use of this is in ‘if statements’, which would only be executed if both conditions are met. An example is:

Specific_thing= data[(data[‘year’]==2007) & (data[‘country’]==’United States’)]

This returns only the data that is both from 2007 and from the United states.

== : ‘==’ is a binary operator, which returns true or false depending on whether the values of operands are equal or not. An example of it being used is when you need to get specific data:

cont = 'Europe'
idxCont = data['continent']==cont

This only gets data when the continent is equal to Europe

 | : This is a bitwise ‘or’ operator. It can be used to check whether one or both of two conditions are true, and if at least one is, it will return true. An example of it being used is: 

Specific_thing= data[(data[‘country’]==’United States’)|(data[‘year’]==2007)]

This gets data that is from the United States, 2007, or both.

^: bitwise ‘xor’ operator. It is used to check two statements, and return true if one, but not both, of the statements is true. An example of it being used is to find variables that are equivalent to one thing, or another, but not both: 

Specific_thing= data[(data[‘country’]==’United States’)^(data[‘year’]==2007)]

This gets you data that is from the United States, or from 2007, but will not return data from the United States during 2007.


7. Describe the difference between .loc and .iloc. Provide an example of how to extract a series of consecutive observations from a data frame. Stretch goal: provide an example of how to extract all observations from a series of consecutive columns.


Both do similar things, but .loc and .iloc work differently. Loc is based on labels, so you have to use row and column labels to specify rows and columns. Iloc is based on integer index, so you have to use integer index to specify rows and columns.

We can extract a series of consecutive observations from a dataframe by doing the following:

data.iloc[1:4]


What this will do is return all of the integer positions between 1 and 4.


8. Describe how an api works. Provide an example of how to construct a request to a remote server in order to pull data, write it to a local file and then import it to your current work session.

API is an abbreviation that stands for ‘application programming interface’. APIs allow different applications to more cohesively interact with each other. In the context of our class, we use APIs to help python work with different websites that supply data, such as a website with Covid case information. APIs allow Python to request data from these websites, and get it automatically. 

To construct a request to a remote server in order to pull data, you can do the following: 

First we need to make a folder for the data to go:

url = "https://api.covidtracking.com/v1/states/daily.csv"
import os
data_folder = 'data'
if not os.path.exists(data_folder):
    os.makedirs(data_folder)

Then, we need to create the file for this data:

file_name_short = 'ctp_' + str(dt.now(tz = pytz.utc)).replace(' ', '_') + '.csv'
file_name = os.path.join(data_folder, file_name_short)

Then we need to request the data from the website:

Import requests

url = "https://api.covidtracking.com/v1/states/daily.csv"

r = requests.get(url)


Lastly, we need to write the data to the local file, and read it in our workspace:


with open(file_name, 'wb') as f:
    f.write(r.content)

import pandas as pd
df = pd.read_csv(file_name)




9. Describe the apply() function from the pandas library. What is its purpose? Using apply) to various class objects is an alternative (potentially preferable approach) to writing what other type of command? Why do you think apply() could be a preferred approach?

The apply() function in the panda library allows you to apply a function to an entire DataFrame. You can use lambda or other functions. This is an alternative to using a loop to iterate through a dataframe and apply a function. Because of its increased simplicity, it might be a preferred approach.


10. Also describe an alternative approach to filtering the number of columns in a data frame. Instead of using .iloc, what other approach might be used to select, filter and assign a subset number of variables to a new data frame?


An alternative way of filtering the number of columns in a data frame is to get the specific desired columns by referencing them specifically. You can do this by referencing a subset number of variables like so:

data[[‘year’, ‘lifeExp’,’pop’, ‘gdpPercap’]]

And then to assign this subset number of variables to a new data frame, do the following:

subset_data=data[[‘year’, ‘lifeExp’,’pop’, ‘gdpPercap’]]







