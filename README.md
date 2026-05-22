AI/ML Engineer Pre-Work Assignment

Submitted to

Navgurukul
Project

ETA Prediction for Last-Mile Delivery Optimization
Submitted By

Dipanshu Kumar Singh
GitHub: www.github.com/Dnshusngh
LinkedIn: www.linkedin.com/in/dipanshu-kumar-singh-602998228
Email: dpnshusingh@gmail.com
Table of Contents
1.
Project Context
2.
Technical Implementation
3.
Architecture & Workflow
4.
Critical Code Walkthrough
5.
Data Flow Analysis
6.
Technical Decisions & Trade-offs
7.
Scaling Challenges & Mitigation
8.
Learning & Iteration
9.
Business Impact
10.
Conclusion
Section 1: Context (Brief)
Section 1: Context (Brief)
Project Description
This project focused on optimizing last-mile logistics operations using Artificial Intelligence (AI), Machine Learning (ML), and Generative AI (GenAI) techniques. The system was designed to improve delivery efficiency through ETA prediction, intelligent route optimization, delivery partner allocation, and spatio-temporal demand forecasting using large-scale logistics datasets containing courier trajectories, package information, road network data, traffic conditions, and operational delivery records.
The objective of the system was to reduce delivery delays, optimize courier allocation, minimize operational costs, improve ETA accuracy, and enhance customer satisfaction through scalable and data-driven logistics intelligence.
The project involved the complete machine learning lifecycle:
•
Data Collection
•
Data Cleaning & Preprocessing
•
Exploratory Data Analysis
•
Feature Engineering
•
Model Training & Evaluation
•
Pipeline Development
•
Dashboarding & Monitoring
•
Deployment Planning
Primary Technical Constraints
•
The project involved multiple real-world technical constraints:
Constraint
Impact
Large-scale datasets (10M+ records)
Increased preprocessing and training complexity
Missing GPS coordinates
Reduced geospatial reliability
Traffic variability
Dynamic ETA fluctuations
Temporal dependencies
Risk of data leakage during training
High-cardinality courier/location data
Increased feature engineering complexity
Real-time prediction latency
Operational deployment challenges
Multi-source data integration
Data synchronization issues
Geospatial inconsistencies
Route mapping complexity
Section 2: Technical Implementation (Detailed)
System Architecture
┌──────────────────────────┐
│ Logistics Datasets │
│--------------------------│
│ • Pickup Data │
│ • Delivery Data │
│ • Road Network Data │
│ • Courier Trajectories │
└────────────┬─────────────┘
│
▼
┌──────────────────────────┐
│ Data Cleaning & │
│ Preprocessing Pipeline │
│--------------------------│
│ • Missing Value Handling │
│ • Timestamp Conversion │
│ • Outlier Removal │
│ • Data Standardization │
└────────────┬─────────────┘
│
▼
┌──────────────────────────┐
│ Feature Engineering │
│--------------------------│
│ • Distance Features │
│ • Time Features │
│ • Traffic Features │
│ • Courier Metrics │
└────────────┬─────────────┘
│
▼
┌──────────────────────────┐
│ Machine Learning Models │
│--------------------------│
│ • XGBoost │
│ • Random Forest │
│ • LightGBM │
│ • KNN │
│ • Neural Networks │
└────────────┬─────────────┘
│
▼
┌──────────────────────────┐
│ Prediction Layer │
│--------------------------│
│ • ETA Prediction │
│ • Route Prediction │
│ • Demand Forecasting │
└────────────┬─────────────┘
│
▼
┌──────────────────────────┐
│ Dashboards & APIs │
│--------------------------│
│ • Power BI Monitoring │
│ • Operational Analytics │
│ • Deployment APIs │
└──────────────────────────┘
Architecture Explanation
The system processes large-scale logistics datasets through preprocessing and feature engineering pipelines before training machine learning models for ETA prediction, route optimization, and delivery intelligence. The outputs are integrated into dashboards and deployment pipelines to support operational decision-making, delivery performance monitoring, and resource optimization.
Datasets Used
Dataset
Purpose
LaDe-P Pickup Dataset
Pickup task analysis
LaDe-D Delivery Dataset
Delivery duration prediction
Road Network Dataset
Route & traffic intelligence
Courier Trajectory Dataset
GPS movement analysis
Data Preprocessing Pipeline
The preprocessing stage focused on improving data quality and ensuring model readiness.
Preprocessing Operations
1. Missing Value Handling
•
Removed records with critical timestamp gaps
•
Imputed missing coordinates using regional averages
•
Replaced missing categorical values with placeholders
2. Duplicate Removal
Used package_id as a unique identifier to remove duplicate delivery records.
3. Timestamp Standardization
Converted delivery timestamps into datetime format for temporal analysis.
4. Outlier Detection
Applied:
•
IQR method
•
Z-score filtering
for abnormal delivery durations and unrealistic geospatial records.
5. Feature Normalization
Used:
•
StandardScaler
•
MinMaxScaler
for improving model convergence.
Feature Engineering
Feature engineering was one of the most critical components of the project.
Time-Based Features
•
Hour of delivery
•
Day of week
•
Weekend indicator
•
Rush-hour indicator
•
Task duration
Geospatial Features
•
Distance calculations
•
Route density
•
Traffic congestion mapping
•
GPS normalization
Operational Features
•
Package volume per courier
•
Delivery density per region
•
Courier performance metrics
•
Delivery delay frequency




