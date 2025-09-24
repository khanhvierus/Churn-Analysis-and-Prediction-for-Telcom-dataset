## Churn-Analysis-and-Prediction-for-Telcom-dataset 
### Problem Statement : 

A telecommunications company is providing a variety of services to its customers such as Internet, telephone, television, additional services and various payment plans. During its development, the company faced several important challenges:

  •	Customer churn rate remains high, directly affecting revenue. <br>
  •	Differences in demographics, service usage habits and payment method choices make customer segmentation necessary. <br>
  •	The need to analyze factors affecting churn (gender, age, service type, payment method, number of years of service, etc.) to build a customer retention strategy. <br>
  
The dataset collects detailed information about customers, subscription services, usage behavior, payment, and churn. The goal of the project is to use this data to uncover insights, analyze churn causes, and propose solutions to improve customer experience and increase retention rates.
### Data and tools used : 
- **Telcom dataset** with 6419 records and 32 columns
- Data cleaning and analysis : PostgreSQL
- Data visualization : Tableau
- Building models for prediction : Python

### Questions : 
1. Sum of churns
2. Churn rate by gender
3. Churn rate by martial status
4. Churn rate by state
5. Top 5 states which contributed the most referrals to our company
6. Churn rate by customer loyalty
7. Churn rate by value deal
8. Churn rate by service groups
9. Churn rate by internet type
10. Churn rate by contract
11. Churn rate by payment method
12. Total churns of each churn category

### Findings and Insights summary: <br>
- Churn rate does not differ between gender and marital status <br>
- The state with the highest Churn rate is 'Jammu & Kashmir' (0.57) while 'Uttar Pradesh' has the most Referrals (4682) <br>
- For the group of reasons for leaving the service, the majority of customers did not leave a specific reason (4778). On the contrary, the most common reason given is 'Competitor' (752) <br>
- In the following service groups, the Churn rate of the registered group is higher than the non-registered group:<br>
  •	Internet service <br>
  •	Multiple Lines (multiple phone numbers at the same time)<br>
  •	Paperless Billing (electronic bill)<br>
  •	Phone Service<br>
  •	Streaming Movies <br>
  •	Streaming Music<br>
  •	Streaming TV<br>
  •	Unlimited Data<br>
- On the contrary, for the following service groups, the Churn rate of the non-registered group is higher than the registered group:<br>
  •	Device Protection Plan<br>
  •	Online Backup<br>
  •	Online Security<br>
  •	Premium Support<br>
- For Age groups, the majority group is from 20 -> 59 years old. However, the highest Churn rate is 0.36, in the elderly group (>= 60)<br>
- For the group of promotional packages, it is noteworthy that the Churn rate increases gradually according to the number of Deals, in other words: The higher the Deal, the higher the Churn rate. The highest is Deal 5 with a Churn rate of 0.54<br>
- According to the Tenure classification, we have the 'New customers' group (<= 12 months) with the highest number. The Churn rate of all 3 Tenure groups is quite equal, the most surprising is the 'Long-term customers' group (> 24 months) with the highest Churn rate of 0.28<br>
- Regarding the Internet network classification, the most used network type is Fiber optic (2725), which also has the highest Churn rate (0.41)<br>
- Regarding the Contract, we can easily see that the month-to-month contract accounts for the majority, and is also the group with the highest Churn rate (0.46). The Churn rate decreases as the contract term increases - this is very reasonable<br>
- Finally, the payment method. The most popular type is 'Bank Withdrawal' (3521), but the type with the highest Churn rate is 'Mailed check' with 0.38 despite only having 343 customers. 'Credit card' has quite a lot of customers (2447) but has the lowest Churn rate with only 0.15.


### Dashboard: <br>
<img width="557" height="363" alt="Image" src="https://github.com/user-attachments/assets/802409d0-b40c-4ab0-a08e-b954860ccea5" />
### Recommendations:

#### 1. Customer Segmentation & Targeting:
- Since churn rate does not differ by gender or marital status, customer retention strategies should focus on other demographics (age, geographic region, services used) instead of gender.  
- The senior group (>= 60) has the highest churn rate (0.36) → need a senior-friendly, easy-to-use service package with priority customer support.  

#### 2. Regional Strategy:
- Jammu & Kashmir has the highest churn rate (0.57) → need to analyze the specific reasons in this region: network quality, price, or competition.  
- Uttar Pradesh has the most referrals → continue to promote referral programs here because of effectiveness, and learn to replicate the model to other states.  

#### 3. Service & Subscription Plans:
- Services such as Internet, Multiple Lines, Streaming, Unlimited Data have high churn rates → proving that customers who use many services often have higher expectations. So:  
  - Improve the quality of Internet & Fiber optic services (because Fiber optic has a high churn of 0.41).  
  - Increase bundle discounts to encourage long-term commitment.  
- On the contrary, services such as Device Protection, Online Backup, Security, Premium Support help reduce churn → can cross-sell/upsell these services as additional packages to retain customers.  

#### 4. Contract & Tenure Strategy:
- Month-to-month contract has the highest churn (0.46) → encourage customers to switch to long-term contracts (1–2 years) by offering installation fee incentives, first month discounts or special benefits.  

#### 5. Payment Methods:
- Mailed checks have the highest churn rate (0.38) → this group may be older customers who are less familiar with online payments. So:  
  - Encourage them to switch to Credit Card or Auto Bank Withdrawal by offering a discount on service fees/small incentives when switching payment methods.  
  - Keep offline support for some older customers, but aim for digitalization.  
- Credit cards have the lowest churn (0.15) → encourage more customers to use this method.  

#### 6. Churn Reasons:
- Among the reasons, Competitor (752) is the most common → need to analyze competitor's strategy (price, promotion, internet speed) and improve current weaknesses.  

#### 7. Deals / Promotions:
- Churn rate increases when there are more deals (deal 5 has churn up to 0.54) → proving that current promotions do not retain customers for a long time, but are only short-term.  
- Promotion policies need to be redesigned: not only initial discounts but also long-term benefits (free upgrade, data bonus, VIP customer support).

### Summary of results from building models for predictions: 
- The results from the importance assessment based on the Random Forest model are very promising, most of the features with high importance match what was analyzed in the Insights section.
- Recall (main metric) increases after filtering out less important features
- The Recall of class 1 after testing on XGBoost (0.67) and LightGBM(0.78) is higher than on RandomForest(0.57)<br>

To see the whole processing, you can view this file [Customer_Churn_Prediction.ipynb](Customer_Churn_Prediction.ipynb)

