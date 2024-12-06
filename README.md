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


## 1. Fetching Data
The application uses the `requests` library to fetch data from an external API. The data is typically fetched from an API endpoint, which returns JSON data. This data can then be processed and used for further analysis.

## 2. Preprocessing Data
Once the data is fetched, it needs to be cleaned and normalized. The preprocessing step uses the **pandas** library to handle missing or invalid values, and **sklearn.preprocessing.MinMaxScaler** to scale numerical features like views, likes, and upvotes between a range of 0 and 1. This ensures that all numerical data is in a comparable range for analysis and modeling.

## 3. Getting Recommendations
The recommender system works by computing the similarity between videos based on features such as views, likes, and upvotes. It uses cosine similarity to measure how similar two videos are based on these features. The system then recommends the top N most similar videos to a given video.

## API Endpoints
If the system is integrated into a Flask API, it exposes the following endpoints:

- **GET /videos**: This endpoint fetches a list of all available videos from the database or external API.
- **GET /recommendations/<video_id>**: This endpoint returns recommendations for a given video based on the video ID. It calculates the similarity between the selected video and others, returning the top recommended videos.

## Class Methods Overview

### 1. `fetch_data(api_endpoint)`
This method is responsible for fetching data from an external API endpoint. It takes the API URL as an input and returns the data in JSON format.

### 2. `preprocess_data(data)`
This method processes the raw JSON data to clean it and prepare it for analysis. It normalizes the features (such as views, likes, and upvotes) to ensure that all the values are within a consistent range, making the data ready for recommendation calculation.

### 3. `get_recommendations(video_index, n_recommendations)`
This method calculates recommendations based on cosine similarity between videos. It takes the index of a video and the number of recommendations required, then returns a list of video IDs that are most similar to the given video.

## Recommendation Logic
The recommendation system uses content-based filtering, where it recommends videos based on features like views, likes, and upvotes. It computes the similarity between videos using cosine similarity, and selects the top N most similar videos for recommendations.

## Error Handling
The system is designed to handle errors gracefully. It handles potential issues like API request failures, missing data, and invalid inputs. If any unexpected conditions occur, the system will ensure that it continues running smoothly, logging any errors that occur during execution.

## Acknowledgments
- **Requests** library for making HTTP requests.
- **Pandas** for data manipulation and preprocessing.
- **scikit-learn** for providing tools for similarity calculations.
- **Flask** (if used) for creating API endpoints.