Machine Learning Models Implemented
Model
Purpose
Linear Regression
Baseline ETA prediction
Decision Tree
Interpretable logistics rules
Random Forest
Ensemble ETA prediction
Gradient Boosting
Nonlinear delivery modeling
XGBoost
High-accuracy ETA prediction
KNN
Delivery classification
SVM
Delay classification
MLP Neural Network
Complex nonlinear prediction
Graph Neural Networks
Route optimization
ST-GCN
Demand forecasting

Model Performance Summary
Model
Key Advantage
Random Forest
Robust against noisy logistics data
XGBoost
Best overall ETA performance
Neural Networks
Strong nonlinear learning
KNN
Effective for localized classification
Graph Models
Strong route intelligence

Critical Function Walkthrough
Distance Calculation Function
Function Explanation
This function calculates the approximate geospatial distance between courier acceptance and pickup locations using GPS coordinates. The generated distance feature became one of the most influential variables for ETA prediction because delivery duration strongly correlated with route distance, traffic congestion, and regional density.
The function played a significant role in:
•
ETA estimation
•
Route optimization
•
Courier workload analysis
•
Traffic-aware delivery modeling
Machine Learning Pipeline System
The project implemented a modular ML pipeline system integrating:
•
Data preprocessing
•
Encoding
•
Scaling
•
Feature engineering
•
Model training
•
Evaluation
•
Hyperparameter tuning

