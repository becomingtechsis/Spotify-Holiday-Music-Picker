# Spotify-Holiday-Music-Picker

## Introduction
Built a Holiday Song Picker using the Image Grid custom visual in Power BI using data from Spotify to help select a song based on Artist, Tempo, or Key.

## Dataset
The Data is from Spotify, that’s stored in a [Data.World](https://data.world/promptcloud/spotify-musical-features-of-160-holiday-songs) dataset. The playlist itself can be found on [Spotify](https://open.spotify.com/playlist/5l6rFyXN63iINVsbaBObag?si=41faa99ae0b84b75)


## Visualization
- Filtered the columns to columns needed for this visualization.
- Renamed Columns.
- Adjusted my canvas size to create a layout that worked with my design. I used Spotify for inspiration and the [Spotify color template](https://www.color-hex.com/color-palette/53188) 
- Added the Image Grid custom visual and used the album image in the Image URL field
- Added slicers, visuals, and text to help users pick a holiday song!


## Measures
Created a measure to show users which song(s) they have selected! I called out Artist, Song, Text and Danceability

### Artist
```Artist =```  

```IF(```

```ISFILTERED( Songs[artist_name] )``` 
    
```ISFILTERED( Songs[album_img] ),``` 

    
```SELECTEDVALUE( Songs[artist_name]),``` 
        
```"")``` 
 

### Danceability
```Danceability =```

```IF(```

```ISFILTERED( Songs[artist_name] )```
    
```ISFILTERED( Songs[album_img] ),```

```SELECTEDVALUE( Songs[danceability]),```

```"")```
 
### Song
```Song = IF(```

```ISFILTERED( Songs[artist_name] )```

```ISFILTERED( Songs[album_img] ),```

```SELECTEDVALUE( Songs[track_name]),```

```"Select an Album")```


  ### Text
```Text =``` 

```IF(```
   
```HASONEVALUE(Songs[track_name]),```
    
```"It's time to listen to '" &```

```[Song] &```
    
```"' by " &```
    
```[Artist] &```
    
```". Fun fact, this song has a danceability score of " &```

```[Danceability] &```

```" 🕺🏼💃🏼!",```

```"Please pick an artist or album!"```

```)```
