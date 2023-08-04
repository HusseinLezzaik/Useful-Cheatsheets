## Interviews Q&A
1) How would you deal with an Imbalanced Dataset?
- Don't use "accuracy" on an Imbalanced dataset. Acc is not a good performance metric for these problems. Instead, use Precision Recall, F-scoure, Confusion Matrix, ROC  curves
- Collect more data in order to balance your data
- Augment the dataset with synthetic data
- Resample your data
- Use "Cost-Sensitivity". Adding a cost-sensitive layer to your model is a great way to optimize your predictions. This will help
to weigh the results of a model trained on imbalanced data
- Check different algorithms. Decision trees are excellent at handling imbalanced classes. They're good with dealing with unstructured data.
2) How would you fix Overfitting?
- Simplify the model (fewer params)
- Simplify the training data (fewer attributes)
- Constrain the Model (Regularization)
- Use Cross-Validation
- Use Early-Stopping
- Build an Ensemble
- Gather more Data
3) How would you fix Underfitting?
- More complex model (more params)
- Increase nb. of features
- Feature engineers should help
- Un-constrain the Model (No Regularization)
- Reduce Noise on the Data
- Train for Longer
4) How do you chosse a ML model?
- Performance (Precision, Recall, Accuracy, F1-score)
- Explainability
- Complexity
- Dataset Size
- Dimensionality
- Training Time & Cost
- Inference Time
5) When to use ML:
- Patterns: there must be patterns to learn
- Complex: the patterns are complex
- Existing data: it's possible to collect
- Predictive: it's a predictive problem .. what would the answer/solution look like
6) Choosing ML Models - Start with these and then Iterate:
- Most models can perform well without even fine-tuning, and you can then push it's performance
- Tabular: XGBoost/LightGBM/RF
- Time series: XGBoost/LightGBM/RF
- Image: ResNet18/EffNet
- Text: DistilRoBERTa
- Audio: ResNet/EffNet
7) Top used ML algos for tabular data problems:
- XGBoost
- HistGradient Boosting
- Logistic/Ridge Regression
- LightGBM
- MLP
8) Explain the difference between Bias and Variance trade-off?
- Bias: underfitting, hard to generalize, simplistic assumptions
- Variance: overfitting, sensitive to degrees of variation in data
9) How do you optimize neural networks:
- Model Pruning
- Knowledge Distillation
- Model Compression
- Quantization
- OpenVINO
- TensorRT
10) Favorite ML Algorithm?
- Random Forest
- Can handle classification and regression tasks with all kinds of input features
- minimal preprocessing needed
11) K-Nearest Neighbors - KNN:
- Supervised Classification algorithm
- You need labeled data and want to classify an unlabeled pt. into (thus the nearest neighbor)
12) K-means Clustering:
- Unsupervised Clustering algorithm
- Unlabeled data, and a threshold
- Computes the mean of the distance b/w pts
13) Receiver Operating Characteristics - ROC:
- Contrast b/w TP vs. FP at various thresholds
14) Define Precision and Recall:
- Recall: known as the TP rate, the amount of positives your model claims compared to the actual nb. of positives there are throughout the data
- Precision: known as positive predictive value, and it's a measure of the amount of accurate positives your model claims compared to the nb. of positives it actually claims
15) What's the F1 score? How woud you use it?
- F1 score is measure of models performane
- F1 is a weighted average of the precision and recall of a model
- F1 = 2 x (PxR)/(P+R)
16) Regularization:
- Tuning param to prevent overfitting
- L1/L2 reg
- To stabilize estimates especially when there's collinearity in the data
17) L1 vs. L2:
- L1: binary/sparse, many variables assigned a 1/0 in weighting, Laplacian prior
- L2: tends to spread error among all terms, Gaussian prior
18) Type I vs. Type II error:
- Type I: false positive, claiming something has happened when it hasn't, telling a man he is pregnant
- Type I: false negative, claiming nothing is happening when something is, tell a pregnant woman she isn't carrying a baby
