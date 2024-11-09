# SPOTIFY 2023 EXPLORATORY DATA ANALYSIS

# General Guidelines:


1. Begin by familiarizing yourself with the structure of the dataset. Check for missing values and data types, and perform an initial exploration to understand the different features available.
   
2. Provide summary statistics to give an overview of key metrics such as the number of streams, release dates, and musical attributes (e.g., BPM, danceability).

3. Use appropriate visualizations (e.g., bar charts, histograms, scatter plots) to uncover trends and patterns in the data. Ensure that your plots are well-labeled and easy to interpret.
   
4. Investigate correlations between different variables and provide insights based on your findings. Explore relationships between streams and other musical characteristics like tempo, energy, or playlists.
   
5. Based on your analysis, offer any insights or recommendations regarding the tracks, artists, or musical trends that could be useful for understanding what makes a track popular.

# Preparation for the Analysis:

The creator downloaded the csv file named 'spotify-2023.csv' in preparation for the EDA.

# Procedures:

## Importing all the Libraries Necessary for the Analysis


```python
# Start of Code
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

## Loading the '.csv' File in the Notebook


```python
# Loading of the csv file
spotify  = pd.read_csv('spotify-2023.csv', encoding='cp1252')
spotify
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>track_name</th>
      <th>artist(s)_name</th>
      <th>artist_count</th>
      <th>released_year</th>
      <th>released_month</th>
      <th>released_day</th>
      <th>in_spotify_playlists</th>
      <th>in_spotify_charts</th>
      <th>streams</th>
      <th>in_apple_playlists</th>
      <th>...</th>
      <th>bpm</th>
      <th>key</th>
      <th>mode</th>
      <th>danceability_%</th>
      <th>valence_%</th>
      <th>energy_%</th>
      <th>acousticness_%</th>
      <th>instrumentalness_%</th>
      <th>liveness_%</th>
      <th>speechiness_%</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Seven (feat. Latto) (Explicit Ver.)</td>
      <td>Latto, Jung Kook</td>
      <td>2</td>
      <td>2023</td>
      <td>7</td>
      <td>14</td>
      <td>553</td>
      <td>147</td>
      <td>141381703</td>
      <td>43</td>
      <td>...</td>
      <td>125</td>
      <td>B</td>
      <td>Major</td>
      <td>80</td>
      <td>89</td>
      <td>83</td>
      <td>31</td>
      <td>0</td>
      <td>8</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>LALA</td>
      <td>Myke Towers</td>
      <td>1</td>
      <td>2023</td>
      <td>3</td>
      <td>23</td>
      <td>1474</td>
      <td>48</td>
      <td>133716286</td>
      <td>48</td>
      <td>...</td>
      <td>92</td>
      <td>C#</td>
      <td>Major</td>
      <td>71</td>
      <td>61</td>
      <td>74</td>
      <td>7</td>
      <td>0</td>
      <td>10</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>vampire</td>
      <td>Olivia Rodrigo</td>
      <td>1</td>
      <td>2023</td>
      <td>6</td>
      <td>30</td>
      <td>1397</td>
      <td>113</td>
      <td>140003974</td>
      <td>94</td>
      <td>...</td>
      <td>138</td>
      <td>F</td>
      <td>Major</td>
      <td>51</td>
      <td>32</td>
      <td>53</td>
      <td>17</td>
      <td>0</td>
      <td>31</td>
      <td>6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Cruel Summer</td>
      <td>Taylor Swift</td>
      <td>1</td>
      <td>2019</td>
      <td>8</td>
      <td>23</td>
      <td>7858</td>
      <td>100</td>
      <td>800840817</td>
      <td>116</td>
      <td>...</td>
      <td>170</td>
      <td>A</td>
      <td>Major</td>
      <td>55</td>
      <td>58</td>
      <td>72</td>
      <td>11</td>
      <td>0</td>
      <td>11</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>WHERE SHE GOES</td>
      <td>Bad Bunny</td>
      <td>1</td>
      <td>2023</td>
      <td>5</td>
      <td>18</td>
      <td>3133</td>
      <td>50</td>
      <td>303236322</td>
      <td>84</td>
      <td>...</td>
      <td>144</td>
      <td>A</td>
      <td>Minor</td>
      <td>65</td>
      <td>23</td>
      <td>80</td>
      <td>14</td>
      <td>63</td>
      <td>11</td>
      <td>6</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>948</th>
      <td>My Mind &amp; Me</td>
      <td>Selena Gomez</td>
      <td>1</td>
      <td>2022</td>
      <td>11</td>
      <td>3</td>
      <td>953</td>
      <td>0</td>
      <td>91473363</td>
      <td>61</td>
      <td>...</td>
      <td>144</td>
      <td>A</td>
      <td>Major</td>
      <td>60</td>
      <td>24</td>
      <td>39</td>
      <td>57</td>
      <td>0</td>
      <td>8</td>
      <td>3</td>
    </tr>
    <tr>
      <th>949</th>
      <td>Bigger Than The Whole Sky</td>
      <td>Taylor Swift</td>
      <td>1</td>
      <td>2022</td>
      <td>10</td>
      <td>21</td>
      <td>1180</td>
      <td>0</td>
      <td>121871870</td>
      <td>4</td>
      <td>...</td>
      <td>166</td>
      <td>F#</td>
      <td>Major</td>
      <td>42</td>
      <td>7</td>
      <td>24</td>
      <td>83</td>
      <td>1</td>
      <td>12</td>
      <td>6</td>
    </tr>
    <tr>
      <th>950</th>
      <td>A Veces (feat. Feid)</td>
      <td>Feid, Paulo Londra</td>
      <td>2</td>
      <td>2022</td>
      <td>11</td>
      <td>3</td>
      <td>573</td>
      <td>0</td>
      <td>73513683</td>
      <td>2</td>
      <td>...</td>
      <td>92</td>
      <td>C#</td>
      <td>Major</td>
      <td>80</td>
      <td>81</td>
      <td>67</td>
      <td>4</td>
      <td>0</td>
      <td>8</td>
      <td>6</td>
    </tr>
    <tr>
      <th>951</th>
      <td>En La De Ella</td>
      <td>Feid, Sech, Jhayco</td>
      <td>3</td>
      <td>2022</td>
      <td>10</td>
      <td>20</td>
      <td>1320</td>
      <td>0</td>
      <td>133895612</td>
      <td>29</td>
      <td>...</td>
      <td>97</td>
      <td>C#</td>
      <td>Major</td>
      <td>82</td>
      <td>67</td>
      <td>77</td>
      <td>8</td>
      <td>0</td>
      <td>12</td>
      <td>5</td>
    </tr>
    <tr>
      <th>952</th>
      <td>Alone</td>
      <td>Burna Boy</td>
      <td>1</td>
      <td>2022</td>
      <td>11</td>
      <td>4</td>
      <td>782</td>
      <td>2</td>
      <td>96007391</td>
      <td>27</td>
      <td>...</td>
      <td>90</td>
      <td>E</td>
      <td>Minor</td>
      <td>61</td>
      <td>32</td>
      <td>67</td>
      <td>15</td>
      <td>0</td>
      <td>11</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
