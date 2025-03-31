# **Fashion Recommendation Project**

## **Team Members**
- **Norah Almubarak**
- **Lama Almazyad**
- **Bayader Aljondeby**
- **Yara Aljasir**
- **Liana Almashharawi**

---

## **Motivation**
The fashion industry is a rapidly growing sector where **visual representation** of products plays a crucial role in consumer decision-making. 

We chose this dataset because:
- The fashion industry **heavily relies on AI-driven solutions** like **image classification and recommendation systems**.
- This dataset provides a **diverse set of fashion product images with metadata**, making it **ideal for machine learning models** for fashion analytics, classification, and visual search.

---

## **Dataset Overview**
The **Fashion Product Images Dataset** consists of **images of fashion products with metadata**, including:
- **Product categories**
- **Gender specifications**
- **Seasonality & Other attributes**

### **Key Features**
**Product Images**: A large collection of fashion product images.  
**Metadata**: Each image is labeled with attributes such as **category, sub-category, gender, season, and usage**.  
**Structured Data**: Includes **CSV files** containing **image paths and metadata**.  
**Potential Use Cases**: **Image classification, recommendation systems, and fashion analytics**.  

---

## **Dataset Source**
The dataset is available on Kaggle:  
**[Fashion Product Images Dataset](https://www.kaggle.com/datasets/paramaggarwal/fashion-product-images-dataset)**

---

# **Data Analysis & Preprocessing**
The **Jupyter Notebook** in this repository includes the following steps:

### **Data Preprocessing Pipeline**
**Data Loading & Exploration**  
**Data Visualization** (Category distribution, gender-wise split, etc.)  
**Missing Value Analysis & Handling**  
**Image Resizing & Normalization**  

---

# **Supervised Learning: Fashion Product Classification & Recommendations**
## **Goal**
We trained **supervised learning models** to **classify and recommend fashion products**.

## Algorithm Selection Justification
In developing our fashion recommendation system, which processes images to predict subcategories and recommend similar items, we have selected two supervised machine learning algorithms: Support Vector Machine (SVM) Classifier and Multi-layer Perceptron (MLP) Neural Network.
- *Support Vector Machine (SVM) Classifier*
SVM is chosen for its effectiveness in image classification, particularly with high-dimensional data. It finds an optimal hyperplane to separate different classes, making it well-suited for distinguishing fashion subcategories based on image features. Its robustness against overfitting is also valuable for handling diverse fashion datasets [1].
- *Multi-layer Perceptron (MLP) Neural Network*
MLP is selected due to its ability to model complex non-linear relationships, which is essential for image-based classification. Its flexibility allows it to learn intricate patterns within image data, enabling accurate subcategory predictions. This makes it a strong candidate for improving recommendation accuracy in our system[2].

## **Steps in Supervised Learning**

1. **Feature Extraction with ResNet50**
   
   Used ResNet50, a Convolutional Neural Network (CNN) pre-trained on ImageNet.
   
   Extracted deep features from images without modifying ResNet50’s weights.
   
   Flattened the extracted feature vectors for classifier input.
   
   Note: ResNet50 model was trained with supervised learning on ImageNet.

2. **Model Selection**
   
   Selected Support Vector Machine (SVM) and MLP (Neural Network) as classifiers.
   
   These models require labeled data to learn decision boundaries.

3. **Model Training**
   
   Trained both SVM and MLP using labeled extracted features.
   
   Optimized hyperparameters to improve classification accuracy.

4. **Model Evaluation**
   
   Evaluated classification performance on the test dataset (with known labels).
   
   Metrics used:
   
   - Accuracy
   - Precision, Recall, F1-score
   - Confusion Matrix Analysis

5. **Fashion Product Recommendation**
   
   Used classification results to recommend similar products.
   
   Analyzed feature embeddings to suggest visually similar items from the same predicted category.

## **Model Performance Comparison**

1. **Support Vector Machine (SVM)**
   
   - **Accuracy:** 97.07%
   - **Classification Report:**
     
     High precision and recall across categories.

2. **Multi-Layer Perceptron (MLP Classifier - Neural Network)**
   
   - **Accuracy:** 79.24%
   - **Comparison:**
     
     SVM outperformed MLP in accuracy.
# **Unsupervised Learning: Fashion Product Classification & Recommendations**

## **Goal**
To group fashion products based on visual similarity **without using labeled data**, and to use these clusters to make recommendations.

## **Steps in Unsupervised Learning**

1. **Feature Extraction with ResNet50**

   Used **ResNet50**, a deep convolutional neural network pre-trained on ImageNet, for feature extraction.

   - Images were resized and preprocessed.
   - Extracted high-dimensional deep features from the 'avg_pool' layer.
   - Flattened features into 2048-length vectors per image.

2. **Dimensionality Reduction with PCA**

   - Applied **Principal Component Analysis (PCA)** to reduce feature vector dimensions from 2048 to 100.
   - Helped improve clustering performance and visualization.
   - Maintained variance while simplifying the feature space.

3. **Clustering with K-Means**

   - Implemented **K-Means Clustering** on the reduced feature set.
   - Selected an optimal number of clusters (**K=4**) based on visual inspection and experimentation.
   - Each image was assigned a cluster label representing visually similar groups.

4. **Cluster Visualization**

   - Displayed sample images from each cluster to validate visual similarity.
   - Used scatter plots of PCA components with color-coded cluster labels for analysis.

5. **Fashion Product Recommendation**

   - For a selected image, retrieved visually similar products from the **same cluster**.
   - Recommendations were based on proximity in PCA-reduced feature space.
   - Achieved visually coherent and relevant suggestions without relying on predefined labels.

## Generative AI – LLaMA API Integration

In this phase, Generative AI was integrated using the LLaMA model through the Together API. The objective was to enhance the recommendation system by generating descriptive explanations based on the input image.

The system predicts the cluster of the input image, finds the most visually similar items within that cluster, and then uses Generative AI to explain the recommendations.

Two different prompt templates were applied:
- A **formal, informative template** that explains item similarities in a structured way
- A **conversational stylist template** that presents the explanation in a friendly, user-oriented tone

Both outputs are displayed side by side, and a justification is provided for which template better fits the system's purpose.


## References
- (1). D. D. A. M. S. Easy, “Understanding SVMs’: For Image Classification,” Medium, Aug. 10, 2018. https://medium.com/@dataturks/understanding-svms-for-image-classification-cf4f01232700
- (2). S. Biswas, "An Algorithm for Training Multilayer Perceptron (MLP) for Image Reconstruction Using Neural Network Without Overfitting," ResearchGate, Nov. 2016. [Online].https://www.researchgate.net/publication/310327188_An_Algorithm_For_Training_Multilayer_Perceptron_MLP_For_Image_Reconstruction_Using_Neural_Network_Without_Overfitting.
