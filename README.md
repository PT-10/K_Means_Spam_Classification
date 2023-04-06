# K_Means_Spam_Classification</br>

Data Loading and Pre-processing:</br>
We first load the data from the CSV file and perform the necessary pre-processing steps, including dropping null comments and irrelevant columns, cleaning the comments data using NLTK, and converting the categorical data to numerical data using label encoding. The final pre-processed dataset consists of the "User", "Video Title", and "Comment Actual" columns.
</br>
- BERT Encoding:</br>
We use PyTorch's BERT model and tokenizer to convert the pre-processed text comments into tensors. The BERT tokenizer tokenizes the comments, adds special tokens like [CLS], and converts the tokens to their corresponding token IDs. The resulting tensor is then fed into the BERT model, which produces a contextualized embedding for each token. We use the [CLS] token embedding as the representation for the entire comment.
</br>
- Dimensionality Reduction with SVD and PCA:</br>
The high-dimensional BERT embeddings for each comment can be difficult to work with. So, we use SVD to reduce the dimensionality of the embeddings while preserving the most important features. We select the first component of the S matrix obtained during SVD. The dataframe now consists of two categorical columns and a column for comments consisting of the representative singular values. We now apply PCA on the data with the aim of using two features of the PCA dataset for improved clustering.
</br>
- 2D and 3D Plotting for K-Means:</br>
To visualize the clustering results, we scatter plot the reduced - dimensional data in 2D and 3D space. In the 3D plot, we use different colours for each cluster, with 4 layers representing each of the 4 YouTubers in the dataset.
</br>
- Clustering with K-Means:</br>
We use K-Means clustering to group the comments into clusters based on their reduced-dimensional embeddings. Based on prior knowledge, the value of k is set to 2.
Experimenting with different values of k, evaluating via Elbow Method, SSE, Silhouette score also shows that k = 2 is the optimal value.</br>
- Hierarchical Clustering:
To further compare the clusters formed, we perform hierarchical clustering on the reduced-dimensional embeddings of the comments. The resulting scatter plots of both the method show similar plots.</br>
- Evaluation:</br>
We evaluate the performance of the clustering pipeline using metrics such as SSE and Silhouette Score. The SSE score for k = 2 is 722195468.8088534 while the Silhoutte Score is 0.65 which is greater than 0.6 indicating proper cluster formation.
We also manually inspect a sample of the comments in each cluster to ensure that they are semantically similar and represent a coherent theme.
- Overall, our pipeline takes raw text comments as input, pre-processes and converts them to numerical format using BERT embeddings, performs dimensionality reduction using SVD, PCA, and finally clusters the comments using K-Means and hierarchical clustering to identify and group spam comments.
