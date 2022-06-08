# Movie Recommendation Collaborative Filtering
Collaborative Filtering focuses on user’s preference data and recommend movies based on it through matching with other users’ historical movies that have a similar preference as well and does not require movies’ metadata.

![image](https://user-images.githubusercontent.com/86812576/172524526-52d7d882-0d04-48f4-8828-b4920e38c4ce.png)

The way colllaborative filtering works is to look for similarities between users from the way they choose products, and take advantage of product similarities. So when someone buys a product and gives a high rating, what the machine does is provide recommendations for similar products.

The way I do it is by using a _dimensionality reduction_ technique, namely decomposition of the sparse matrix.

![image](https://user-images.githubusercontent.com/86812576/172528332-5f218c95-3fca-4695-942a-840246f648a4.png)

Why do I use matrix decomposition? the idea is that if there is a matrix A it can be split into a matrix U (code) and V (feature), which if U and V are multiplied it will be similar to the original matrix (A).

Now we do the same thing on the sparse matrix (perforated matrix), then do a modified SVD technique so that it can still be decomposed into U and V based on the existing data. The goal is that when U and V are multiplied to produce a complete matrix, that is, to fill in the gaps with predictions derived from user similarity and content similarity.

# Import Package
import package:
- import pandas as pd
- import numpy as np
- 
# Import Data

The data that I use in this project is user rating data, consisting of 1000209 rows and 3 columns, namely 'UserId', 'movie', and 'rating'.

# Training
Assign

![image](https://user-images.githubusercontent.com/86812576/172529493-e1ee8f69-0b5a-4dc4-b0dd-e13cd42e551a.png)

Model

![image](https://user-images.githubusercontent.com/86812576/172529625-36a34837-577f-4466-bf02-6cfd31e26e09.png)


Predict

![image](https://user-images.githubusercontent.com/86812576/172529771-c5401a6d-95b0-4014-9660-afe0100a61df.png)

# Rating predictions for Unwatched Movies
I took the UserId 1 sample. First, find out all the movies in the dataset. Then check the movies that have been watched by UserId 1. After that, also check the movies that have not been watched by UserId 1. Finally make predictions on the movies that have not been watched. 

Prediction result:

![image](https://user-images.githubusercontent.com/86812576/172531994-389bce8b-e293-447b-a7d6-aeff07ca8034.png)


# Movies Recommend
Movie recommendation for UserId = 1:

![image](https://user-images.githubusercontent.com/86812576/172532943-aff99e4e-a6a4-4aa7-9a84-98393b0b5864.png)

The table above is a prediction of the rating that will be given by UserId 1 based on the similarity of the user and his items.
