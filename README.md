# customer-lifetime-value-and-churn-modeling
## Problem Statement

For customer-facing businesses, long-term growth depends less on acquisition volume and more on retaining high-value customers and allocating resources efficiently across the customer base.

The core challenge is that customers exhibit highly heterogeneous behavior. Treating all customers uniformly leads to inefficient spend, increased churn, and missed opportunities to grow lifetime value.

This project builds an end-to-end customer analytics system to:
- Segment customers based on behavioral patterns  
- Predict customer lifetime value (CLV)  
- Identify customers at risk of churn  
- Anticipate future purchasing behavior  

The goal is to support data-driven decisions around retention strategy, targeted engagement, and revenue planning.
## Why This Is a Data Science Problem

Customer behavior is complex, non-linear, and highly imbalanced across a population. Simple rules or aggregate metrics are insufficient to capture differences in customer value, churn risk, and future purchasing patterns.

Effective decision-making requires:
- Learning latent structure in behavioral data rather than relying on static labels  
- Modeling future outcomes such as churn and lifetime value using historical signals  
- Balancing interpretability with predictive performance  
- Translating model outputs into actionable business decisions  

This project frames customer analytics as a data science problem by combining unsupervised learning for segmentation with supervised machine learning for prediction. Together, these techniques enable proactive retention strategies, targeted investment, and improved revenue forecasting rather than reactive, descriptive analysis.
## Dataset Overview & Scope

The analysis is based on a large-scale transactional dataset from an online retail business, containing customer purchase activity over a two-year period.

**Dataset characteristics:**
- Source: Online Retail II dataset (public, reproducible)  
- Time range: December 2009 – December 2011  
- Observations: ~1.07 million transactions  
- Unit of analysis: Customer-level and transaction-level records  

**Core fields include:**
- Customer identifier  
- Invoice date and order details  
- Quantity and unit price  
- Derived revenue per transaction  

**Scope decisions:**
- Analysis is conducted at the customer level for segmentation and prediction  
- Customers with insufficient transactional history are excluded to reduce noise  
- Monetary value is treated as a proxy for lifetime value due to the absence of explicit cost data  

These decisions prioritize behavioral signal, scalability, and business relevance over exhaustive feature coverage.
## Methodology

The project implements an end-to-end customer analytics pipeline that combines behavioral segmentation with predictive modeling to support retention and revenue optimization decisions.

### 4.1 Feature Engineering & Behavioral Metrics

Raw transaction data was transformed into customer-level behavioral features capturing recency, frequency, and monetary value (RFM). These features summarize how recently customers interacted, how often they purchased, and how much value they generated.

Additional derived metrics were created to support prediction tasks, including customer tenure, purchase intervals, and aggregated spending patterns.

### 4.2 Customer Segmentation via Unsupervised Learning

RFM features were used to segment customers into behavioral groups using K-Means clustering. This approach groups customers based on observed behavior rather than predefined business rules.

Segmentation enables:
- Identification of high-value customers critical to retention  
- Differentiation between occasional, regular, and loyal buyers  
- Targeted downstream modeling and intervention strategies  

Clusters were validated using distributional analysis and visual inspection to ensure meaningful separation.

### 4.3 Customer Lifetime Value Prediction

Customer Lifetime Value (CLV) was modeled by predicting future revenue over a fixed horizon using historical behavioral features.

The modeling process included:
- Defining training and prediction windows  
- Feature selection and transformation  
- Supervised learning to estimate future customer value  

Model performance was evaluated on a holdout set to assess generalization.

### 4.4 Churn Prediction

Churn was formulated as a binary classification problem to identify customers at risk of inactivity.

Feature engineering included behavioral aggregates, encoded categorical variables, and segment-level indicators. An ensemble-based classifier was used to capture non-linear relationships between features and churn outcomes.

The resulting model supports proactive retention by flagging high-risk customers before churn occurs.

### 4.5 Purchase Timing & Sales Forecasting

To anticipate future demand, the project includes models to estimate time-to-next-purchase at the customer level and aggregate sales forecasts over time.

These components enable planning decisions related to marketing cadence, inventory management, and revenue expectations.
## Key Results & Business Insights

- **Customer value is highly concentrated**  
A small subset of customers accounts for a disproportionate share of total revenue, reinforcing the importance of targeted retention rather than uniform engagement.

- **Behavioral segmentation improves signal quality**  
RFM-based clustering reveals clear separation between low-, mid-, and high-value customers, enabling more precise downstream prediction and intervention strategies.

- **Lifetime value is predictable from early behavior**  
Historical recency, frequency, and monetary patterns provide strong signal for forecasting future customer value over a fixed horizon, supporting differentiated investment decisions.

- **Churn risk can be identified proactively**  
Supervised churn models flag customers likely to disengage before inactivity occurs, enabling earlier and more cost-effective retention actions.

- **Purchase timing improves planning accuracy**  
Estimating time-to-next-purchase and aggregating forecasts supports more reliable revenue planning compared to relying on historical averages alone.

Together, these results demonstrate how combining segmentation with predictive modeling enables more efficient allocation of retention and growth resources.
## Decision Metrics & Evaluation

Model evaluation focused on decision usefulness rather than isolated technical scores.

Key metrics include:
- **Customer Lifetime Value prediction accuracy** evaluated on a holdout set to assess generalization to unseen customers  
- **Churn classification performance** measured using standard classification metrics (precision, recall, and overall accuracy) to balance false positives and false negatives  
- **Segment-level lift** comparing retention and value concentration across behavioral clusters  
- **Forecast error** for purchase timing and sales predictions to assess planning reliability  

These metrics are used to answer operational questions such as:
- Which customers should be prioritized for retention investment?
- How early can churn risk be detected with acceptable confidence?
- How reliably can future revenue be estimated for planning purposes?

The emphasis is on enabling better decisions rather than maximizing any single model metric in isolation.
