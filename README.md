# Item-Based Anime Recommendation System

This is an Item-Based Anime Recommendation System, which predicts the rating of a particular anime for a specific user based on the similarity of anime and the ratings given by the user to the similar anime. The core algorithm relies on the cosine similarity between the anime based on their user ratings.

## How it works

The system works by finding anime that are similar to the one specified, then uses the ratings given by the user to these similar anime to predict what the user's rating would be for the specified anime.

The function `predict_rating(user_id, anime_name, max_neighbor=10)` is the heart of this system. Here is a brief overview of its parameters and what it does:

- **user_id** (int): The ID of the user for whom the rating is being predicted.
- **anime_name** (str): The name of the anime for which the rating is being predicted.
- **max_neighbor** (int, optional): The maximum number of similar anime to consider for the prediction. Defaults to 10.

## Algorithm Overview

Here's what the `predict_rating` function does in detail:

1. `get_similar_anime(anime_name)` is called to get a list of anime that are similar to the specified anime, along with their similarity scores.
2. We then create arrays for the similar anime and their scores.
3. We filter out any anime that haven't been rated by the specified user.
4. The prediction is then calculated as a weighted average of the user's ratings for the similar anime, with the similarity scores used as weights. Only the top `max_neighbor` similar anime (by similarity score) are used in this calculation.
5. The predicted rating is then returned.

## Running the Code

To use this system, you need to have a dataset of anime and user ratings, and the dataset should be in a specific format. For instance, a normalized pivot table named `pivot_norm` with user ratings is required. You will also need the unnormalized pivot table named `pivot` for calculating the weighted average.

## Requirements

- numpy
- pandas

## Note

This recommendation system is built for anime, but with slight modifications, it can be adapted for other types of items (movies, books, etc.).

