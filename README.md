# Video Recommender System

A Python-based recommendation system that fetches and preprocesses data from a social video API to provide personalized and popularity-based video recommendations.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Features](#features)
3. [Requirements](#requirements)
4. [Setup Instructions](#setup-instructions)
5. [Usage](#usage)
    - [Fetching Data](#fetching-data)
    - [Preprocessing Data](#preprocessing-data)
    - [Getting Recommendations](#getting-recommendations)
6. [API Endpoints](#api-endpoints)
7. [Class Methods Overview](#class-methods-overview)
8. [Recommendation Logic](#recommendation-logic)
9. [Error Handling](#error-handling)
10. [Acknowledgments](#acknowledgments)

---

## Introduction

The **Social Video Recommender System** leverages data from a REST API to build a recommendation engine for video posts. It supports:
- **Personalized recommendations** based on user interactions (views, likes, ratings).
- **Popularity-based recommendations** for new users or fallback scenarios.

This project is useful for platforms aiming to enhance user engagement with personalized video content suggestions.

---

## Features

- Fetches data from multiple paginated API endpoints.
- Preprocesses user and post interaction data to create:
  - **Interaction matrices**
  - **Content-based feature sets**
- Provides personalized recommendations using **collaborative filtering**.
- Offers fallback recommendations based on post popularity.
- Includes robust error handling for API and data issues.

---

## Requirements

- **Python 3.7+**
- Libraries:
  - `requests`
  - `pandas`
  - `numpy`
  - `scikit-learn`
  - `datetime`
  - `traceback`

---

## Setup Instructions

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/Kamna-S/Video-Recommendation-Algorithm-Assignment.git
## Usage

### **1. Fetching Data**
The application uses the `requests` library to fetch data from an external API.

Example:
```python
import requests

api_endpoint = "https://example.com/api/videos"
response = requests.get(api_endpoint)
data = response.json()


## **2. Preprocessing Data**
The fetched data is cleaned and normalized using:
- **pandas** for handling missing or invalid values.
- **sklearn.preprocessing.MinMaxScaler** for scaling features like views, likes, and upvotes between 0 and 1.

### Example:
```python
from sklearn.preprocessing import MinMaxScaler
import pandas as pd

# Assuming `data` is the raw JSON data fetched from the API
df = pd.DataFrame(data)

# Scaling the 'views', 'likes', and 'upvotes' columns
scaler = MinMaxScaler()
df[['views', 'likes', 'upvotes']] = scaler.fit_transform(df[['views', 'likes', 'upvotes']])

# Now the data is normalized
print(df.head())



## **3. Getting Recommendations**
The recommender system computes the similarity between videos based on features such as views, likes, and upvotes.

### Example Logic:
```python
from sklearn.metrics.pairwise import cosine_similarity

# Compute similarity matrix based on 'views', 'likes', and 'upvotes'
similarity_matrix = cosine_similarity(df[['views', 'likes', 'upvotes']])

# Get top N recommended videos for a given video index
recommended_videos = similarity_matrix[video_index].argsort()[-n_recommendations:]



## API Endpoints
If integrated into a Flask API, here are some example endpoints:

- **GET /videos**: Fetches a list of all videos.
- **GET /recommendations/<video_id>**: Returns recommendations for a given video ID.

## Class Methods Overview

### 1. `fetch_data(api_endpoint)`
Fetches data from the given API endpoint.

- **Input**: API URL
- **Output**: JSON data

### 2. `preprocess_data(data)`
Cleans and normalizes the fetched data.

- **Input**: Raw JSON data
- **Output**: Preprocessed DataFrame

### 3. `get_recommendations(video_index, n_recommendations)`
Generates recommendations based on cosine similarity.

- **Input**: Index of the video, number of recommendations
- **Output**: List of recommended video IDs

## Recommendation Logic
The recommender system uses content-based filtering to suggest videos based on features such as:

- Views
- Likes
- Upvotes

The system computes similarity between videos using cosine similarity and selects the top N similar videos for recommendations.

## Error Handling
The system handles errors gracefully, including:

- API request failures
- Missing data
- Invalid inputs

It ensures the system remains operational even when facing unexpected conditions.

### Example:
```python
try:
    response = requests.get(api_endpoint)
    response.raise_for_status()
except requests.exceptions.RequestException as e:
    print(f"Error fetching data: {e}")

## Acknowledgments
- **Requests** library for making HTTP requests.
- **Pandas** for data manipulation and preprocessing.
- **scikit-learn** for providing tools for similarity calculations.
- **Flask** (if used) for creating API endpoints.
