# Database Design Document

## Overview

This document describes the schema design for a MongoDB database that includes three main collections: `Users`, `Movies`, and `TVShows`. The design leverages Mongoose for schema definition and validation.

### User Schema

The `User` collection stores information about users, including their email, password, and a watchlist that can contain references to both movies and TV shows.

- **email**: String, Required, Unique
  - The user's email address. It must be unique to prevent duplicate accounts.
- **password_hashed**: String, Required
  - The hashed version of the user's password for security purposes.
- **watchlist**: Array of Objects
  - A collection of references to `Movie` and `TVShow` documents. Each object in the array includes an `_id` (referencing the document's ObjectId) and a `type` indicating whether the referenced document is a "Movie" or a "TV Show".

### Movie Schema

The `Movie` collection contains detailed information about movies, including titles, ratings, and other relevant metadata.

- **title**: String, Required
  - The title of the movie.
- **imdbId**: String
  - The unique identifier from IMDb for the movie.
- **rating**: Number
  - The movie's rating, typically based on user reviews or critic scores.
- **runtime**: Number
  - The duration of the movie in minutes.
- **language**: String, Required
  - The primary language of the movie.
- **releaseDate**: Date, Required
  - The official release date of the movie.
- **status**: String
  - The current status of the movie (e.g., "Released", "In Production").
- **genres**: Array of Strings
  - A list of genres that describe the movie.
- **summary**: String, Required
  - A brief summary or synopsis of the movie's plot.
- **cast**: Array of Strings, Required
  - A list of the main cast members in the movie.
- **homepage**: String
  - The URL to the movie's official homepage.
- **bannerUrl**: String
  - The URL to the movie's banner image.
- **posterUrl**: String
  - The URL to the movie's poster image.
- **trailerUrl**: String
  - The URL to the movie's trailer.

### TV Show Schema

The `TVShow` collection holds information about TV shows, similar to the `Movie` schema but tailored for serialized content.

- **title**: String, Required
  - The title of the TV show.
- **imdbid**: String
  - The unique identifier from IMDb for the TV show.
- **rating**: Number
  - The TV show's rating.
- **rated**: String
  - The age or content rating of the TV show.
- **language**: String, Required
  - The primary language of the TV show.
- **firstAirDate**: Date, Required
  - The date of the first episode's airing.
- **lastAirDate**: Date
  - The date of the last episode's airing (if applicable).
- **status**: String
  - The current status of the TV show (e.g., "Running", "Ended").
- **genres**: Array of Strings
  - A list of genres that describe the TV show.
- **summary**: String, Required
  - A brief summary or synopsis of the TV show's plot.
- **cast**: Array of Strings
  - A list of the main cast members in the TV show.
- **homepage**: String
  - The URL to the TV show's official homepage.
- **bannerUrl**: String
  - The URL to the TV show's banner image.
- **posterUrl**: String
  - The URL to the TV show's poster image.

## Relationships

- The `User` schema's `watchlist` field establishes a many-to-many relationship between users and the content they wish to track (Movies and TV Shows). Each item in the watchlist specifies the `_id` of the content and its `type` to distinguish between a `Movie` and a `TVShow`.
