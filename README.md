# Netflix Description Classification and Sentiment Analysis

Group Members: Divya Nataraj | Judy Rhee | Amber Xia | Karen Wang | Xinyi Yang


Netflix is one of the largest streaming services, with a customer base of over 220 million subscribers. Globally, Netflix streams over 17,000 titles in a variety of languages, genres, and maturity ratings. We plan to conduct text analysis on the names of cast and crew for the titles to classify names based on gender and see how the gender of cast and producers may affect a title’s popularity. Additionally, we plan to conduct sentiment analysis on the content offered by Netflix, which will allow us to gain a better understanding of the range of shows and movies that users can watch, as well as see how the popularity or ratings of titles may differ based on the general sentiment. 

### Research Question 1
> What is the gender breakdown of cast and crew members for English-titled Netflix shows and movies? How does this vary across genres and influence popularity ratings?

We are interested in incorporating machine learning and natural language processing (NLP) for research question 1. We perform classification by using NLTK to conduct text analysis of the producers and cast members’ names in the chosen genres, then classifying the names by gender. The following steps outline how we investigated this research question:
1. Find 5-6 genres (‘genres’ in titles.csv) with the most movies and shows listed. Pull title IDs (‘title’ in titles.csv) of English productions under each of these genres (‘production_country’ == ‘US’ or ‘GB’ or ‘CA’).
2. Get names of actors or directors (‘name’ and ‘role’ in credits.csv) with corresponding title IDs from step 1.
3. Build a classifier to find features that would help us determine if those names are more likely to be male or female. With the two .txt files of the most common English male and female first names, we develop a test set to train a model.
4. Use the model on the names we obtained from the Kaggle dataset to classify names as male or female.
5. Determine proportion of names of each gender within each genre. For example, in the action genre, are movies more likely to be dominated by male-identified names? Do TV shows in the romance genre see more female-identified names?
6. Compare popularity of titles with more male-identified names v.s. more female-identified names (using ‘tmdb_popularity’ in titles.csv).

### Research Question 2
> How do levels of positive and negative sentiment of Netflix titles differ between titles that were released before versus after the start of the COVID-19 pandemic?

We wondered if there were any significant changes in sentiments of show/movie descriptions released on Netflix after 2020, which was the year when COVID became widespread and disrupted every industry around the world. We conducted positive/negative sentiment analysis of show descriptions (‘description’ in titles.csv) for shows released before versus after 2020, and see if and how they vary. The general breakdown of steps for research question 2 is as follows:
1. Separate movies and shows from titles.csv into two groups based on ‘release_year’: ‘release_year’ <= 2020 and ‘release_year’ > 2020.
2. Clean data. Descriptions will need to be cleaned by tokenization using the NLTK word tokenization function, and words that are not meaningful to our research will need to be removed. After using a stop word dictionary to remove stop words like ‘the’, ‘and’, ‘a’, we can group words by their dictionary form (lemmatization).
3. Using NLTK’s Vader sentiment analysis, generate a score to determine if each description is positive, negative, or neutral.
4. Use Vader library to get a compound score telling us how much of each sentiment is portrayed in the descriptions.
5. Compare sentiment scores of descriptions in the two groups.

