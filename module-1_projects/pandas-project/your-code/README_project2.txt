## Project Data Cleaning and Manipulation with Pandas

# First Step: Preparation

This step was used to import the necessary packages like pandas and numpy as well as uploading the csv file by using pd.read_csv. A problem occured while uploading, but specifying the encoding method as latin1 helped.
It was also useful to take the clean date our of the case number using .str.slice.
For more convinience in the future, I already at this stage renamed the column Case Number to case_number using df.rename and then assigned this column as an index using df.set_index, because this column consists of unique values.

# Second step: Missing values and adjusting the table

I started with counting the null values in columns using the .isnull().sum() method. As a result I've received different values, but it was important to count which part of all values in column do these nulls occupy, that is why I've also devided through the length of the dataframe.

I've made an assumption, that I am going to drop the columns where the percentage of all nulls is going to be more than 10%, such as in age, time, unnamed22 and unnamed23, but there were additional columns, which contained not interesting for us information such as pdf, href formula, href, case number 1, case number 2, original order and the date since I've created a new column called clean_date. For this case I've used df.drop method. 

The next step was to make the column names in lower case and replace the spaces between words using '_'. In this case I've applied the .str.replace() and .str.lower. If the problem occured like with sex_, I just replaced it with sex using the df.rename.

After I tried to adjust the country column by using .str.title(), but that also caused the problem with "USA" being "Usa". In this case I've used the replace method to make it back "USA". Before these manipulations I've filled in the null values with "UNKNOWN" using .fillna().

Then, I've adjusted the values in the columns sex and fatal to the lowercase using .str.lower().

I wanted to get the column ivestigator_or_source cleaned from the date, which appeared after the ','. For this case I firstly used the .str.split() method and the assigned these splitted values to the two new columns. After that I've used df.drop to drop the original column as well as one with the splitted date. 

Next step was to get rid of the rows, where in the column year was 0. To do this, I have assigned the previous database to the new one, but specifying, that the year column cannot be equal to 0 (!=0). 

I still didn't want to leave any null values, that is why I've used the .fillna() to fill in the "unknown" to the columns.

# Third step: Data types

I was interested to find out which data types are presented in my column using df.dtypes. In turns out, that all of the are object, but year is an integer. So I 've used .astype method to do it.

# Changing the order of the columns and exporting

I wanted to clean_date to come directly after the index, so I've reassigned the columns to the new dataframe in the order that I wanted. 

Final step was to export the file using the .to_csv method and specifying the name of the new file.