# MIST-4610-Project-2

# MIST Project Two
Group Members:
Group 3: Grey Mendenhall, Lizzie Stewart, Karwan Gardi
Links:


# Data Set Description
Our dataset was a list of songs from spotify and different metrics from each song. We got the dataset from Kaggle. It is around 600 thousand rows and 20 columns. The different factors from the dataset include numerical values for danceability, energy, tempo, and other factors that measure the enjoyment of a song. It is helpful to have these metrics to compare musical features and popularity of the song.

# Questions Generated
Question 1: What musical characteristics separate highly popular tracks from less popular ones? 

This is relevant because it can help us recognize what song features most people are attracted to and why. It highlights what song attributes listeners tend to gravitate toward and whether popular songs follow a predictable musical pattern.

Question 2: Which genres consistently produce higher-performing tracks?

This question is important because it shows which genres people tend to prefer. Popular genres often get more attention on streaming platforms and influence what music becomes popular in our culture. Our dataset includes popularity scores and genre labels, so we can compare genres to see which ones perform best.

# Data Manipulation


We organized the popularity groups into three simple filters:
Popular: popularity ≥ 70
Medium: popularity 30–69
Unpopular: popularity < 30

We also used average calculations for each category.

# SQL Code used
Question 1:
SELECT 
    'Popular (70–100)' AS popularity_group,
    AVG(danceability) AS avg_danceability
FROM SPOTIFY_DATABASE.PUBLIC.SPOTIFY_DATA
WHERE popularity >= 70

UNION ALL

SELECT 
    'Medium (30–69)' AS popularity_group,
    AVG(danceability) AS avg_danceability
FROM SPOTIFY_DATABASE.PUBLIC.SPOTIFY_DATA
WHERE popularity BETWEEN 30 AND 69

UNION ALL

SELECT 
    'Unpopular (0–29)' AS popularity_group,
    AVG(danceability) AS avg_danceability
FROM SPOTIFY_DATABASE.PUBLIC.SPOTIFY_DATA
WHERE popularity < 30
ORDER BY popularity_group;





Question 2:
SELECT 
    genre,
    COUNT(*) AS num_songs,
    AVG(popularity) AS avg_popularity
FROM SPOTIFY_DATABASE.PUBLIC.SPOTIFY_DATA
GROUP BY genre
HAVING COUNT(*) > 30
ORDER BY avg_popularity DESC;





