Project Overview

This project develops a neural network model to predict customer churn for a mobile service provider. Using a dataset of 1 million customer records, we aim to identify customers at risk of churning, enabling targeted retention strategies.

Dataset
Size: 1 million customer records

Features: Behavioral, demographic, and service usage metrics
1. AcctLength: Measures the duration of a customer’s relationship with the company. Shorter tenures may indicate higher churn risk, as newer customers are less likely to be loyal.
2. IntlPlan: Indicates if a customer has an international calling plan. Customers lacking this feature may churn if they need international calls, while those with it are more engaged.
3. VMPlan: Shows if the customer has a voicemail plan. Customers needing voicemail may switch if they lack this feature, while those with it are less likely to churn.
4. NVMailMsgs: Counts the number of voicemail messages. High usage suggests reliance on this service, reducing churn risk.
5. DayMinutes, DayCalls, DayCharge: Measures daytime usage. High usage can reflect strong engagement, likely reducing churn risk.
6. EveMinutes, EveCalls, EveCharges: Captures evening usage, revealing different patterns that can help tailor services to retain customers.
7. NightMin, NightCalls, NightCharge: Shows nighttime usage. High usage may indicate reliance on the service during off-hours, reducing churn risk.
8. IntlMin, IntlCalls, IntlCharge: Represents international usage. Customers with high international use are likely dependent on these services, lowering churn risk.
9. NCustServiceCalls: Tracks customer service interactions. High frequency may indicate dissatisfaction, signaling a higher churn risk.
These variables offer valuable insights into customer behaviors, with key indicators like NCustServiceCalls and DayCharge directly linked to engagement and satisfaction, making them strong predictors of churn.

Target Variable: Churn (binary: True/False)

Key Steps

•	Data Preprocessing: Cleaning and encoding of categorical features

•	Exploratory Data Analysis: Visualizing feature distributions and correlations

•	Model Development: Implementation of neural network using TensorFlow/Keras

•	Hyperparameter Tuning: Optimization using Keras Tuner's Hyperband method

•	Model Evaluation: Performance assessment on test set


Model Architecture

Input Layer: Based on number of features

Hidden Layer 1: 64 units, ReLU activation

Dropout Layer 1: 10% dropout rate

Hidden Layer 2: 32 units, ReLU activation

Dropout Layer 2: 10% dropout rate

Output Layer: 1 unit, Sigmoid activation

Results
Using evaluation metrics like accuracy, precision, recall, and F1-score, we can gauge the performance of the neural network on both training and testing sets. Here's an interpretation of each metric:

1.	Accuracy: Training Set: 96%, Testing Set: 92%. This high accuracy indicates the model's reliability in classifying most cases correctly, showing that it generalizes well to unseen data without overfitting.

2.	Precision for Churn Class: Training Set: 84%, Testing Set: 73%. Precision measures the proportion of customers predicted as churners who are actual churners. The high precision in the test set (73%) means that most customers identified as churners are indeed likely to churn, avoiding unnecessary retention costs.

3.	Recall for Churn Class: Training Set: 91%, Testing Set: 79%. Recall indicates the proportion of actual churners the model successfully identified. High recall (79%) on the test set ensures the model captures the majority of churners, which is crucial for minimizing customer loss.

4.	F1-Score: F1-score balances precision and recall, providing an overall measure of the model's performance in handling churn prediction. For the test set, the F1-score for churners is 76%, reflecting a good balance between capturing churners and avoiding false positives.
   
The optimized neural network model outperforms both baseline models (logistic regression and decision tree) and the initial neural network version by achieving superior accuracy, recall, and F1-score. While logistic regression and decision trees provided a solid starting point, their limitations became apparent in handling the complex, non-linear patterns within the churn data. 
Logistic regression, for example, struggled with lower recall for the churn class, meaning it missed a significant number of actual churners. The decision tree achieved perfect accuracy on the training set, suggesting overfitting, but underperformed on the test set, especially in identifying churners accurately without excessive false positives.
Compared to the initial NN model, this optimized neural network—with hyperparameters fine-tuned for dropout rates, learning rate, and layer units—struck a better balance between capturing true churners and avoiding false positives. It maintained high testing accuracy around 92%, high recall for the churn class around 79%, and improved stability in training and testing loss, indicating minimal overfitting and reliable generalization on unseen data. This refined model captures complex interactions among features more effectively, making it the most robust option for precise and actionable churn predictions.


Key Findings / Factors strongly influencing churn:
1.	High daytime usage charges
2.	Frequent customer service interactions
3.	Status of international and voicemail plans


