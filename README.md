# 2022's Hottest Tracks as Data:
Final Curation Protocol project for LIS 545 (Data Curation I) in the MLIS program at the University of Washington.
<br><br>
This data was curated by Joe Lollo, and is intended for re-use in data-driven research or journalism.
<br><br>
The dataset was created to support researchers interested in the influences of social media on global music charts, particularly through combining the 100 most popular songs on TikTok and Spotify over a 12-month period from January to December 2022. The dataset quantifies the popularity of each song and artist through the applications’ own analytics. This includes each song’s highest position, and the number of weeks they spent, on the Spotify charts, as well as each song and artist’s popularity on TikTok.
<br><br>
This Readme file contains similar contents to the [final report I wrote](https://github.com/ChessPiece21/LIS-54X/blob/main/Curation-Protocol/Curation-Protocol-Report.pdf) for the protocol.

## Datasets:
The main dataset is titled **[2022-Music-Charts.csv](https://github.com/ChessPiece21/LIS-54X/blob/main/Curation-Protocol/2022-Music-Charts.csv)**, and is the result of joining two datasets together (2022-Spotify-Charts and 2022-TikTok-Charts) to create a centralized dataset for both platforms.
<br><br>
The original, raw datasets from both Spotify (gathered by me using the Spotify API) and TikTok (gathered and shared publicly by Kaggle user [sveta151](https://www.kaggle.com/sveta151)) are also included in this repository, in the folder titled [raw-data](https://github.com/ChessPiece21/LIS-54X/tree/main/Curation-Protocol/raw-data).

## Normalization:
The Spotify dataset was gathered raw using the [spotifyr](https://www.rcharlie.com/spotifyr/) package for the statistical programming language R. Once I had both the Spotify and TikTok datasets, I used the "full.join()" method in R, as explained in [*R for Data Science*](https://r4ds.had.co.nz/) by Hadley Wickham.
<br><br>
In the combined dataset, there were a few steps taken for normalization:
- Variables for chart positions, popularity, and URIs were renamed to show the platform they came from. For example, "track_pop" in the TikTok dataset was renamed "tiktok_track_pop," while "chart_pos" in the Spotify dataset was renamed "spotify_chart_pos." I did this using the open-source spreadsheet application [OpenRefine](https://openrefine.org/).
- Boolean (true/false) column variables for whether a song was on the Spotify and TikTok charts were added, called "spotify_chart" and "tiktok_chart" respectively. At least one of these variables will be "true" for each song in the combined dataset. This was also done using OpenRefine.
- Spotify [uniform resource indicators (URIs)](https://community.spotify.com/t5/FAQs/What-s-a-Spotify-URI/ta-p/919201) were added for all of the songs from the TikTok dataset that were not also in the Spotify dataset. This was done so that researchers could confirm that each song was what it claims to be in the data. I added them manually by searching for each song on Spotify and then filling in each blank column using Microsoft Excel. The "uri" column from the Spotify dataset was consequently renamed "spotify_uri."

## Potential Data Quality Issue:
This data represents the top 100 songs on TikTok and Spotify **from January 1, 2022 to December 31, 2022,** being a representative sample of the charts over a yearly period of time. I wanted to represent each month, but the resulting amount of data would be too large not very tractable.
 
## Naming Conventions:
No spaces or special symbols appear in file or variable names. Everything that would be a space in natural language was replaced with an underscore or hyphen.

## Sources:
The Spotify data was gathered by me using the [Spotify API](https://developer.spotify.com/documentation/web-api/), while the TikTok data was posted by [sveta151 on Kaggle](https://www.kaggle.com/datasets/sveta151/tiktok-popular-songs-2022) and gathered by them using the [TikTok API](https://developers.tiktok.com/).

## Metadata and Additional Documentation:
- [Data Dictionary](https://github.com/JoeLollo21/Music-Data-Curation/blob/main/Data-Dictionary.csv): This data dictionary for 2022-Music-Charts is located in the repository. It was only done as a CSV because table formatting in Markdown was hard and relied too much on trial and error.
- [XML Metadata](https://github.com/JoeLollo21/Music-Data-Curation/blob/main/Music-Charts-Metadata.xml): Metadata for the dataset was created using the Dublin Core schema, indicating the creator, topics, and access rights. It is also located in the repository.
- [Report Bibliography](https://github.com/JoeLollo21/Music-Data-Curation/blob/main/Bibliography.md)
