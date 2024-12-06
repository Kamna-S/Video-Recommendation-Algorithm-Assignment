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
