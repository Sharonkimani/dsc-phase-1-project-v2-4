# Phase 1 Project

## Project overview

 ### project goals/ objectives
* To find out the top films  at the box office
* To find out the film genres with the highest ratings and those with the lowest ratings
* To find out the relationship between runtime and the rating of the films
* To find out the relationship between runtime minutes and number of votes
* To find out the relationship between the domestic gross and foreign gross

### project audience
The audience of this project is the microsoft business stakeholders.

### project dataset
This project used two datasets; the bom movie gross data and the im.db sql database.
* [Box Office Mojo](https://www.boxofficemojo.com/)
* [IMDB](https://www.imdb.com/)

In the sql database, the focus was on the movie basics and movie ratings tables. Exploratory data analysis of both these datasets was used  to generate insights for  the microsoft business stakeholder.

### Business Problem

In the film industry, the ability to predict a movie’s box-office revenues before its theatrical release can decrease its financial risk. However, accurate predictions are not easily obtained. The complex relationship between movie-related data and movie box-office revenues, plus the increasing volume of data in online movie databases, pose challenges for their effective analysis.This analysis will take into considerations two datasets to try and understand the types of films that are currently doing the best at the box office in order to decide what type of films microsoft should create, the genre of movies with the highest rating in order to decide which genre of movies microsoft should focus on more, the relationship between runtime minutes of the films and the ratings of the films and also the number of votes in order to decide how long the films microsoft will create be.


###  Data understanding 

This project used two datasets which are in the folder `zippedData`. The datasets are from:

* [Box Office Mojo](https://www.boxofficemojo.com/)
* [IMDB](https://www.imdb.com/)

Because it was collected from various locations, the  files have different formats. The bom gross movie is a  compressed CSV (comma-separated values) file that has 5 columns in which the title column,studio column and foreign gross column contains object type data,the domestic gross column has data of data type,float and  the year column contains data of data type ,integer. The data from IMDB is located in a SQLite database. The IMDB database is as shown below;

![movie data erd](https://raw.githubusercontent.com/learn-co-curriculum/dsc-phase-1-project-v2-4/master/movie_data_erd.jpeg)

This project only considered `movie_basics` and `movie_ratings` tables since they are most relevant.


### Data analysis
##### bom movie gross data
The numerical columns are; domestic_gross, foreign_gross and year. The count represents the number of non empty values in the column. Since the dataset doesn't have any missing values , the count is 2037,the number of rows the dataframe has. Let's focus on foreign gross and domestic gross. The mean of the columns are 46,346,680 and 74,872,800 for domestic gross and foreign gross respectively. The standard deviation is 81,210,240 and 13,741,060 for domestic gross and foreign gross respectively.Their standard deviation is quite large ,implyimg that in both columns, the data values are widely dispersed about their mean, that is, they are further away from the mean. The minimum values for domestic gross and foreign gross respectively are; 400 and 600 while the maximum values for domestic gross and foreign gross respectively are; 936,700,000 and 960,500,000. The 25% percentile for domestic gross and foreign gross respectively is;6,970,000 and 3,700,000 while the 50% percentile,which is the median, for domestic gross and foreign gross respectively is;15,500,000 and 18,700,000 and the 75% percentile for domestic gross and foreign gross respectively is;55,500,000 and 74,900,000.

On comparing the mean and the median in both columns;in the domestic gross column, the mean is higher than the median implying that the data is skewed to the right,that is, it is positively skewed. In the foreign gross column, the mean is also higher than the median, implying that it is also positively skewed.

Let's visualize this;
![histogram of foreign and domestic gross](https://github.com/Sharonkimani/dsc-phase-1-project-v2-4/blob/master/histogram%20of%20foreign%20and%20domestic%20gross.PNG )


The histogram shows that the data in both columns is positively skewed. The correlation between domestic gross and foreign gross is 0.768451 which indicates that the two variables have a strong relationship and that they are positively correlated ,that is, increase in domestic gross leads to increase in foreign gross and vice versa. We can visualize this using a scatter plot.

![relationship of foreign and domestic gross](https://github.com/Sharonkimani/dsc-phase-1-project-v2-4/blob/master/foreign%20vs%20domestic.PNG )

The correlation between foreign_gross and year is 0.145653 which is a positive correlation, though not strong, implying that as years go by, the foreign gross increases. The correlation between year and domestic gross is 0.122727 ,which is a positive correlation, implying that as years go by the domestic gross increases.

Sorting the dataframe using the foreign gross, the top 5 movies are;Harry Potter and the Deathly Hallows Part 2, Avengers: Age of Ultron, Marvel's The Avengers, Jurassic World: Fallen Kingdom and Frozen.Sorting the dataframe using the domestic gross, the top 5 movies are;Star Wars: The Force Awakens, Black Panther, Avengers: Infinity War, Jurassic World and Marvel's The Avengers.

###### im.db sql data
The numerical columns are; runtime_minutes, average_rating, numberof votes and start_year. The count represents the number of non empty values in the column. Since the dataset doesn't have any missing values , the count is 65720,the number of rows the dataframe has. Let's focus on runtime_minutes, average_rating and number of votes. The mean of the columns are 94.73, 6.32 and 3954.67 for runtime_minutes, average_rating and number of votes respectively. The standard deviation is 209.37, 1.459 and 32,088.23 for runtime_minutes, average_rating and number of votes respectively.Their standard deviation is quite large ,implyimg that in these columns, the data values are widely dispersed about their mean, that is, they are further away from the mean. The minimum values for runtime_minutes, average_rating and number of votes respectively are; 3, 1 and 5 while the maximum values for runtime_minutes, average_rating and number of votes respectively are; 51420,10, and 1,841,066. The 25% percentile for runtime_minutes, average_rating and number of votes respectively is; 81, 5.5 and 16 while the 50% percentile,which is the median, for runtime_minutes, average_rating and number of votes respectively is; 91, 6.5 and 162 and the 75% percentile for runtime_minutes, average_rating and number of votes respectively is;104, 7.3 and 352.

For runtime and number of votes , the mean is greater than the median meaning that the data in those columns is positively skewed/skewed to the right and for the average rating, the median is greater than the mean implying that the data is negatively skewed/skewed to the left. Let's visualize this.

![histogram of runtime, rating and votes](https://github.com/Sharonkimani/dsc-phase-1-project-v2-4/blob/master/hist%20of%20runtime%2C%20rating%20and%20votes.PNG)

The top 5 rated movies are;The Dark Knight: The Ballad of the N Word,The Paternal Bond: Barbary Macaques, I Was Born Yesterday! , Ellis Island and Requiem voor een Boom .The top rated movies are of genre; comedy,drama,documentary and history.The poorly rated movies were;Onverwacht, Ya vas vsyekh ub'yu, Delusion of Persecution, Pure Hearts: Into Chinese Showbiz and Ryûsei which were of genre; documentary, drama,horror,thriller,comedy and family .

The correlation between runtime minutes and the average rating is -0.007076, which shows that they have a negative relationship(but not a strong negative relationship), that is, increase in runtime minutes lowers the rating.The correlation between runtime and number of votes is 0.012428, which shows that they have a positive relationship,though not a strong relationship since the correlation is close to 0, implying that increase in runtime minutes leads to increase in the number of votes.The correlation between average rating and number of votes is 0.048756 which shows that they have a positive relationship implying that increase in number of votes increases the average rating.

Let's visualize the relationship between the runtime and average rating.

![relationship between runtime and rating](https://github.com/Sharonkimani/dsc-phase-1-project-v2-4/blob/master/runtime%20vs%20rating.PNG)


From the above scatter plot, we can tell that runtime minutes aand average rating have low negative to no correlation but it still implies that increase in runtime minutes may lead to decrease in the average rating hence the company should put this into consideration.

Let's visualize the relationship between the runtime and number of votes.

![relationship between runtime and votes]("""C:\Users\Admin\Desktop\project1\dsc-phase-1-project-v2-4\runtime vs numvotes.PNG""")

## Conclusion
### Recommendations
* The company should consider creating more movies of genre ; comedy, drama, documentary and history since the top rated movies were of these genres.
* The company should consider creating few movies of genre; horror, thriller and family  since  the least rated movies were of these genres.
* The company should make movies that are not too long nor too short since increase in runtime minutes increases number of votes but also decreases the average rating.

