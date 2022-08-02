# Project-Group-4
## Group Participants
* Jenny Bedwell
* Joshua Cressaty
* Lennox Nguyen
* Hee Oh
* Austin Skorb
* William Tecchio
* Aimee Vu

## Purpose
The main purpose of this project is to present the movie streaming services data to a new company who wants to enter the movie streaming service industry. 

By utilizing different data sources, Jupyter notebook, and Python libraries like Pandas, Matplotlib, and Numpy, we analyze movies over the past 10 years to show:

* Which streaming service has the highest rated content and most content for different age groups
* How movie ratings and customer interactions have changed
* Which services have the best content based on genres
* Which countries produce the most films and revenue

Our dataset is more focused on movies that can be streamed on Netflix, Prime Video, Hulu, and Disney+.

## Data Source:
* "Movies on Netflix, Prime Video, Hulu and Disney+" Dataset on <a href="https://www.kaggle.com/datasets/ruchi798/movies-on-netflix-prime-video-hulu-and-disney">Kaggle</a>
* <a href="https://www.themoviedb.org/documentation/api">TheMovieDatabase API</a>

### Data Limitations
While analyzing the final data output, we've identified some discrepancies between the data that we used for each question. Some of the data fields contained no data from TMDB API, so that movie was dropped for that particular question. 

In addition, this API is maintained by fans of a limited population. Our analysis and conclusion will be based on the Kaggle dataset and what data we can pull from the API.

### Data Cleanse
We started with the dataset found on Kaggle that contained a list of movies streamed on Netflix, Prime Video, Hulu, and Disney+. After identifying the questions that we were curious about, we used Excel to filter for movies produced in the past 10 years and removed initial null values from the initial columns provided by Kaggle.

Originally, we pulled a comprehensive data dump from TMDB that contained a list of all movies on the site along with their Movie IDs. From here, we used VLOOKUP in Excel to identify the TMDB ID for the movies on the Kaggle dataset. We later identified movies with the same name. Because the JSON export did not contain movie year, we had to use a different method. 

To find the correct movie ID, we had use the query API call to search for the movie by title and year to pinpoint the movie we were looking for. A code outline can be found below and the full code can be found <a href="Project-Group-4/Question 2/Question 2.ipynb">here</a>.

```
for index, movie in cleanBaseData.iterrows():
    # Make API call using Movie Title and Year to query
    try:
        for results in queryRequest['results']:
            if results['title'] == currentMovie:
                # Check if current result in query matches Kaggle Title, save movie ID
            else:
                # Skips to the next result in query
    except:
        # If search has no results, skip to next movie in Kaggle list
    
    if currentMovieID == '':
        # If no movie ID found, skip to next movie in Kaggle list
    else:
        # Continue with extracting data
        try:
            # Save data from 
        except:
            # Continue to next movie in Kaggle list if data cannot be found
```
<b>Additional Issues</b>
* Identical movie names
* Different movie name in "title" and "original title"
* Movie name with multiple search results
* Special characters with no search results

## Analysis
### Question 1: Which streaming service has the highest rated content and most content for different age groups?
Jenny and Hee explore age rating and star rating across different streaming services using the movie list from Kaggle. The <a href="Question 1 Over'rated'/age_rating.ipynb">code</a> aims to make conclusions such as if Netflix has more content for children over Disney+ or if people are more likely to view a 5 Star movie over a 2 Star movie. 

The overall idea is to show:
* The distribution of movies across the different streaming services
* Which streaming services that have more content of a specific age group
* The distribution of movies across the star rating (1-5)
* The distribution of movie star ratings across the different streaming services

Given our dataset, we've generated the following graphs:

---------------------------------------------------------

<b>Total Movies per Streaming Services</b>

<img src="Question 1 Over'rated'/data/movies_per_service.png" width="500">

---------------------------------------------------------

<b>Number of Movies per Age Rating</b>

<img src="Question 1 Over'rated'/data/age_per_services.png" width="500">

---------------------------------------------------------

<b>Total Movies per Star Rating based by Rotten Tomatoes</b>

<img src="Question 1 Over'rated'/data/movies_per_star.png" width="500">

---------------------------------------------------------

<b>Movie Counts based on Star Rating per Streaming Service</b>

<img src="Question 1 Over'rated'/data/star_moviecount.png" width="500">


### Question 2: How have movies improved(ratings) and have customer interactions increased?
Austin and Aimee explore how movie ratings have changed and whether or not more people have interacted with a movie over a 10-year period. The <a href="Project-Group-4/Question 2/Question 2(with Graphs).ipynb">code</a> generates charts to show how the movie ratings and interactions have changed over the 10 years. Our goal was also to see how COVID may have affected these interations.

The overall idea is to show:
* How average votes for movies has changed over the years
* How the quantity of votes has changed over the years

Given our dataset, we've generated the following graphs:

---------------------------------------------------------

<b>Yearly Average of Mean Votes</b>

<img src="Question 2/Question2.1.PNG" width="500">

---------------------------------------------------------

<b>Average Vote Count by Year</b>

<img src="Question 2/Question 2,2.PNG" width="500">

### Question 3: Which services have the best content based on genres?

<a href="">code</a>

---------------------------------------------------------

<b>Quantity of Movie by Genre</b>

<img src="Question 3/Images/GenreBarPlot.png" width="500">

---------------------------------------------------------

<b></b>

<img src="" width="500">


### Question 4: Which countries produce the most films and revenue?

<a href="">code</a>

---------------------------------------------------------

<b>Average Review of Movies by Language</b>

<img src="Question 4/Images/AverageReview.png" width="500">

---------------------------------------------------------

<b></b>

<img src="Question 4/Images/BoxPlot.png" width="500">

---------------------------------------------------------

<b>Sum of Review Count by Movie Language</b>

<img src="Question 4/Images/ReviewCount.png" width="500">

## Conclusions