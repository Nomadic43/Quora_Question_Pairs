The Quora Question Pair Classification competition on Kaggle is a renowned challenge with a dataset containing 800,000 data points. The objective is to determine whether pairs of questions are duplicates, i.e., if they ask the same thing. I have utilized a subset of 50,000 data points for this project due to computing power limitations. The project involves sophisticated data preprocessing, feature engineering, and model tuning to classify question pairs as duplicates.

Dataset Description
The dataset consists of:

id: Unique identifier for each question pair.
qid1 and qid2: IDs of the two questions in the pair.
question1 and question2: The text of the two questions.
is_duplicate: A binary label indicating if the questions are duplicates (1) or not (0).
Approach
1. Exploratory Data Analysis (EDA)
Initial EDA was performed to understand the distribution and characteristics of the dataset. This step involved analyzing question lengths, distribution of duplicate labels, and identifying patterns.

2. Feature Engineering
To enhance model performance, we engineered several features:

Length Features:

Length of question1 and question2.
Number of words in question1 and question2.
Count Features: 3. Unique words in the combined questions. 4. Total number of words in both questions. 5. Ratio of common words to total words.

New Features: 6. Common words count divided by the minimum number of words in the two questions. 7. Common words count divided by the maximum number of words in the two questions. 8. Common stopwords count divided by the minimum number of stopwords in the two questions. 9. Common stopwords count divided by the maximum number of stopwords in the two questions. 10. Common tokens count divided by the minimum number of tokens in the two questions. 11. Common tokens count divided by the maximum number of tokens in the two questions. 12. Indicator if the last word of both questions is the same. 13. Indicator if the first word of both questions is the same. 14. Mean length of tokens in both questions. 15. Absolute difference in length between the two questions.

3. Bag of Words (BoW)
The Bag of Words model was used to convert text data into numerical vectors:

Preprocessing:

Tokenization: Splitting text into words.
Stopword Removal: Eliminating common words that do not add significant meaning.
Vectorization: Converting text into vectors based on word frequencies.
Binary vs. Normal BoW:

Binary BoW: Assigns 1 if a word is present, 0 otherwise.
Normal BoW: Assigns a count of word occurrences.
We applied BoW on both questions in each pair and used Random Forest (RF) for initial classification.

4. Advanced Techniques
LightGBM: LightGBM was chosen for its efficiency and performance. It handles large datasets well and provides accurate results with less training time compared to other algorithms.

Fuzzy Matching: Fuzzy matching techniques were used to find approximate matches between question pairs. This approach helps in identifying duplicates that may not have exact word matches but are contextually similar.

Dimensionality Reduction (t-SNE): t-SNE was used for visualizing high-dimensional data in 2D space. It helps in understanding the structure and distribution of data, making it easier to identify patterns and outliers.

5. Results and Future Work
Current Accuracy: After three iterations, we achieved an accuracy of 80% with our models. The best accuracy achieved in Kaggle's leaderboard is 83%. This suggests that while our approach is competitive, there is still room for improvement.

Future Enhancements: To further improve accuracy, we plan to:

Introduce additional features to capture more nuanced similarities between question pairs.
Increase the dataset size beyond 50,000 data points to enhance model performance and generalizability.
The addition of new features and expanding the dataset are expected to contribute significantly to achieving higher accuracy.

Conclusion
This project demonstrates the application of advanced machine learning techniques to a challenging text classification problem. By leveraging sophisticated methods like LightGBM, fuzzy matching, and dimensionality reduction, we aim to achieve high accuracy in identifying duplicate question pairs on Quora. Future work will focus on refining features and expanding the dataset to enhance model performance.