<p>953 rows × 24 columns</p>
</div>



## GUIDE QUESTIONS:

## • Overview of Dataset

### 1. How many rows and columns does the dataset contain?


```python
# Finding the number of Rows and Columns using the len function

rows = len(spotify) # not adding the '.axes' automatically measure its number of rows
columns = len(spotify.axes[1]) # setting the axes to 1 will measure its number of columns

# An alternative and simplified version would be '.shape'

print('Data set Shape:',spotify.shape,'\n\nRows =', rows, '\nColumns =', columns)
```

    Data set Shape: (953, 24) 
    
    Rows = 953 
    Columns = 24
    

-Using the 'len' function, we can properly quantify the amount of rows and columns in the dataset. In conclusion, the number of Rows is 953 and the Columns is 24. The '.shape' function can be used to easily determine its rows and columns, but for formatting reason, the creator also utilized the 'len' function.

### 2. What are the data types of each column? Are there any missing values?


```python
# Finding the datatypes of each column using '.dtypes'

data_type = spotify.dtypes
data_type
```




    track_name              object
    artist(s)_name          object
    artist_count             int64
    released_year            int64
    released_month           int64
    released_day             int64
    in_spotify_playlists     int64
    in_spotify_charts        int64
    streams                 object
    in_apple_playlists       int64
    in_apple_charts          int64
    in_deezer_playlists     object
    in_deezer_charts         int64
    in_shazam_charts        object
    bpm                      int64
    key                     object
    mode                    object
    danceability_%           int64
    valence_%                int64
    energy_%                 int64
    acousticness_%           int64
    instrumentalness_%       int64
    liveness_%               int64
    speechiness_%            int64
    dtype: object



-By utilizing the '.dtype' function from pandas, we can easily find the data types that was used in each column. By analyzing the result, we can see that most of the columns that relies on numerical values has a data type of 'int64' while some of the columns that relies on alphanumeric values has a data type of 'object'. However, there are some columns that are supposed to have a data type of integer that has a dtype of 'object' ('streams', 'in_deezer_playlists', and 'in_shazam_charts').


```python
# Checking for the missing values in the data set

Number_of_Null = spotify.isnull().sum()

print(Number_of_Null,'\n\nTotal number of Missing Values:', spotify.isnull().sum().sum())
```

    track_name               0
    artist(s)_name           0
    artist_count             0
    released_year            0
    released_month           0
    released_day             0
    in_spotify_playlists     0
    in_spotify_charts        0
    streams                  0
    in_apple_playlists       0
    in_apple_charts          0
    in_deezer_playlists      0
    in_deezer_charts         0
    in_shazam_charts        50
    bpm                      0
    key                     95
    mode                     0
    danceability_%           0
    valence_%                0
    energy_%                 0
    acousticness_%           0
    instrumentalness_%       0
    liveness_%               0
    speechiness_%            0
    dtype: int64 
    
    Total number of Missing Values: 145
    

-By using the '.isnull' function, it will check each data to determine if ther are Null or not. And adding a '.sum()' will sum up the total number of null values in each column. Additionally, by adding another '.sum()' will add all of the number of Null values in every column.

-By looking at the data above, we can see the data has a lot of missing values, specifically in the 'in_shazam_charts' and 'keys' columns (50 and 95, respectively). By summing all of the missing value, we can identify the total number of Missing Values, which is 145.

### Fixing the Data Set

#### Changing the Missing Numerical Values to '0' and the Missing Keys to 'C'


```python
# Filling the missing values using '.fillna()'

spotify['in_shazam_charts'] = spotify['in_shazam_charts'].fillna(0)
spotify['key'] = spotify['key'].fillna('C')

# Verifying if the missing values are properly fixed
print(spotify.isnull().sum())
```

    track_name              0
    artist(s)_name          0
    artist_count            0
    released_year           0
    released_month          0
    released_day            0
    in_spotify_playlists    0
    in_spotify_charts       0
    streams                 0
    in_apple_playlists      0
    in_apple_charts         0
    in_deezer_playlists     0
    in_deezer_charts        0
    in_shazam_charts        0
    bpm                     0
    key                     0
    mode                    0
    danceability_%          0
    valence_%               0
    energy_%                0
    acousticness_%          0
    instrumentalness_%      0
    liveness_%              0
    speechiness_%           0
    dtype: int64
    

-Using the '.fillna()', we can easily replace all the missing values with its appropriate value. In the 'in_spotify_charts', all of the blank values are replaced by 0 fix the NaN values. On the 'key' section, we can apply also apply both Musical and simple logic to determine that the key of C is the missing key in the given data, which is a very unlikely scenario, knowing that the key of C is the most common and standard scale and basis for music theory. By replacing the missing values and verifying the songs through key analyzing, the user safely replaced the missing key to 'C'.

#### Changing the data types of the other Columns


```python
# Changing the data types of other columns

# Removing the non-numerical value in the 
spotify = spotify.replace(',','', regex = True)

# Removing the error string 'BPM110KeyAModeMajorDanceability53Valence75Energy69Acousticness7Instrumentalness0Liveness17Speechiness3'
spotify = spotify.replace('BPM110KeyAModeMajorDanceability53Valence75Energy69Acousticness7Instrumentalness0Liveness17Speechiness3','0', regex = True)

# Using pd.to_numeric to convert the data type into the most appropriate numerical data type (e.g., float, int, etc.)
spotify["streams"] = pd.to_numeric(spotify["streams"])#--------------------------streams
spotify["in_deezer_playlists"] = pd.to_numeric(spotify["in_deezer_playlists"])#--in_deezer_playlists
spotify["in_shazam_charts"] = pd.to_numeric(spotify["in_shazam_charts"])#--------in_shazam_charts

# Verifying if the data types are properly converted
print(spotify.dtypes)
```

    track_name              object
    artist(s)_name          object
    artist_count             int64
    released_year            int64
    released_month           int64
    released_day             int64
    in_spotify_playlists     int64
    in_spotify_charts        int64
    streams                  int64
    in_apple_playlists       int64
    in_apple_charts          int64
    in_deezer_playlists      int64
    in_deezer_charts         int64
    in_shazam_charts         int64
    bpm                      int64
    key                     object
    mode                    object
    danceability_%           int64
    valence_%                int64
    energy_%                 int64
    acousticness_%           int64
    instrumentalness_%       int64
    liveness_%               int64
    speechiness_%            int64
    dtype: object
    