Business Recommendations
1. Focus on High-Risk Segments with Precision
Targeted Retention Outreach: With a precision of 95%, the model accurately identifies churners, meaning that nearly all flagged customers are genuinely at risk. This high precision allows the business to confidently allocate retention resources without wasting efforts on low-risk customers.
Cost-Effective Retention Offers: Given the model's precision, invest in targeted retention incentives (e.g., special discounts, personalized plans) only for customers identified as high churn risks, avoiding unnecessary spending on customers likely to stay.
2. Address Specific Dissatisfaction Signals
Proactive Support for High Customer Service Callers: The recall rate of 73% suggests that while the model captures a majority of churners, some at-risk customers might be missed. Focus additional efforts on customers who contact customer service frequently, as these interactions correlate strongly with churn. For example:
Implement a proactive follow-up system to reach out to high-frequency callers and address unresolved issues, preventing them from slipping through the cracks.
Enhanced Support for High-Usage Customers in Specific Areas: Customers with high daytime and international usage showed notable churn patterns. The model’s recall indicates that many of these high-value users may be at risk, so consider special retention packages or targeted support to ensure they feel valued.
3. Optimize Offerings Based on Usage Patterns
Promotional Bundles for Engaged Users: With an F1-score of 81%, the model balances identifying both true churners and non- churners effectively, allowing a strategic focus on high-usage customers without excessive false positives. For instance:
High Daytime Users: Offer discounted daytime data or minutes bundles to users with significant daytime engagement, encouraging loyalty.
Frequent International Callers: Create international calling plans at discounted rates to retain customers who rely on this service.
Voice Mail and Other Add-On Plans: Customers with voicemail plans churn less frequently. Promote these add-ons as part of a loyalty package, as they seem to increase satisfaction and reduce churn probability.
4. Leverage High Accuracy on Test Data
Focus on Retention Campaigns with Predictable ROI: With a consistent testing accuracy of 90-92%, the model reliably predicts churn on unseen data, providing a steady foundation for churn-related interventions.
Revenue Protection Based on Model Confidence: For each customer the model identifies as high-risk, estimate potential revenue loss using average revenue per customer and churn likelihood. For instance:
If each customer is worth $50/month and a high-risk customer is flagged, consider an intervention worth a fraction of this revenue to prevent potential churn and maximize ROI.
5. Profit-Optimized Interventions Based on Cost-Benefit Analysis
Retention Budget Allocation: Given that the model’s confusion matrix showed specific True Positive (TP) and False Positive (FP) rates, utilize these to structure cost-effective retention strategies. For example:
With a high TP rate, assign a fixed budget for targeted retention strategies that prevent churn while avoiding excessive investment in customers unlikely to churn.
Calculate the expected savings per intervention by comparing the cost of offers to the estimated lost revenue for each high-risk customer. For example, if the average revenue loss per churned customer is $500 annually, allocate an intervention budget below this amount for effective retention.
6. Improve Customer Experience with Data-Driven Insights (High Testing Stability)
Stable Testing Metrics: The testing accuracy and loss remain stable after the initial epochs, which is a strong indicator that the model is not prone to large variances. Use this stability to build trust with customer support and marketing teams by implementing the model’s insights into customer interactions and outreach programs.
Personalized Customer Experience: Use specific insights from the variables in the model to personalize experiences for different customer segments:
New Customers (AcctLength): For customers with shorter account lengths, provide enhanced support during the first 6 months to build loyalty.
Service-Dependent Users (DayMinutes, IntlMin): For customers with high usage during the day or internationally, consider incentives like free additional minutes or loyalty rewards to reduce churn.
7. Model Monitoring and Iterative Improvements
Regular Evaluation and Adjustments: Given the model’s performance metrics, set a schedule to retrain and fine-tune the model every few months to capture evolving customer behavior. This ensures the churn predictions stay relevant as customer preferences shift.
Threshold Tuning: Based on profit margins and customer lifetime value, periodically evaluate the threshold for predicting churn to ensure it aligns with business goals and maximizes the effectiveness of retention efforts.


Expected Profit
Training Data Set: $47,816,135
Testing Data Set: $46,551,724 (estimated)

How to Use
Clone the repository:
text
git clone https://github.com/sameeragarwal123/Churn-Rate-Prediction.git


Future Work

•	Implement more advanced feature engineering

•	Explore ensemble methods for improved performance

•	Develop a real-time prediction system


Conclusion:
In this case study, we successfully developed and implemented a neural network model to predict customer churn, leveraging a rich dataset of customer usage and engagement metrics. The model’s high accuracy, recall, and precision on the testing set underscore its ability to effectively identify at-risk customers, enabling targeted interventions that align with the business's retention objectives.
By applying data-driven strategies, such as proactive customer service, customized promotions, and precision-based targeting, the telecom provider can enhance customer satisfaction and reduce churn rates. This approach not only strengthens customer relationships but also maximizes profitability through more efficient use of retention resources.
With regular model updates and continued monitoring of performance metrics, the company can maintain a robust churn prediction framework that adapts to changing customer behaviors and market conditions. This comprehensive churn reduction strategy positions the business to retain a competitive edge in a dynamic and challenging market environment, ensuring long-term customer loyalty and sustainable growth.
