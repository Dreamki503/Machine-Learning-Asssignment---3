# Machine-Learning-Asssignment - 3

## JOB CLASSIFICATION MODEL
Used an **SVM mode**l on the dataset to categorize the descriptions into different categories based on their content.

Reasons for low accuracy:
1. Limited Training Data – 325 job descriptions are not enough for the model to learn diverse job categories.
2. Overlapping Categories – Some job descriptions may contain similar terms across different categories, causing misclassification.
3. Sparse Features from Text – The text embeddings (SPLADE) may not fully capture the contextual meaning of job descriptions.
4. Imbalanced Data – If some categories have significantly more samples than others, the model may bias towards dominant categories.

Ways to Improve Accuracy in the Future:
1. Expand Dataset – Collect more job descriptions to improve generalization. A dataset of 1,000+ samples per category would be more effective.
2. Use Advanced NLP Models – Instead of SPLADE, try BERT-based models (e.g., sentence-transformers or distilBERT) to get better text representations.
3. Feature Engineering – Extract key skills, required qualifications, and job titles separately to improve classification signals.
4. Handle Imbalanced Data – If some job categories have fewer samples, use oversampling (SMOTE) or class-weight balancing in SVM.
5. Try a Different Model – While SVM works well on small datasets, trying a Random Forest or fine-tuned BERT classifier could yield better results.

---

## JOB RECOMMENDATION MODEL
### 1️. Content-Based Filtering (CBF) Approach
Extracted features from job descriptions using SPLADE embeddings.
Used cosine similarity to compare the user's profile (Work experience, Education, Skills) from the dataset with job descriptions.
Recommended jobs that are most similar to what the user's profile.

Advantages:
1. Works well when user data is limited (e.g., first-time users).
2. Ensures recommendations are personalized to the user's profile.
3. Doesn’t rely on other users' behavior, making it independent of past interactions.

Possible Improvements: Use NLP to extract skills, roles, and industries from user input for better matching.

### 2. Collaborative-Based Filtering (CF)
Clustered jobs using K-Means to identify groups of similar jobs.
Used KNN to find the closest job clusters for the user.
Recommended jobs from the nearest clusters rather than comparing all jobs.

Advantages:
1. Captures patterns from multiple users rather than just individual preferences.
2. Helps users discover new job categories they might not have searched for.
3. Works well for large datasets where explicit user-job similarities aren’t available.

Possible Imporvements: 
1. Use a Hybrid Model (CBF + CF). Combine content-based filtering (CBF) (job description similarities) with collaborative filtering (CF) (user-job interactions).
2. This solves the cold-start problem (when a new user or job has no interaction history).
Example: Use CBF for new users and switch to CF once enough interactions exist.
