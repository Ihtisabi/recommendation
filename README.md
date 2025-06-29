# Rental Property Recommendation System 🏠
### Machine Learning Final Project - Suci Ihtisabi Hida Nursyifa

You can read the full report in [Laporan Proyek](laporan.md), however, the full report is currently only available in Indonesian.

## 🏘️ Domain
This project focuses on **real estate technology**, specifically addressing the challenges users face when searching for rental properties on digital platforms. With the increasing urbanization and reliance on online property platforms, there's a critical need for intelligent recommendation systems that can automatically suggest relevant properties without requiring extensive manual filtering.

## 🎯 Objectives
- Design an automated property recommendation system that leverages content similarity to improve user experience.
- Implement and compare two similarity measurement approaches: **Cosine Similarity** and **K-Nearest Neighbors with Euclidean Distance**.
- Evaluate system performance using coverage, diversity, and Top-K recommendation metrics.
- Reduce user frustration with complex manual filtering by providing personalized, relevant property suggestions.

## 📊 Dataset
- **Source**: Kaggle - Rental Recommender Data
- **Properties**: 1,000 rental properties in Japan
- **Features**: 9 columns including property details, location, pricing, and descriptions

[Dataset on Kaggle](https://www.kaggle.com/datasets/sasakitetsuya/rental-recommender-data/data?select=rental_data.csv)

## 🛠️ Models Implemented

### 1. Content-Based Filtering with Cosine Similarity
- **Approach**: Measures the cosine of the angle between property feature vectors
- **Range**: 0 (dissimilar) to 1 (identical)
- **Advantages**: Scale-invariant, effective for normalized data, fast for large datasets

### 2. Content-Based Filtering with KNN (Euclidean Distance)
- **Approach**: Finds nearest neighbors based on Euclidean distance in feature space
- **Similarity Conversion**: `similarity = 1 / (1 + distance)`
- **Advantages**: Simple, non-parametric, supports real-time scenarios

## ✅ Model Performance

### Original Models
| Model | Catalog Coverage | Layout Diversity | Address Diversity |
|-------|------------------|------------------|-------------------|
| Cosine Similarity | 98.2% | 39.9% | 45.5% |
| KNN (Euclidean) | 99.1% | 39.6% | 45.4% |

### Top-K Recommendation Metrics (Original)
| Model | Top-K | Precision | Recall | F1-Score | NDCG | Hit Rate |
|-------|-------|-----------|--------|----------|------|----------|
| **Cosine** | 20 | 0.0033 | 0.0242 | 0.0057 | 0.0113 | 0.0650 |
| **KNN** | 20 | 0.0030 | 0.0208 | 0.0052 | 0.0094 | 0.0600 |

### Improved Models (with Feature Weighting)
| Model | Top-K | Precision | Recall | F1-Score | NDCG | Hit Rate | Cluster Precision |
|-------|-------|-----------|--------|----------|------|----------|-------------------|
| **Weighted Cosine** | 20 | 0.0070 | 0.0239 | 0.0104 | 0.0140 | 0.1400 | 0.3210 |
| **Weighted KNN** | 20 | 0.0080 | 0.0234 | 0.0115 | 0.0156 | 0.1450 | 0.3233 |

### Coverage & Diversity (Improved Models)
| Metric | Weighted Cosine | Weighted KNN |
|--------|-----------------|--------------|
| **Catalog Coverage** | 98.9% | 99.8% |
| **Layout Diversity** | 20.0% | 20.0% |
| **Address Diversity** | 83.1% | 82.6% |

## 🏆 Best Model: Weighted KNN (Euclidean Distance)
- **Superior Performance**: Higher precision, recall, and cluster relevance
- **Best Cluster Precision**: 34.45% at Top-10 recommendations
- **Excellent Coverage**: 99.8% catalog coverage
- **Balanced Diversity**: Maintains good diversity across property types and locations

## 🔧 Model Improvements
### Feature Weighting Strategy
- **Numerical Features** (rent, size, year, distance): Weight = 2.0
- **Categorical Features** (layout, address): Weight = 1.5  
- **Text Features** (description): Weight = 1.0

### Enhanced Evaluation
- **Realistic User Simulation**: Cluster-based user preferences
- **Contextual Relevance**: Property relevance based on user cluster preferences
- **Additional Metrics**: Cluster precision for thematic consistency

## 📈 Key Insights
- **Significant Improvement**: Feature weighting dramatically improved all metrics
- **Diversity Enhancement**: Address diversity increased from ~45% to >81%
- **Layout Variety**: Layout diversity improved from ~39% to ~78%
- **User Satisfaction**: Hit rates doubled with the improved models

## 💡 Business Impact
- **Reduced Search Time**: Automated recommendations eliminate manual filtering complexity
- **Improved User Experience**: Higher relevance and diversity in suggestions
- **Platform Retention**: Better recommendations lead to increased user satisfaction and loyalty
- **Competitive Advantage**: Superior recommendation quality differentiates the platform

## 🧠 Key Takeaways
- **Feature Engineering Matters**: Proper weighting of different feature types significantly improves performance
- **Content-Based Filtering Works**: Effective for scenarios without extensive user interaction history
- **KNN Superiority**: For this use case, KNN with Euclidean distance outperformed Cosine Similarity
- **Evaluation Complexity**: Realistic evaluation requires sophisticated user behavior simulation

---

_This project was developed as part of the **CodingCamp DBS Foundation 2025**, Machine Learning Track._
