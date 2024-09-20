# Travel-planner-app
This code implements a basic recommendation system using K-Nearest Neighbors (KNN) algorithm
for a dataset of Airbnb listings.
Let's break down the different parts and functionalities:


1. Data Loading and Preprocessing:

   - `load_data(csv_path)`:
     - Reads the Airbnb data from a CSV file (specified by `csv_path`).
     - Creates a user-item matrix using `pivot_table`.
     - The matrix has `id` as rows, `host_id` as columns, and `price` as values, representing the average price for each listing by a host.
     - Missing values (where a host doesn't have a listing for a particular id) are filled with 0.

2. KNN Model Training:

   - `train_knn_model(user_item_matrix, n_neighbors=5)`:
     - Initializes a KNN model with cosine similarity as the distance metric and brute-force algorithm.
     - `n_neighbors=5` means it will consider the 5 nearest neighbors for recommendations.
     - Fits the KNN model on the user-item matrix.


3. Destination Recommendations:

   - `recommend_destinations(knn_model, user_id, user_item_matrix, top_n=5)`:
     - Takes the trained KNN model, a user ID, the user-item matrix, and the number of recommendations to generate (`top_n`) as input.
     - Finds the K nearest neighbors for the given user based on the cosine similarity in the user-item matrix.
     - It returns a list of `(destination_id, average_price)` tuples. These are recommendations for the user based on the average price of their neighbours.

4. Revenue Calculation:

   - `calculate_revenue(recommendations, cost_per_booking=500, fixed_cost=2000)`:
     - Calculates the total revenue based on the number of recommended destinations.
     - The formula is: Revenue = (Cost per booking * Number of recommendations) - Fixed cost.


5. Example Usage:

   - Reads the data using `csv_path`.
   - Trains the KNN model.
   - Gets recommendations for the user with `user_id = 2539`.
   - Prints the top recommendations and the total revenue generated.


Limitations:
   - The current recommendation approach only considers the user's average price of their neighbors and doesn't capture other factors like location, amenities, or user reviews.
   - The revenue calculation is very simplistic and doesn't account for the actual bookings made based on the recommendations.



Conclusion:
   - This code provides a basic framework for building a recommendation system for Airbnb listings using KNN.
   - It can be improved by adding more features and considering other aspects of the data.