-In preparation of replacing the data types, the creator removed the unnecessary commas in the data to avoid errors when converting. During the process, the creator noticed an error in the data, specifically on row 576 in the 'streams' column, so the value was then simply replaced to 0 to prevent further errors. By replacing the said columns, everything is now eligible for data representation for further analysis.

## • Basic Descriptive Statistics

### 1. What are the mean, median, and standard deviation of the streams column?


```python
# Calculate mean, median, and mode
mean = spotify['streams'].mean()
median = spotify['streams'].median()
mode = spotify['streams'].mode()[0]
stdev = spotify['streams'].std()
print('Mean   =',mean,'\nMedian =',median,'\nMode   =',mode,'\nStandard Deviation =',stdev)
```

-Using the functions '.mean', '.median', '.mode', and '.std', we can easily determine the measurement of central tendency and the deviation of the data inside the "streams" column. With these, we can conclude that the mean is 513597931.3137461, median is 290228626, mode is 156338624, and the standard deviation is 566803887.0588316.

### 2. What is the distribution of released_year and artist_count? Are there any noticeable trends or outliers?

#### Released Year


```python
# Number of songs included per year of release

song_per_year = spotify.groupby('released_year').size().reset_index(name='number of songs')
song_per_year.describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>released_year</th>
      <th>number of songs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>50.000000</td>
      <td>50.00000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>1990.440000</td>
      <td>19.06000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>24.133269</td>
      <td>62.71751</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1930.000000</td>
      <td>1.00000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1973.500000</td>
      <td>1.00000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1995.500000</td>
      <td>2.00000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2010.750000</td>
      <td>9.25000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2023.000000</td>
      <td>402.00000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Creating a Bar Graph for a Graphical Representation of the data above

plt.figure(figsize=(15, 5))
plt.title('Number of Songs Included per Year', fontsize=20)
plt.bar(song_per_year['released_year'], song_per_year['number of songs'])
plt.xlabel('Released Year', fontsize=14)
plt.ylabel('Disitribution of Songs', fontsize=14)

plt.show()
```


    
![output_35_0](https://github.com/user-attachments/assets/d092f64d-419e-46b3-8097-810d59af0519)



-Looking at the data above, we can easily find the outliers (minimum and maximum values). Looking at the bar graph, we can see that the distribution is very different, especially at the latter years. By analyzing the data thoroughly, the years around 2010 and below have a very similar distribution of small and very similar amounts as most of the songs in those years can be considered outdated, which lessens the relevancy from those years.

-With that, we can conclude that the Released Year plays a huge role in the distribution. Old songs may not be appealing to people, thus resulting in a low number of songs being included in those years. On the other hand, many of the songs in the list are released in the recent years, thus making the deviation of data large.

#### Artist Count


```python
# Number of songs included per number of artists

song_per_artist = spotify.groupby('artist_count').size().reset_index(name='number of songs')
song_per_artist.describe()
```


```python
# Creating a Bar Graph for a Graphical Representation of the data above

plt.figure(figsize=(15, 5))
plt.title('Number of Songs Included per Number of Artist', fontsize=20)
plt.bar(song_per_artist['artist_count'], song_per_artist['number of songs'])
plt.xlabel('Amount of Artists per Song', fontsize=14)
plt.ylabel('Number of Songs Included in the List', fontsize=14)

plt.show()
```

-Looking at the data above, we can easily find the outliers from the minimum and maximum values of the number of songs and the artist counts. Looking at the bar graph, we can see a negative trend between the amount of artists in a song and the number of songs included in the data set. By thoroughly analyzing the data, we can see that it is a common scenario that a song is released by one artist or one group. Mostly, songs with more than one artist is a product of collaborations, which is an uncommon scenario when comparing it to the probability of an artist to release a song without any collaboration.

In conclusion, the songs with only one artist got the highest number of songs included in the list. On the other hand, the songs with more than one artist has the lower amount of songs included in the list, but mostly due to the frequency of occurence of collaborations, especially with multiple artists.r.

##  • Top Performers

### 1. Which track has the highest number of streams? Display the top 5 most streamed tracks.


```python
# Displaying the Top 5 most streamed tracks

Top_Five_Tracks = spotify[['track_name', 'streams']]
Top_Five_Tracks = Top_Five_Tracks.sort_values('streams', ascending=False).head()
Top_Five_Tracks
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>track_name</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>55</th>
      <td>Blinding Lights</td>
      <td>3703895074</td>
    </tr>
    <tr>
      <th>179</th>
      <td>Shape of You</td>
      <td>3562543890</td>
    </tr>
    <tr>
      <th>86</th>
      <td>Someone You Loved</td>
      <td>2887241814</td>
    </tr>
    <tr>
      <th>620</th>
      <td>Dance Monkey</td>
      <td>2864791672</td>
    </tr>
    <tr>
      <th>41</th>
      <td>Sunflower - Spider-Man: Into the Spider-Verse</td>
      <td>2808096550</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Creating a bar graph

plt.figure(figsize=(20, 5))
plt.title('Top 5 Highest Streamed Songs', fontsize=20)
plt.bar(Top_Five_Tracks['track_name'], Top_Five_Tracks['streams'])
plt.xlabel('Track Name', fontsize=14)
plt.ylabel('Number of Streams', fontsize=14)

plt.show()
```


![output_44_0](https://github.com/user-attachments/assets/51cd9b1a-db2b-49d1-93c4-98a6ecc63b0d)



-Looking at the graph, the song 'Blinding Lights' appears to be the most streamed song in the year 2023. The rest are 'Shape of You', 'Someone You Loved', 'Dance Monkey', and 'Sunflower', respectively.

### 2. Who are the top 5 most frequent artists based on the number of tracks in the dataset?


```python
# Displaying the Top 5 Artist with the most amount of songs in the dataset

artist_freq = spotify['artist(s)_name'].value_counts().reset_index().head()
artist_freq
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>artist(s)_name</th>
      <th>count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Taylor Swift</td>
      <td>34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>The Weeknd</td>
      <td>22</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Bad Bunny</td>
      <td>19</td>
    </tr>
    <tr>
      <th>3</th>
      <td>SZA</td>
      <td>19</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Harry Styles</td>
      <td>17</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Creating a bar graph

plt.figure(figsize=(20, 5))
plt.title('Top 5 Artist with Most Songs in the List', fontsize=20)
plt.bar(artist_freq['artist(s)_name'], artist_freq['count'])
plt.xlabel('Artist/s Name', fontsize=14)
plt.ylabel('Number of Tracks', fontsize=14)

plt.show()
```


    
![output_48_0](https://github.com/user-attachments/assets/b4c27e38-bfa9-4903-8a6f-deca581ffaf0)
    


-Looking at the graph above, we can see large amount of tracks produced by the first artist, which is Taylor Swift. The second is the Weeknd, which also hase the number one most streamed song on the list. The rest of the list includes Bad Bunny, SZA, and Harry Styles, respectively.

## •  Temporal Trends

### 1. Analyze the trends in the number of tracks released over time. Plot the number of tracks released per year.


```python
# Looking at the raw set of the relation of the number of tracks released over time
song_per_year
```


```python
# Creating a Line Graph to show the trend of the number tracks through the years

plt.figure(figsize=(15, 5))
plt.title('Number of Tracks Released Over Time', fontsize=20)
sns.lineplot(x='released_year', y='number of songs', data=song_per_year, marker='o')
plt.xlabel('Released Year', fontsize=14)
plt.ylabel('Streams', fontsize=14)
plt.grid(True)

plt.show()
```


![output_53_0](https://github.com/user-attachments/assets/fe6d2403-8828-45a6-9262-2716cb7f1046)

    


Looking at the line graph, we can see a similarity with the distribution per released year from the previous graph as it shows a positive trend until it reaches the year 2022, but then the value declines the year after (2023). By analyzing the data thoroughly, the sudden decline in the number of songs included in 2023 was due to its recency (the closer the release date to the date the table was created, the less time it has to be streamed by the people).

-With that, we can conclude that the Released Year plays a huge role in a song's relevancy. Old songs may not be appealing to people, thus resulting in a low number of songs being included in those years. On the other hand, recent songs may be relevant, but due to their recency, it doesn't have enough time to count the maximum potential streams (unlike the songs released in 2022), making their values less than the previous year.

### 2. Does the number of tracks released per month follow any noticeable patterns? Which month sees the most releases?


```python
# Number of tracks released per month

song_per_month = spotify.groupby('released_month').size().reset_index(name='number of songs')
song_per_month
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>released_month</th>
      <th>number of songs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>134</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>86</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>66</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>128</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>86</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>62</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>46</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>56</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>73</td>
    </tr>
    <tr>
      <th>10</th>
      <td>11</td>
      <td>80</td>
    </tr>
    <tr>
      <th>11</th>
      <td>12</td>
      <td>75</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Creating a Line Graph to show the trend of the number tracks through each month

plt.figure(figsize=(15, 5))
plt.title('Number of Songs per Month', fontsize=20)
plt.bar(song_per_month['released_month'], song_per_month['number of songs'])
plt.xlabel('Months', fontsize=14)
plt.ylabel('Number of Songs', fontsize=14)

plt.show()
```


    
![output_57_0](https://github.com/user-attachments/assets/dccba8f1-5314-4c23-a9a0-84b6f9ff365c)
  


-Looking at the bar graph above, we can see an increased amount of songs in the month of January and May. By thoroughly analyzing the data above, we can infer that both months enters a new season (e.g., January is the start of the Spring season, May is the peak summer season), which plays a role in setting a specific mood or emotions in the songs included in the list.

-In conclusion, I would say that there's a trend between the song's released month and its popularity as they tend to set a mood or emotion that would encapsulates the audience's interest, thus making the song more relevant.

## • Genre and Music Characteristics

### 1. Examine the correlation between streams and musical attributes like bpm, danceability_%, and energy_%. Which attributes seem to influence streams the most?

#### BPM-Streams Correlation


```python
# Creating a scatter plot to examine any correlation

plt.figure(figsize=(15, 5))
plt.title('Relation between BPM and Streams', fontsize=20)
sns.scatterplot(x='bpm', y='streams', data=spotify)
plt.xlabel('Beats per Minute', fontsize=14)
plt.ylabel('Streams', fontsize=14)
plt.show()
```


    
![output_62_0](https://github.com/user-attachments/assets/73fa9254-bfc7-4d04-94aa-2388d126aeee)


-Looking at the plots above, there's a slightly noticeable trend or increase in streams to the songs with a BPM at around 90 to 150. However, there are still alot of other songs that have several amount of streams in every bpm (especially around 170 bpm). In conclusion, BPM may have a small effect or relation with the amount of streams but will not directly affect the amount of streams of a song.

#### Danceability-Streams Correlation


```python
# Creating a scatter plot to examine any correlation

plt.figure(figsize=(15, 5))
plt.title('Relation between Danceability% and Streams', fontsize=20)
sns.scatterplot(x='danceability_%', y='streams', data=spotify)
plt.xlabel('Danceability %', fontsize=14)
plt.ylabel('Streams', fontsize=14)
plt.show()
```


    
![output_65_0](https://github.com/user-attachments/assets/989a596a-cc69-4f52-92c7-ceb71338208f)
   


-By observing the graph above, we can see that there's a sudden increase of stream at around 50% danceability and above. There are still some songs that are below the 50% danceability with a high amount of streams, but most of the higher once belong in the 50% and above. In conclusion, there is a correlation between Danceability% and Streams. It doesn't necessarily need to be on the higher percentage of danceability, but having enough danceability factor affects the number of streams positively.

#### Energy-Streams Correlation


```python
# Creating a scatter plot to examine any correlation

plt.figure(figsize=(15, 5))
plt.title('Relation between Energy% and Streams', fontsize=20)
sns.scatterplot(x='energy_%', y='streams', data=spotify)
plt.xlabel('Energy %', fontsize=14)
plt.ylabel('Streams', fontsize=14)
plt.show()
```


    
![output_68_0](https://github.com/user-attachments/assets/7cc4b5ea-385f-4cfb-afcb-8384c9fef1fa)
 


-Looking at the graph above, we can immediately see a positive trend, especially at the starting part of the x-axis, but then the number of streams slowly decreases at the higher Energy% (approximately around 90%). With that trend, we can conclude that having a proper amount of Energy% to a song can positively impact the number of streams it has.

### 2. Is there a correlation between danceability_% and energy_%? How about valence_% and acousticness_%?

#### Danceability-Energy Correlation


```python
# Creating a scatter plot to examine any correlation

plt.figure(figsize=(15, 5))
plt.title('Relation between Danceability% and Energy%', fontsize=20)
sns.scatterplot(x='energy_%', y='danceability_%', data=spotify)
plt.xlabel('Energy %', fontsize=14)
plt.ylabel('Danceability %', fontsize=14)
plt.show()
```


    
![output_72_0](https://github.com/user-attachments/assets/157c99fe-119e-43fc-bd07-f306180f3d0f)
   


-By examining the scatterplot above, we can clearly see a positive correlation between the danceability and energy. Commonly, both concepts/factors are related to each other as they both theories are inline with each concept's principle. In conclusion, the danceability% is proportionaly to energy% in a song.

#### Valence-Acousticness Correlation


```python
plt.figure(figsize=(15, 5))
plt.title('Relation between Valence% and Acousticness%', fontsize=20)
sns.scatterplot(x='valence_%', y='acousticness_%', data=spotify)
plt.xlabel('Valence %', fontsize=14)
plt.ylabel('Acousticness %', fontsize=14)
plt.show()
```


    
![output_75_0](https://github.com/user-attachments/assets/a86c0834-ffea-4a96-86d5-8ae95ffd8b6a)
   



```python
# Creating a Line Graph to show any potential trend or correlation

plt.figure(figsize=(15, 5))
plt.title('Relation between Valence% and Acousticness%', fontsize=20)
sns.lineplot(x='valence_%', y='acousticness_%', data=spotify, marker='o')
plt.xlabel('Valence %', fontsize=14)
plt.ylabel('Acousticness %', fontsize=14)
plt.grid(True)

plt.show()
```


    
![output_76_0](https://github.com/user-attachments/assets/c8c6994a-fd19-492b-b77e-0611a10829e2)
    


-When it comes to the relation between Valence% and Acousticness%, most of the data above are scattered randomly, and most of the acousticness values are positioned at the lower percentage of acousticness. When we analyze the line graph, there are very few correlations evident with the trend as most of which are also scattered randomly. With those findings and the graphs above, we can say that there's no significant correlation between the two data.

## •  Platform Popularity

### 1. How do the numbers of tracks in spotify_playlists, spotify_charts, and apple_playlists compare? Which platform seems to favor the most popular tracks?

#### Numbers of tracks in spotify_playlists, spotify_charts, and apple_playlists


```python
# Comparing the number of tracks in spotify_playlists, spotify_charts, and apple_playlists using the .sum() function

platform_tracks = (spotify[['track_name','in_spotify_playlists','in_spotify_charts','in_apple_playlists']] !=0).copy().astype(int).sum()

# The 'track_name' serves as the TOTAL Number of Tracks
platform_tracks_data = platform_tracks.rename(index={'track_name': 'TOTAL'})

# To show the total number of tracks per the given category
print(platform_tracks_data)
```

    TOTAL                   953
    in_spotify_playlists    953
    in_spotify_charts       548
    in_apple_playlists      930
    dtype: int64
    


```python
# Removing the 'track name' for graphical representation
platform_tracks_table = platform_tracks.drop('track_name')

# Renaming the x-axis label for a more organized look
new_labels = ['Spotify Playlists (953)', 'Spotify Charts (548)', 'Apple Playlists (930)']

# Creating the actual Bar Graph
plt.figure(figsize=(10,6))
platform_tracks_table.plot(kind='bar')
plt.title('Number of Tracks per Category')
plt.ylabel('Number of Tracks')
plt.xticks(ticks=range(len(platform_tracks_table)), labels=new_labels, rotation=0)
plt.show()
```


    
![output_82_0](https://github.com/user-attachments/assets/a266aecd-f7d9-42b2-a7d2-ea354b8d0554)
  


-When we look at the graph above, we can see a massive difference in between the number of tracks in Playlists (Spotify and Apple) and in the Charts. When it comes to the two categories in playlists, Spotify has the complete amount of songs included in the list (953), while the Apple Playlist come in second (930).

#### Finding which platform seems to favor the most popular tracks


```python
# Combining the total numbers of charts and playlist per platform

# Spotify
pd.options.mode.copy_on_write = True # To prevent setting with copy warning
spotify_arr = spotify.sort_values('streams', ascending=False)
spotify_comb = spotify_arr[['in_spotify_charts', 'in_spotify_playlists', 'streams']]

# Combining the two numbers from Spotify Platform
spotify_comb.loc[:, "Combined Total"] = spotify_comb['in_spotify_charts'] + spotify_comb['in_spotify_playlists']
spotify_comb.drop(['in_spotify_charts', 'in_spotify_playlists'], axis=1, inplace=True)



# Apple
apple_comb = spotify_arr[['in_apple_charts', 'in_apple_playlists', 'streams']]

#Combining the two numbers from Apple Platform
apple_comb.loc[:, "Combined Total"] = apple_comb['in_apple_charts'] + apple_comb['in_apple_playlists']
apple_comb.drop(['in_apple_charts', 'in_apple_playlists'], axis=1, inplace=True)



# Deezer
deezer_comb = spotify_arr[['in_deezer_charts', 'in_deezer_playlists', 'streams']]

#Combining the two numbers from Apple Platform
deezer_comb.loc[:, "Combined Total"] = deezer_comb['in_deezer_charts'] + deezer_comb['in_deezer_playlists']
deezer_comb.drop(['in_deezer_charts', 'in_deezer_playlists'], axis=1, inplace=True)



# Shazham
shazam_comb = spotify_arr[['in_shazam_charts', 'streams']]

#Combining the two numbers from Apple Platform
shazam_comb.loc[:, "Combined Total"] = shazam_comb['in_shazam_charts']
shazam_comb.drop(['in_shazam_charts'], axis=1, inplace=True)



# Creating the Scatterplot

fig, platf = plt.subplots(2, 2, figsize=(18,10))

# SPOTIFY - STREAMS
sns.scatterplot(x='Combined Total', y='streams', data=spotify_comb, ax=platf[0, 0], edgecolor='none')
platf[0, 0].set_title('Spotify X Streams', fontsize=14)
platf[0, 0].set_xlabel('Spotify No.', fontsize=14)
platf[0, 0].set_ylabel('Streams', fontsize=14)

# APPLE - STREAMS
sns.scatterplot(x='Combined Total', y='streams', data=apple_comb, ax=platf[0, 1], edgecolor='none')
platf[0, 1].set_title('Apple X Streams', fontsize=14)
platf[0, 1].set_xlabel('Apple No.', fontsize=14)
platf[0, 1].set_ylabel('Streams', fontsize=14)

# DEEZER - STREAMS
sns.scatterplot(x='Combined Total', y='streams', data=deezer_comb, ax=platf[1, 0], edgecolor='none')
platf[1, 0].set_title('Deezer X Streams', fontsize=14)
platf[1, 0].set_xlabel('Deezer No.', fontsize=14)
platf[1, 0].set_ylabel('Streams', fontsize=14)

# SHAZAM - STREAMS
sns.scatterplot(x='Combined Total', y='streams', data=shazam_comb, ax=platf[1, 1], edgecolor='none')
platf[1, 1].set_title('Shazam X Streams', fontsize=14)
platf[1, 1].set_xlabel('Shazam No.', fontsize=14)
platf[1, 1].set_ylabel('Streams', fontsize=14)

# Adjust the vertical space between rows (hspace) and horizontal space between columns (wspace)
plt.subplots_adjust(hspace=0.3)  # Adjust as needed

# Show the plot
plt.show()
```


    
![output_85_0](https://github.com/user-attachments/assets/fae0e3a4-b67f-4891-830f-b562c724d841)
  


-Comparing the Four Scatterplots above, we can observe a large amount of numbers in the spotify graph. When observing the trends and patterns, We can see a somewhat positive correlation on the 'Spotify X Streams' and 'Apple X Streams', which signifies that the total number of charts and playlist in those platform positively correlates to the number of streams a song has. On the other hand, the bottom two figures shows an inconsistent relation as both of the numbers included in both platforms are low, which means that only few people uses the two platform, thus having an insignificant correlation with the song's number of streams.

## • Advanced Analysis

### 1. Based on the streams data, can you identify any patterns among tracks with the same key or mode (Major vs. Minor)?

#### Stream-Key Correlation


```python
# Creating a reference table for the graphic table

key_streams = spotify.groupby('key')['streams'].sum().reset_index()

key_frequency = spotify.groupby('key')['streams'].size().reset_index()

key_table = pd.merge(key_streams, key_frequency, on='key')
key_table.rename(columns={'streams_x': 'streams', 'streams_y': 'frequency'}, inplace=True)
key_table = key_table.sort_values('streams', ascending=False)
key_table
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>key</th>
      <th>streams</th>
      <th>frequency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>C#</td>
      <td>72513629843</td>
      <td>120</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C</td>
      <td>49513287260</td>
      <td>95</td>
    </tr>
    <tr>
      <th>10</th>
      <td>G</td>
      <td>43449542493</td>
      <td>96</td>
    </tr>
    <tr>
      <th>11</th>
      <td>G#</td>
      <td>43398979639</td>
      <td>91</td>
    </tr>
    <tr>
      <th>5</th>
      <td>D</td>
      <td>42891570295</td>
      <td>81</td>
    </tr>
    <tr>
      <th>2</th>
      <td>B</td>
      <td>42067184540</td>
      <td>81</td>
    </tr>
    <tr>
      <th>8</th>
      <td>F</td>
      <td>41691728620</td>
      <td>89</td>
    </tr>
    <tr>
      <th>9</th>
      <td>F#</td>
      <td>38132510024</td>
      <td>73</td>
    </tr>
    <tr>
      <th>7</th>
      <td>E</td>
      <td>35804825731</td>
      <td>62</td>
    </tr>
    <tr>
      <th>1</th>
      <td>A#</td>
      <td>31491099814</td>
      <td>57</td>
    </tr>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>30254264458</td>
      <td>75</td>
    </tr>
    <tr>
      <th>6</th>
      <td>D#</td>
      <td>18250205825</td>
      <td>33</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Comparison of the Songs' Keys with the Stream Data
plt.figure(figsize=(15, 5))
plt.title('Songs Keys with the Stream Data', fontsize=14)
plt.bar(key_streams['key'], key_streams['streams'])
plt.xlabel('Keys', fontsize=12)
plt.ylabel('Number of Streams', fontsize=12)
plt.show()
```


    
![output_91_0](https://github.com/user-attachments/assets/67d721fe-972f-4b9e-b4dd-fcd0eee05391)
    


-Based on the chart above, we can see that there's an increased amount of streams to the songs that are in the keys of C#, while the rest of the keys have closer values with each other. On the other hand, the lowest number of streams are the songs that are in the keys of A and D#. By looking at the frequency or the amount of song that every key has, we can notice a correlation with the frequency of key to the number of streams, making the Keys frequency proportional to the number of Streams.

#### Stream-Mode Correlation


```python
# Creating a reference table for the graphic table

mode_streams = spotify.groupby('mode')['streams'].sum().reset_index()

mode_frequency = spotify.groupby('mode')['streams'].size().reset_index()

mode_table = pd.merge(mode_streams, mode_frequency, on='mode')
mode_table.rename(columns={'streams_x': 'streams', 'streams_y': 'frequency'}, inplace=True)
mode_table = mode_table.sort_values('streams', ascending=False)
mode_table
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mode</th>
      <th>streams</th>
      <th>frequency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Major</td>
      <td>293623203541</td>
      <td>550</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Minor</td>
      <td>195835625001</td>
      <td>403</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Comparison of Major and Minor with the Stream Data

plt.figure(figsize=(5.5, 7))
plt.title('Major and Minor Keys on Streams', fontsize=14)
plt.bar(mode_table['mode'], mode_table['streams'])
plt.xlabel('Mode of Songs', fontsize=12)
plt.ylabel('Number of Streams', fontsize=12)
plt.show()
```


    
![output_95_0](https://github.com/user-attachments/assets/1064271a-4bc1-4a3e-b199-0c6cd62753c8)
  


-Looking at the resulting table above, we can see that there's a large difference with the amount of major and minor songs, which affected the graph above. By looking at the bar graph, we can see that the songs in major have a greater amount of stream than the songs in minor. By definition of the two modes, Major songs rely on the major keys in the notes, which produces a positive and bright tones. On the other hand, minor songs are focused on the negative/minor keys of the notes, which adds a gloomy or mysterious effect to the overall emotion of the song. With that, we can say that the songs that are considered happy/positives tend to have more streams than the gloomy songs.

### 2. Do certain genres or artists consistently appear in more playlists or charts? Perform an analysis to compare the most frequently appearing artists in playlists or charts.

#### Preparation of Artist Data


```python
# Setting up the Table of Frequency of Artist per platform

artist_platform = spotify[['artist(s)_name', 'streams', 'in_spotify_playlists', 'in_spotify_charts', 'in_apple_playlists', 'in_apple_charts', 'in_deezer_playlists', 'in_deezer_charts', 'in_shazam_charts']].copy()
artist_psorted = artist_platform.groupby('artist(s)_name', as_index=False)[['streams', 'in_spotify_playlists', 'in_spotify_charts', 'in_apple_playlists', 'in_apple_charts', 'in_deezer_playlists', 'in_deezer_charts', 'in_shazam_charts']].sum()
artist_psorted = artist_psorted.sort_values(by='streams',ascending=False,ignore_index=True)
artist_psorted.rename(columns={'artist(s)_name':'Artist',
                               'streams':'Streams',
                               'in_spotify_playlists':'Spotify Playlists',
                               'in_spotify_charts':'Spotify Charts',
                               'in_apple_playlists': 'Apple Playlists',
                               'in_apple_charts': 'Apple Charts',
                               'in_deezer_playlists':'Deezer Playlists',
                               'in_deezer_charts': 'Deezer Charts',
                               'in_shazam_charts': 'Shazam Charts'},
                        inplace=True)
# Using the .head() to find the top 5 streamed Artist Overall
artist_psorted.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Streams</th>
      <th>Spotify Playlists</th>
      <th>Spotify Charts</th>
      <th>Apple Playlists</th>
      <th>Apple Charts</th>
      <th>Deezer Playlists</th>
      <th>Deezer Charts</th>
      <th>Shazam Charts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>The Weeknd</td>
      <td>14185552870</td>
      <td>144053</td>
      <td>180</td>
      <td>1677</td>
      <td>1348</td>
      <td>7551</td>
      <td>23</td>
      <td>854</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Taylor Swift</td>
      <td>14053658300</td>
      <td>132974</td>
      <td>542</td>
      <td>1796</td>
      <td>1866</td>
      <td>3086</td>
      <td>58</td>
      <td>1811</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ed Sheeran</td>
      <td>13908947204</td>
      <td>128758</td>
      <td>94</td>
      <td>1448</td>
      <td>488</td>
      <td>16952</td>
      <td>43</td>
      <td>874</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Harry Styles</td>
      <td>11608645649</td>
      <td>110026</td>
      <td>185</td>
      <td>1741</td>
      <td>545</td>
      <td>3695</td>
      <td>76</td>
      <td>282</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Bad Bunny</td>
      <td>9997799607</td>
      <td>51317</td>
      <td>268</td>
      <td>589</td>
      <td>852</td>
      <td>751</td>
      <td>56</td>
      <td>603</td>
    </tr>
  </tbody>
</table>
</div>



#### Spotify Playlist


```python
# Spotify Playlists Table

S_P = artist_psorted.sort_values(by='Spotify Playlists',ascending=False,ignore_index=True)
S_P.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Streams</th>
      <th>Spotify Playlists</th>
      <th>Spotify Charts</th>
      <th>Apple Playlists</th>
      <th>Apple Charts</th>
      <th>Deezer Playlists</th>
      <th>Deezer Charts</th>
      <th>Shazam Charts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>The Weeknd</td>
      <td>14185552870</td>
      <td>144053</td>
      <td>180</td>
      <td>1677</td>
      <td>1348</td>
      <td>7551</td>
      <td>23</td>
      <td>854</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Taylor Swift</td>
      <td>14053658300</td>
      <td>132974</td>
      <td>542</td>
      <td>1796</td>
      <td>1866</td>
      <td>3086</td>
      <td>58</td>
      <td>1811</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ed Sheeran</td>
      <td>13908947204</td>
      <td>128758</td>
      <td>94</td>
      <td>1448</td>
      <td>488</td>
      <td>16952</td>
      <td>43</td>
      <td>874</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Harry Styles</td>
      <td>11608645649</td>
      <td>110026</td>
      <td>185</td>
      <td>1741</td>
      <td>545</td>
      <td>3695</td>
      <td>76</td>
      <td>282</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Eminem</td>
      <td>6183805596</td>
      <td>87331</td>
      <td>152</td>
      <td>475</td>
      <td>281</td>
      <td>15121</td>
      <td>12</td>
      <td>272</td>
    </tr>
  </tbody>
</table>
</div>



#### Spotify Charts


```python
# Spotify Charts Table

S_C = artist_psorted.sort_values(by='Spotify Charts',ascending=False,ignore_index=True)
S_C.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Streams</th>
      <th>Spotify Playlists</th>
      <th>Spotify Charts</th>
      <th>Apple Playlists</th>
      <th>Apple Charts</th>
      <th>Deezer Playlists</th>
      <th>Deezer Charts</th>
      <th>Shazam Charts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Taylor Swift</td>
      <td>14053658300</td>
      <td>132974</td>
      <td>542</td>
      <td>1796</td>
      <td>1866</td>
      <td>3086</td>
      <td>58</td>
      <td>1811</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bad Bunny</td>
      <td>9997799607</td>
      <td>51317</td>
      <td>268</td>
      <td>589</td>
      <td>852</td>
      <td>751</td>
      <td>56</td>
      <td>603</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Arctic Monkeys</td>
      <td>5569806731</td>
      <td>84016</td>
      <td>190</td>
      <td>241</td>
      <td>340</td>
      <td>4992</td>
      <td>6</td>
      <td>101</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Harry Styles</td>
      <td>11608645649</td>
      <td>110026</td>
      <td>185</td>
      <td>1741</td>
      <td>545</td>
      <td>3695</td>
      <td>76</td>
      <td>282</td>
    </tr>
    <tr>
      <th>4</th>
      <td>The Weeknd</td>
      <td>14185552870</td>
      <td>144053</td>
      <td>180</td>
      <td>1677</td>
      <td>1348</td>
      <td>7551</td>
      <td>23</td>
      <td>854</td>
    </tr>
  </tbody>
</table>
</div>



#### Apple Playlists


```python
# Apple Playlists Table

A_P = artist_psorted.sort_values(by='Apple Playlists',ascending=False,ignore_index=True)
A_P.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Streams</th>
      <th>Spotify Playlists</th>
      <th>Spotify Charts</th>
      <th>Apple Playlists</th>
      <th>Apple Charts</th>
      <th>Deezer Playlists</th>
      <th>Deezer Charts</th>
      <th>Shazam Charts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Taylor Swift</td>
      <td>14053658300</td>
      <td>132974</td>
      <td>542</td>
      <td>1796</td>
      <td>1866</td>
      <td>3086</td>
      <td>58</td>
      <td>1811</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Harry Styles</td>
      <td>11608645649</td>
      <td>110026</td>
      <td>185</td>
      <td>1741</td>
      <td>545</td>
      <td>3695</td>
      <td>76</td>
      <td>282</td>
    </tr>
    <tr>
      <th>2</th>
      <td>The Weeknd</td>
      <td>14185552870</td>
      <td>144053</td>
      <td>180</td>
      <td>1677</td>
      <td>1348</td>
      <td>7551</td>
      <td>23</td>
      <td>854</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Ed Sheeran</td>
      <td>13908947204</td>
      <td>128758</td>
      <td>94</td>
      <td>1448</td>
      <td>488</td>
      <td>16952</td>
      <td>43</td>
      <td>874</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Dua Lipa</td>
      <td>3227639000</td>
      <td>39940</td>
      <td>101</td>
      <td>765</td>
      <td>159</td>
      <td>2209</td>
      <td>42</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



#### Apple Charts


```python
# Apple Charts Table

A_C = artist_psorted.sort_values(by='Apple Charts',ascending=False,ignore_index=True)
A_C.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Streams</th>
      <th>Spotify Playlists</th>
      <th>Spotify Charts</th>
      <th>Apple Playlists</th>
      <th>Apple Charts</th>
      <th>Deezer Playlists</th>
      <th>Deezer Charts</th>
      <th>Shazam Charts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Taylor Swift</td>
      <td>14053658300</td>
      <td>132974</td>
      <td>542</td>
      <td>1796</td>
      <td>1866</td>
      <td>3086</td>
      <td>58</td>
      <td>1811</td>
    </tr>
    <tr>
      <th>1</th>
      <td>The Weeknd</td>
      <td>14185552870</td>
      <td>144053</td>
      <td>180</td>
      <td>1677</td>
      <td>1348</td>
      <td>7551</td>
      <td>23</td>
      <td>854</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SZA</td>
      <td>4557811204</td>
      <td>44539</td>
      <td>110</td>
      <td>680</td>
      <td>1070</td>
      <td>567</td>
      <td>27</td>
      <td>446</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NewJeans</td>
      <td>1544567007</td>
      <td>5127</td>
      <td>168</td>
      <td>133</td>
      <td>877</td>
      <td>72</td>
      <td>13</td>
      <td>283</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Bad Bunny</td>
      <td>9997799607</td>
      <td>51317</td>
      <td>268</td>
      <td>589</td>
      <td>852</td>
      <td>751</td>
      <td>56</td>
      <td>603</td>
    </tr>
  </tbody>
</table>
</div>



#### Deezer Playlists


```python
# Deezer Playlists Table

D_P = artist_psorted.sort_values(by='Deezer Playlists',ascending=False,ignore_index=True)
D_P.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Streams</th>
      <th>Spotify Playlists</th>
      <th>Spotify Charts</th>
      <th>Apple Playlists</th>
      <th>Apple Charts</th>
      <th>Deezer Playlists</th>
      <th>Deezer Charts</th>
      <th>Shazam Charts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Ed Sheeran</td>
      <td>13908947204</td>
      <td>128758</td>
      <td>94</td>
      <td>1448</td>
      <td>488</td>
      <td>16952</td>
      <td>43</td>
      <td>874</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Eminem</td>
      <td>6183805596</td>
      <td>87331</td>
      <td>152</td>
      <td>475</td>
      <td>281</td>
      <td>15121</td>
      <td>12</td>
      <td>272</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Linkin Park</td>
      <td>2985590613</td>
      <td>45176</td>
      <td>11</td>
      <td>102</td>
      <td>0</td>
      <td>14149</td>
      <td>2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Nirvana</td>
      <td>2058839789</td>
      <td>59505</td>
      <td>9</td>
      <td>310</td>
      <td>148</td>
      <td>13564</td>
      <td>4</td>
      <td>203</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Coldplay</td>
      <td>3825176058</td>
      <td>75716</td>
      <td>72</td>
      <td>381</td>
      <td>25</td>
      <td>12727</td>
      <td>10</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



#### Deezer Charts


```python
# Deezer Charts Table

D_C = artist_psorted.sort_values(by='Deezer Charts',ascending=False,ignore_index=True)
D_C.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Streams</th>
      <th>Spotify Playlists</th>
      <th>Spotify Charts</th>
      <th>Apple Playlists</th>
      <th>Apple Charts</th>
      <th>Deezer Playlists</th>
      <th>Deezer Charts</th>
      <th>Shazam Charts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Harry Styles</td>
      <td>11608645649</td>
      <td>110026</td>
      <td>185</td>
      <td>1741</td>
      <td>545</td>
      <td>3695</td>
      <td>76</td>
      <td>282</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Miley Cyrus</td>
      <td>1887370770</td>
      <td>15583</td>
      <td>134</td>
      <td>365</td>
      <td>263</td>
      <td>883</td>
      <td>59</td>
      <td>1123</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Taylor Swift</td>
      <td>14053658300</td>
      <td>132974</td>
      <td>542</td>
      <td>1796</td>
      <td>1866</td>
      <td>3086</td>
      <td>58</td>
      <td>1811</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Bad Bunny</td>
      <td>9997799607</td>
      <td>51317</td>
      <td>268</td>
      <td>589</td>
      <td>852</td>
      <td>751</td>
      <td>56</td>
      <td>603</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OneRepublic</td>
      <td>3097149603</td>
      <td>37646</td>
      <td>119</td>
      <td>420</td>
      <td>224</td>
      <td>3852</td>
      <td>48</td>
      <td>485</td>
    </tr>
  </tbody>
</table>
</div>



#### Shazam Charts


```python
# Shazam Charts Table

S_C = artist_psorted.sort_values(by='Shazam Charts',ascending=False,ignore_index=True)
S_C.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Artist</th>
      <th>Streams</th>
      <th>Spotify Playlists</th>
      <th>Spotify Charts</th>
      <th>Apple Playlists</th>
      <th>Apple Charts</th>
      <th>Deezer Playlists</th>
      <th>Deezer Charts</th>
      <th>Shazam Charts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Taylor Swift</td>
      <td>14053658300</td>
      <td>132974</td>
      <td>542</td>
      <td>1796</td>
      <td>1866</td>
      <td>3086</td>
      <td>58</td>
      <td>1811</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jain</td>
      <td>165484133</td>
      <td>6060</td>
      <td>53</td>
      <td>150</td>
      <td>148</td>
      <td>2703</td>
      <td>22</td>
      <td>1451</td>
    </tr>
    <tr>
      <th>2</th>
      <td>David Kushner</td>
      <td>511978174</td>
      <td>4316</td>
      <td>98</td>
      <td>93</td>
      <td>156</td>
      <td>214</td>
      <td>25</td>
      <td>1281</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Billie Eilish</td>
      <td>2616432448</td>
      <td>18521</td>
      <td>106</td>
      <td>344</td>
      <td>494</td>
      <td>731</td>
      <td>24</td>
      <td>1198</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Ayparia unxbected</td>
      <td>58054811</td>
      <td>641</td>
      <td>50</td>
      <td>1</td>
      <td>52</td>
      <td>8</td>
      <td>0</td>
      <td>1170</td>
    </tr>
  </tbody>
</table>
</div>



#### Table Analysis

-Using the .head() function per table, we can easily find the top five artist with the highest amount per categories. By looking at the results, Taylor Swift appeared the most in those platform with the value of 7 (seven times), while the second artist that appeared is Ed Sheeran, which appeared in five different platforms. The Weeknd earned the third place by appearing four times, while Harry Styles and Bad Bunny is tied for the fourth place by appearing in 3 different platforms. The fifth placer is Eminem which appeared twice in the top 5 of different platforms, and some only appeared once on different platforms.


```python
# End of Code
```
