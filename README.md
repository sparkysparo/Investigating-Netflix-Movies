# NETFLIX DATA SET #
## introduction

Netflix, established in 1997 as a DVD rental service, has evolved into one of the most prominent entertainment and media companies globally. With its vast collection of movies and series available on the platform, Netflix has become a significant player in the entertainment industry.
The objective of this exploration is to analyze Netflix data to investigate the claim that the average duration of movies on the platform has been declining. This task provides an opportunity to employ exploratory data analysis (EDA) techniques to gain insights into trends within the entertainment industry.
Initially, my friend has conducted preliminary research using a CSV file containing Netflix data. They suspect that movie lengths may be decreasing over time. In response, i will delve into the Netflix dataset to verify this claim and explore potential contributing factors if such a trend exists.

Through thorough analysis of the Netflix data, i aim to determine:

1. Whether there is evidence supporting the claim of declining movie durations.
2. Factors contributing to any observed trends, such as changes in audience preferences, production strategies, or industry dynamics.

 
By leveraging Python programming and EDA techniques, i will uncover insights that shed light on the evolving landscape of movie lengths on Netflix and offer valuable perspectives for understanding shifts within the entertainment industry.

### Importing pandas and matplotlib
import pandas as pd

import matplotlib.pyplot as plt

### Steps!

#### Step 1: Load the CSV file
---
netflix_df = pd.read_csv("netflix_data.csv")

#### Step 2: Filter out TV shows
---
netflix_subset = netflix_df[netflix_df['type'] == 'Movie']

#### Step 3: Keep only relevant columns
---
netflix_movies = netflix_subset[['title', 'country', 'genre', 'release_year', 'duration']]

#### Step 4: Filter movies shorter than 60 minutes
---
short_movies = netflix_movies[netflix_movies['duration'] < 60]

#### Step 5: Assign colors to genre groups
---
colors = []
for index, row in netflix_movies.iterrows():
    if 'Children' in row['genre']:
        colors.append('blue')
    elif 'Documentaries' in row['genre']:
        colors.append('green')
    elif 'Stand-Up' in row['genre']:
        colors.append('red')
    else:
        colors.append('gray')

#### Step 6: Create scatter plot
---
fig, ax = plt.subplots()
ax.scatter(netflix_movies['release_year'], netflix_movies['duration'], c=colors)
ax.set_xlabel('Release year')
ax.set_ylabel('Duration (min)')
ax.set_title('Movie Duration by Year of Release')
plt.show()


#### Step 7: Analyze the plot and answer the question
---
answer = "no"  # Based on the scatter plot, there's no clear trend indicating that movies are getting shorter.


## Conclusion
---

Based on the analysis conducted on the Netflix data, the conclusion drawn is that there is no clear trend indicating that movies are getting shorter. The scatter plot visualization, which depicts the relationship between movie release year and duration, does not reveal a discernible pattern or trend over time.

While there may be fluctuations in movie durations across different years, there is no consistent downward trend suggesting a significant decline in the average length of movies on the platform. This finding contradicts the initial hypothesis that movie lengths have been decreasing over time.

Several factors may contribute to the lack of a clear trend in movie durations. These factors could include variations in film genres, audience preferences, production strategies, and industry dynamics, among others. Additionally, the dataset may have limitations or biases that could influence the analysis and interpretation of results.

Overall, the analysis suggests that there is no compelling evidence to support the notion that movies on Netflix are getting shorter. Further research and analysis may be warranted to explore other aspects of movie trends and to understand the dynamics of the entertainment industry more comprehensively.
