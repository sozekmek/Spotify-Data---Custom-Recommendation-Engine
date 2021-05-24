# Spotify-Custom Recommendation Engine

## Introduction

Spotify creates a playlist for its every user yearly, collecting their favourite tracks for that year. On this project, I wanted to use this playlist as a basis to make recommendations. Input will be this playlist and the output will be a seperate playlist called "Recommendations".

## Folder Structure
* **2020_top_songs.csv:** CSV file for the dataframe including all the tracks from 2020 Favourites Playlist with their corresponding audio features.
* **script.ipynb:** Jupyter Notebook for all the work done for this project.
* **tracks.csv:** CSV file for the dataframe of a database including 600.000 tracks. 
* **sim_tracks_df.csv:** CSV file for the dataframe including the calculated similarities between the 2020 Favourites Playlist and the track database.

## Logic of the Recommendation Engine
Spotify uses some latent features to define all the tracks on their database. They are as following with their descriptions (descriptions are my understanding, they are not official descriptions from Spotify):
* **Danceability:** Used for determining mood, how much the song is suitable for dance
* **Energy:** Used for determining mood, how upbeat is the track
* **Loudness:** Used for determining propeties, how high is the overall decibel of the track
* **Speechiness:** Used for determining propeties, how heavy is the track on vocals
* **Acousticness:** Used for determining context, how much a track resembles an acoustic performance
* **Instrumentalness:** Used for determining propeties, how heavy is the track on instruments
* **Liveness:** Used for determining context, how much a track resembles an live performance
* **Valence:** Used for determining mood, how positive the track is musically
* **Tempo:** Used for determining mood, overall estimated tempo of the track in terms of Beats Per Minute (BPM)

Features of all the songs on my 2020 Favourites Playlist is gathered and their distributions are visualized. For that, Minimum-Maximum Scaling is needed because ranges of the values are different and without the scaling different features will have different weights on the predictions. To make each features weight uniform, scaling is applied. 

![image](https://user-images.githubusercontent.com/61328773/119312020-7a5ed780-bc7a-11eb-92a4-5f660ed4ec86.png)

According to these metrics, I have created my preferences to be used as a referance to make recommendations. Dot product of array created from these mean values and the audio features of each track on the database shows how similar they are.

![image](https://user-images.githubusercontent.com/61328773/119314315-49cc6d00-bc7d-11eb-897b-b5758985a6b2.png)

Calculated similarity metric for each track is stored as a column on database and that database is saved as *sim_track_df.csv*.

This dataframe is then sorted as descending and top 20 tracks are added to the created *Recommendations* playlist on Spotify.

## Results

My evaluation metric for this project is subjective as a I can listen to the songs and determine if the recommendations were good or not.
Following are my comments for each track:
