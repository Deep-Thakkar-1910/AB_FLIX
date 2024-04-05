# API Documentation

## Overview

This document provides detailed information on the API endpoints for a movie and TV show information service. It covers user management, movie and TV show information retrieval, watchlist management, and trending content.

## User Management

### Register a New User

- **POST** `/user/register`

**Request Body:**

```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

**Response:**

- **Status:** 201 Created

```json
{
  "success": true,
  "message": "User Registered successfully.",
  "email": "USER_EMAIL"
}
```

### User Login

- **POST** `/user/login`

**Request Body:**

```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

**Response:**

- **Status:** 200 OK

```json
{
  "success": true,
  "access_token": "Bearer token"
}
```

### Get User Information

- **GET** `/user/details`

**Headers:**

`Authorization: Bearer <token>`

**Response:**

- **Status:** 200 OK

```json
{
  "success": true,
  "userDetails": {
    "_id": "user_id",
    "email": "user@example.com"
  }
}
```

## Movie Information

### Get All Movies

- **GET** `/movies?page=<page_number>`

**Response:**

- **Status:** 200 OK

```json
[
  {
    "title": "Movie Title",
    "bannerUrl": "image_url",
    "releaseDate": "release_date",
    "type": "movie_type"
  },
  ...
]
```

### Search Movies

- **GET** `/movies/search?title=<search_query>`

**Response:**

- **Status:** 200 OK

```json
[
  {
    "title": "Movie Title",
    "bannerUrl": "image_url",
    "releaseDate": "release_date",
    "type": "movie_type"
  },
  ...
]
```

### Get Movie by ID

- **GET** `/movies/:id`

**Response:**

- **Status:** 200 OK

```json
{
  "title": "Movie Title",
  "releaseDate": "release_date",
  "rating": "movie_rating",
  "summary": "movie_summary",
  "genres": ["genre1", "genre2"],
  "runtime": "runtime_in_minutes",
  "language": "movie_language",
  "posterUrl": "poster_image_url",
  "status": "movie_status"
}
```

## TV Show Information

### Get All TV Shows

- **GET** `/tvshows?page=<page_number>`

**Response:**

- **Status:** 200 OK

```json
[
  {
    "title": "TV Show Title",
    "bannerUrl": "image_url",
    "firstAirDate": "first_air_date",
    "lastAirDate": "last_air_date",
    "type": "tv_show_type"
  },
  ...
]
```

### Search TV Shows

- **GET** `/tvshows/search?title=<search_query>`

**Response:**

- **Status:** 200 OK

```json
[
  {
    "title": "TV Show Title",
    "bannerUrl": "image_url",
    "firstAirDate": "first_air_date",
    "lastAirDate": "last_air_date",
    "type": "tv_show_type"
  },
  ...
]
```

### Get TV Show by ID

- **GET** `/tvshows/:id`

**Response:**

- **Status:** 200 OK

```json
{
  "title": "TV Show Title",
  "firstAirDate": "first_air_date",
  "lastAirDate": "last_air_date",
  "rating": "tv_show_rating",
  "summary": "tv_show_summary",
  "genres": ["genre1", "genre2"],
  "runtime": "runtime_in_minutes",
  "language": "tv_show_language",
  "posterUrl": "poster_image_url",
  "status": "tv_show_status"
}
```

## Watchlist Management

### Get User Watchlist

- **GET** `/watchlist`

**Headers:**

`Authorization: Bearer <token>`

**Response:**

- **Status:** 200 OK

```

json
[
  {
    "_id": "movie_or_tv_show_id",
    title: "movie_or_tv_show_title",
    bannerUrl: "movie_or_tv_show_bannerUrl,
    releaseDate:"movie_release_date",
    firstAirDate:"tv_show_first_air_date",
    lastAirDate:"tv_show_first_last_date",
    "type": "movie_or_tvShow"
  },
  ...
]
```

### Add to Watchlist

- **POST** `/watchlist/:id`

**Headers:**

`Authorization: Bearer <token>`

**Response:**

- **Status:** 200 OK

```json
{
  "success": true,
  "message": "movie_or_tv_show_added_to_watchlist successfully"
}
```

### Delete from Watchlist

- **DELETE** `/watchlist/:id`

**Headers:**

`Authorization: Bearer <token>`

**Response:**

- **Status:** 200 OK

```json
{
  "success": true,
  "message": "movie_or_tv_show_removed_from_watchlist successfully"
}
```

## Trending Content

### Get Trending Movies and TV Shows

- **GET** `/trending`

**Response:**

- **Status:** 200 OK

```json
[
  {
    "title": "Trending Title",
    "bannerUrl": "image_url",
    "releaseDate": "release_date_or_first_air_date",
    "type": "movie_or_tv_show_type"
  },
  ...
]
```

This documentation provides a comprehensive guide to the available API endpoints, including the methods, URLs, request bodies, and response formats.
