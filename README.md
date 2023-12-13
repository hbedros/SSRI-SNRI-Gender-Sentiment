# SSRI-SNRI-Gender-Sentiment
DATA607 Final Group Project

by Gavriel Steinmetz-Silber, Noori Selina, Zainab Oketokoun, and Haig Bedros

# Part A: National Center for Health Statistics
Data Source: https://www.cdc.gov/nchs/hus/data-finder.htm?year=2019&table=Table%20009

# Introduction:
Since COVID, various news outlets have been reporting on what they are calling a mental health crisis in the United States in individuals of all age groups. The CDC reports that 1 in 25 US Adults lives with serious mental health conditions e.g. major depression. The NIMH reports that mental disorders cost the U.S. 193 billion dollars alone annually in lost earnings.

We wanted to investigate if there were patterns relating to mental health over years to determine if there is a mental health crisis occurring and if so ,is it an one that is on the rise  or are we, the American public, just noticing an existing condition.
 We looked to the CDC to get annual data on mental health in the U.S. After looking at variety of variables, we decided that death by suicide rates were a traceable phenotype. The initial struggle was having to load the file as an excel and then having to rename columns , changing class types repeatedly and eliminating “N/A”  before we could even transform the data. We fixed this issue by locating an API key.We loaded the data using an API key by first defining the URL, and reading it in as a csv file. The next challenge was splitting variables. For example we had a column that had combined Sex (alone) and Sex + Ethnicity together in one column.
We use dplyr, tidyverse and stringr, to remove ethnicity from genders and combine Race and Ethnicity related information to one column. We simplified all female related information to the variable = “female” , did the same for the males and combined it all into one column. We removed and rewrote column names. We aggregated variables like e.g.year and sex to create a plot showing the trend of mental health over the years for the different sexes, ethnicities and  age_range groups.

# Part A: Conclusion

We observed a difference in rates between different races/ethnic groups, however we believe that since there is a large amount of missing data , the analysis needed heavy transformation to not calculate a heavily skew  analysis. We do recognize that it was not until 1995 that the NIH mandated that clinical and field work -NIH funded- projects must include participants from POCS and marginalized groups. This may account for the  low values in the POC groups in comparison to the Whites.

Lastly, the increase of the death rates as the years increase, suggest that the country is uncovering  an existing mental health problem or that there is one on the rise.

We decided to further explore Sex differences and engage with data that reflect real-life patient experiences and investigate if there is a pattern indicating a difference in experience between male and female patients.

We lead our statistical analysis by having a null hypothesis stating there would be no differences seen for death by suicide rates between sex, between ethnic groups and between age_range groups.
First we use dplyr to determine summary stats ,and followed this up by using ggplot to compare center(mean) and spread of males rates to female rates, center and spread of the rates between the different ethnic groups and center and spread of the rates between the different age range groups. Then we used the Levene test( under the package “car”) to determine if the variance was equal between the groups. We use LearnBayes package to determine correlation value between death rates and Sex and lastly, we used a one.way test for an ANOVA test to identify the statistical significance of the difference seen in the age groups.

# Part B: Sentiment analysis

To gather the reviews, we will scrape from WebMD (e.g. https://reviews.webmd.com/drugs/drugreview-63990-lexapro-oral). All the pages have a similar format. There appear to be boxes, with some basic user info on top and then the content of the review below. There are also some star ratings, but we will rely exclusively on the text for this project.

Inspecting the webpages further, we see that each review is under the headers of review sections are marked as ".card-header"). So we can use this as part of a loop. Further, within each review, we can find the user informatoin by looking for the class .details. We can find the date by looking for the class .date. And we can find the text of the review by looking for the immediately following class .description. that contains a paragraph of the class "description-text."

Now, one struggle is that there are only 20 reviews on a page but each drug has many, many reviews. For Lexapro, I see there are 215 pages (so presumably around 215 x 19 to 20 total reviews). However, for each drug there's also a consistent format. Taking Lexapro again, the format is: "https://reviews.webmd.com/drugs/drugreview-63990-lexapro-oral?conditionid=&sortval=1&page=[page number]&next_page=true"

# Part B: Conclusion
In conclusion, our extensive analysis of antidepressant reviews from WebMD has provided valuable insights into the gender dynamics of sentiments expressed by users. Our analysis of antidepressant reviews from WebMD sheds light on distinct gender dynamics in user sentiments, particularly concerning SSRIs and SNRIs. SNRIs, such as Cymbalta and Effexor, revealed a gender-neutral trend, indicating consistent experiences among male and female users. In contrast, SSRIs like Lexapro and Prozac exhibited statistically significant differences in sentiment scores, hinting at nuanced emotional expressions between genders. The findings emphasize the necessity of recognizing these variations for a more informed and personalized approach to mental health care.

As for future recommendations, healthcare professionals should be attentive to the diverse ways male and female users express their experiences with antidepressants, and taking note of the adverse reactions that may occur based on gender. Future research endeavors could explore qualitative aspects of reviews to unveil the underlying factors contributing to gender-based differences. Additionally, similar studies should also be conducted on non-binary and transgender patients as well to grasp a better understanding of how the mentioned drugs affect those gender groups as well, this would be a more inclusive approach.