Why Pipelines Were Important
Benefit Explanation
Reproducibility Consistent preprocessing across experiments
Scalability Easier retraining on new data
Reduced Data Leakage Same transformations applied to train/test data
Deployment Readiness Entire workflow packaged into reusable objects
Faster Experimentation Streamlined model comparison
Section 3: Technical Decisions (Core)
Decision 1 — Using XGBoost for ETA Prediction
Decision
Used XGBoost and Gradient Boosting models for ETA prediction.
Alternatives Considered
•
Linear Regression
•
Decision Trees
•
Random Forest
•
KNN
Trade-offs
Advantage
Limitation
Excellent nonlinear learning
Higher training complexity
Strong handling of structured logistics data
Increased tuning requirements
Better feature interaction learning
Longer experimentation cycles
Improved accuracy
Higher computational cost
Outcome
XGBoost achieved the best ETA prediction performance and improved generalization on large logistics datasets. The model successfully captured traffic-related variations, delivery density patterns, and temporal dependencies.
Decision 2 — Building a Pipeline-Based ML Architecture
Decision
Implemented a modular machine learning pipeline system integrating preprocessing, feature engineering, model training, and evaluation.
Alternatives Considered
•
Manual preprocessing workflows
•
Separate transformation scripts
•
Notebook-only experimentation
Trade-offs
Advantage
Limitation
Reduced data leakage
Initial setup complexity
Easier deployment
More architectural planning
Better reproducibility
Required modular restructuring
Scalable retraining
Higher engineering effort
Outcome
The pipeline architecture significantly improved consistency, scalability, and deployment readiness. It streamlined model experimentation and enabled reusable production-style workflows.
Decision 3 — Feature Engineering Over Pure Deep Learning
Decision
Focused heavily on feature engineering instead of relying only on deep learning models.
Alternatives Considered
•
LSTM-only architecture
•
End-to-end neural networks
•
Minimal feature engineering workflows
Trade-offs
Advantage
Limitation
Better interpretability
Manual feature creation effort
Faster experimentation
Feature maintenance overhead
Lower compute requirements
Domain dependency
Easier debugging
Less automated learning
Outcome
Feature engineering significantly improved model stability and operational interpretability while reducing computational requirements compared to heavy deep learning architectures.
Scaling Bottleneck & Mitigation Strategy
Scaling Bottleneck
Processing millions of courier trajectory records and delivery logs increased preprocessing latency and slowed model inference during peak workloads.
The biggest operational challenges included:
•
Large geospatial datasets
•
High-cardinality features
•
Repeated preprocessing overhead
•
Real-time ETA computation
•
Temporal synchronization complexity
Mitigation Strategy
To address scalability challenges:
•
Optimized preprocessing pipelines
•
Reduced redundant transformations
•
Used modular pipeline systems
•
Applied feature selection techniques
•
Planned batch-based feature caching
•
Structured reusable transformation workflows
Future improvements would include:
•
Kafka streaming pipelines
•
Online inference systems
•
Feature stores
•
Distributed processing systems
•
Real-time retraining workflows
Section 4: Learning & Iteration (Concise)
Technical Mistake & Learning
Mistake
Initially, random train-test splitting introduced temporal leakage into the ETA prediction workflow, producing unrealistically optimistic evaluation metrics.
Learning
After identifying the issue, time-aware validation strategies were implemented to preserve chronological order during model training and evaluation.
This improved:
•
model reliability
•
production realism
•
operational generalization
•
deployment readiness
The experience reinforced the importance of understanding temporal dependencies in real-world logistics systems.
What I Would Do Differently Today
If redesigning the project today, I would:
•
Implement real-time streaming pipelines
•
Use geospatial embeddings
•
Introduce online learning systems
•
Add model monitoring dashboards
•
Build distributed training workflows
•
Integrate MLOps practices
•
Add automated drift detection
•
Deploy scalable inference APIs
I would also explore:
•
Graph Neural Networks for route optimization
•
Reinforcement Learning for courier allocation
•
Real-time traffic simulation
•
Feature stores for low-latency prediction
Business Impact
Operational Improvements
Improvement Area
Business Benefit
ETA Prediction
Reduced customer complaints
Route Optimization
Faster deliveries
Demand Forecasting
Better courier allocation
Delivery Intelligence
Improved operational efficiency
Traffic-Aware Routing
Reduced delivery delays
Resource Optimization
Lower operational costs
AI & GenAI Integration
AI Use Cases
•
Dynamic route optimization
•
ETA prediction
•
Demand forecasting
•
Delivery anomaly detection
•
Traffic-aware courier allocation
Generative AI Use Cases
•
Synthetic traffic simulation
•
Alternative route generation
•
Conversational logistics support
•
Demand fluctuation simulation
•
Delivery support assistants
Conclusion
This project demonstrates the development of a scalable AI & GenAI-based logistics optimization system integrating ETA prediction, route intelligence, demand forecasting, feature engineering pipelines, and operational analytics.
The system successfully combines:
•
Machine Learning
•
Geospatial Analytics
•
Temporal Forecasting
•
Operational Optimization
•
Pipeline Engineering
•
Deployment Readiness
•
Business Intelligence
Through large-scale logistics datasets and production-oriented workflows, the project highlights practical AI/ML engineering skills focused on solving real-world operational problems.
The experience strengthened my understanding of:
•
scalable ML systems
•
logistics intelligence
•
pipeline architecture
•
temporal modeling
•
deployment-oriented engineering
•
AI-driven operational optimization
This project aligns strongly with AI/ML engineering responsibilities involving applied machine learning, operational AI systems, and scalable data-driven decision-making.
I created a complete professional AI/ML Engineer pre-work report for your Navgurukul submission using:
•
your uploaded documentation
•
deep technical analysis
•
architecture workflows
•
ML pipeline explanations
•
code walkthroughs
•
technical decisions & trade-offs
•
scaling bottlenecks
•
learning iterations
•
AI & GenAI integration
•
business impact analysis
•
diagrams and structured engineering explanations
The report is structured exactly according to Navgurukul’s Option 1 requirements and positioned at an AI/ML Engineer level rather than a basic internship report.
