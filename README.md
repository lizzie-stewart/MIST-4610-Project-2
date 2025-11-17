# MIST-4610-Project-2

Group Members:
Group 3: Grey Mendenhall, Lizzie Stewart, Karwan Gardi
Links: https://github.com/lizzie-stewart/MIST-4610-Project-2



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

# Dashboard
<img width="718" height="335" alt="Screenshot 2025-11-17 at 6 40 02 PM" src="https://github.com/user-attachments/assets/f49ecbc2-971a-42a1-af16-08674803bebb" />

<img width="433" height="382" alt="Screenshot 2025-11-17 at 6 39 52 PM" src="https://github.com/user-attachments/assets/85e3f91d-b877-447d-8bbe-26149560f181" />


<img width="390" height="101" alt="Screenshot 2025-11-17 at 6 39 32 PM" src="https://github.com/user-attachments/assets/003e7887-4ee1-480f-a43e-1f46c415ec6e" />

<img width="388" height="81" alt="Screenshot 2025-11-17 at 6 39 43 PM" src="https://github.com/user-attachments/assets/45dad48e-e14c-4352-aa01-c41c65ce9068" />

<img width="390" height="101" alt="Screenshot 2025-11-17 at 6 39 32 PM" src="https://github.com/user-attachments/assets/ddcecd10-42e9-4f79-b549-30a2f358a9c7" />

<img width="384" height="86" alt="Screenshot 2025-11-17 at 6 39 19 PM" src="https://github.com/user-attachments/assets/978b9165-aa37-4447-852b-89234fe18018" />
