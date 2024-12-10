## GRAFANA DASHBOARD

#### INTRODUCTION

The dataset **Online Retail Sales Dataset** provides comprehensive transactional data for an online retail platform. It captures sales and customer details over a specific time frame, potentially useful for analyzing purchasing trends, customer demographics, and product performance. Each row represents an individual transaction, complete with product, customer, and payment details.

<br>

![image](https://github.com/user-attachments/assets/6b3fd639-14c0-4d16-9298-55427633c59e)

<br>

#### DATASET : ONLINE RETAIL SALES DATASET 

<a href="https://www.kaggle.com/datasets/arnavsmayan/online-retail-sales-dataset">Dataset Link</a>

![image](https://github.com/user-attachments/assets/355cb20b-99f9-432f-9be8-d313066550e8)



Number of rows: <b>10,00,000</b><br>
Number of columns: <b>13</b>
<br>
<br>

#### VARIABLE DESCRIPTION


- **transactionid:** Unique identifier for each transaction.
- **customerid:** Unique identifier for the customer making the purchase.
- **productid:** Unique identifier for the purchased product.
- **productcategory:** Category to which the purchased product belongs (e.g., Electronics, Books).
- **quantity:** Number of units of the product purchased in the transaction.
- **price:** Price of one unit of the product.
- **discount:** Discount applied on the product as a fraction of the price (e.g., 0.23 for 23%).
- **paymentmethod:**  Mode of payment used (e.g., CreditCard, PayPal).
- **customerage:** Age of the customer making the purchase.
- **customergender:** Gender of the customer (e.g., Male, Female, Other).
- **customerlocation:** Geographic region where the customer is located (e.g., NorthAmerica, Asia).
- **totalamount:** Total amount spent in the transaction after accounting for quantity and discounts. 

<Br>
<br>

### DASHBOARD

![Whole_Dashboard](https://github.com/user-attachments/assets/876a6d90-089e-4a76-8a98-bd3cd22323a6)

<br>

[Screencast from 23-11-24 12_19_57 AM IST.webm](https://github.com/user-attachments/assets/e5d97f33-60cf-4661-8aed-f47c04cfbcea)


<br>
<br>

### CHARTS


1.  How does revenue vary over time?
   
      <ins>**Revenue Over Time**</ins>

     **Description:** This time-series visualization likely helps monitor **sales performance** and identify trends or anomalies in real-time or over a specified period.

     ![Graph-1](https://github.com/user-attachments/assets/08eb70f7-4f86-4cf7-87f3-d5173f146ae2)

     **Query:** <i>select (“totalamount”),(“time”) from “data”</i>

     <b>Insights:</b>  The graph displays fluctuating revenue over time, indicating variability in transaction amounts driven by factors like customer behavior or product categories. Peaks in revenue suggest high-value purchases or promotional periods, while red markers likely highlight anomalies or predefined thresholds. These insights help identify sales trends, monitor performance, and detect unusual activity for further analysis.

<br>
<br>

2. What is the contribution of different product category to revenue?

   
     <ins> **Product Category Contribution to Total Revenue** </ins>

   
      **Description:** This donut chart visualizes the contribution of each product category to the total revenue. It helps in understanding which categories generate the most revenue and their relative importance in the overall sales.

    ![Graph-5](https://github.com/user-attachments/assets/6bcb2ccc-19ab-4c50-9f89-cb850e3bd855)

     **Query:** <i>SELECT sum("totalamount") FROM data GROUP BY "productcategory"</i>

     <b>Insights:</b> The chart shows that Electronics (19%) and Home & Kitchen (18%) are the top contributors to revenue, suggesting they are key drivers of sales. Other categories, such as Sports & Outdoors, Clothing, Beauty & Personal Care, and Books, each contribute 14-17%, indicating a relatively balanced revenue distribution across product categories. This distribution highlights the importance of focusing on high-performing categories while maintaining diversity in offerings.

<br>
<br>

3. What is the preferred payment method by customers?
   
   <ins> <B>Payment Method Preference</B> </ins>
    
   **Description:** This bar chart represents the preference for payment methods among customers, showing the distribution of transactions made via different payment methods like Credit Card, Debit Card, Gift Card, and PayPal. Its purpose is to analyze which payment options are most frequently used.

   ![Graph-6](https://github.com/user-attachments/assets/a94d2f3f-9baf-45ba-874a-0ff5c4c7f11b)


   **Query:** <i>SELECT COUNT(transactionid) AS "transactions" FROM "data" GROUP BY "paymentmethod"</i>
    
   **Insights:**   The chart reveals that the transaction counts for all payment methods—Credit Card, Debit Card, Gift Card, and PayPal—are relatively similar, indicating no single dominant payment method. This balance suggests that customers are diverse in their payment preferences, and the business should continue supporting all these options to cater to varied customer needs

<br>
<br>

4. What is the gender distribution of customers?
   
	  <ins> **Gender Breakdown** </ins>
   
     **Description:** The purpose of the graph is to display the gender distribution of customers in the dataset using a visual representation of counts for each gender category: Female, Male, and Other. Each gauge indicates the number of customers falling into a respective gender group.

    ![Graph-4](https://github.com/user-attachments/assets/a4b861b0-98af-42ac-93f6-c4fe7ca9e34f)


      **Query:** <i>SELECT COUNT(transactionid) AS "Customer Count" FROM data GROUP BY customergender</i>

     **Insights:** The graph reveals that the customer distribution is relatively balanced across genders. Specifically, there are 567 Female customers, 588 Male customers, and 579 customers categorized as Other. This demonstrates inclusivity in gender representation among customers and indicates no significant gender dominance in the customer base.
  
<br>
<br>

5. What is the Customer Age Distribution based upon revenue? 

      <ins> **Customer Age Distribution** </ins>
    
      **Description:** The purpose of the graph is to visualize the customer age distribution across different age groups (e.g., 18-25, 26-40, 41-55, 56-70) over time. It highlights the frequency or transaction patterns among various age categories within the given time frame.

    ![Graph-2](https://github.com/user-attachments/assets/8cf0c1d4-933c-4b24-b506-f9d200acc4ed)

      **Query:** <i>SELECT "totalamount","time" FROM "data" WHERE "customerage" >= 18 AND "customerage" <= 25<br>
SELECT "totalamount","time" FROM "data" WHERE "customerage" >= 26 AND "customerage" <= 40<br>
SELECT "totalamount","time" FROM "data" WHERE "customerage" >= 41 AND "customerage" <= 55<br>
SELECT "totalamount","time" FROM "data" WHERE "customerage" >= 56 AND "customerage" <= 70<br></i>

     **Insights:** The graph shows that all age groups have varying levels of activity throughout the time period, with spikes in certain intervals indicating higher engagement or transaction volume. The 26-40 and 41-55 age groups appear to contribute significantly to the activity, as indicated by their frequent and prominent peaks. This suggests these age groups are the primary customers, with occasional significant activity from the younger (18-25) and older (56-70) groups.

<br>
<br>

6. How is the Sales distributed based upon Customer Location?

    <ins> **Sales by Customer Location** </ins>
    
    **Description:** The purpose of this graph is to represent sales by customer location, showing the total sales value generated from each region (South America, North America, Europe, Australia, Asia, and Africa). It helps compare the contribution of different regions to overall sales.

      ![Graph-3](https://github.com/user-attachments/assets/a0f106f6-02a4-48ed-9fcf-87d7c9c7ba0e)


      **Query:** <i>select sum(totalamount) from data group by customerlocation order by DESC</i>

      **Insights:** The graph highlights that Asia leads with the highest sales total (317,365), followed by Europe (285,865) and Africa (273,153). Regions like South America (265,911), Australia (260,116), and North America (255,061) have slightly lower but comparable contributions. This suggests that Asia and Europe are key markets driving sales, while North America and Australia might represent areas with potential for growth.

<br>
<br>

7. What is the Total Revenue?
   
    <ins>	**Total Revenue** </ins>
    
    **Description:** The graph displays the Total Revenue generated by the e-commerce business, aggregating all transactions within the selected time period (last 6 hours, as indicated). It provides a quick, high-level view of the business's financial performance during that time frame.

     ![Graph-8](https://github.com/user-attachments/assets/aa84eb3f-9f47-4029-832b-ccd1debfe55c)


     **Query:** <i> SELECT sum("totalamount") FROM "data"</i>

     **Insights:** The total revenue of **$1.67** million reflects the business's strong performance within the monitored timeframe. This indicates effective product sales and customer engagement, possibly driven by popular product categories, targeted discounts, or successful marketing efforts. However, further analysis of revenue drivers (e.g., top-selling categories, regions, and payment methods) can help pinpoint specific factors contributing to this result.

<br>
<br>

8. Which time of day sees the highest sales?
   
    <ins>	**Peak Hour Sales** </ins>
    
    **Description:** The graph illustrates the total sales volume across specific time intervals, aiming to identify the time of day when sales activity peaks.

    ![Graph-7](https://github.com/user-attachments/assets/65158dbb-2e0a-4e80-a2a7-22c76e64849f)


     **Query:** <i>Query: SELECT SUM(totalamount) AS "Total Sales" FROM data GROUP BY time(30m)</i>

     **Insights:** The graph reveals variations in sales activity over time, with the highest sales occurring around 21:00–22:30, as indicated by the darker orange bars. This suggests a trend of increased customer activity during late evening hours, potentially driven by shopping habits or promotional strategies targeted during this time. Businesses can leverage this insight to optimize marketing campaigns or flash sales during peak hours to maximize revenue.

<br>
<br>

9. Are there any thresholds in the Dashboard?
   
   <ins>**Alert Revenue**</ins>
    
   **Description:** This shows a clear visual representation of whether their spending exceeds a predefined threshold (e.g., 3000). This serves as a tool for identifying key revenue-generating demographics and enables timely responses to shifts in consumer behavior or purchasing patterns.

    ![Graph-9](https://github.com/user-attachments/assets/54ae8d31-2d79-43bc-b59f-b1f422f954b8)

   **Alert URL:** <i>[ Alert Revenue](https://webhook.site/7d6aaf76-bffc-4b09-88f4-a7f8f681f79a)</i>

   **Insights:** The alert indicates that customers aged 41-55 have exceeded the revenue threshold, likely driven by effective marketing, product appeal, or increased engagement. This group represents a significant revenue opportunity, warranting tailored strategies such as personalized promotions, product innovations, and loyalty programs to capitalize on their spending patterns and drive sustained growth.

<br>
<br>

10. Are there any other thresholds in the Dashboard?
   
       <ins> **Alert: Revenue by specific Age Group** </ins>
    
       **Description:** The graph is designed to track total revenue over time, identifying instances where it exceeds a predefined threshold (e.g., 3000). This provides a clear visualization of revenue performance, enabling businesses to pinpoint periods of exceptional growth and analyze contributing factors.


    ![Graph-10](https://github.com/user-attachments/assets/fc982bf2-8b6d-463f-8801-7d92e368c1e9)


       **Alert URL:** <i>[ Alert: Revenue by specific Age Group](https://webhook.site/7d6aaf76-bffc-4b09-88f4-a7f8f681f79a)</i>


      **Insights:** Exceeding the revenue threshold suggests strong business performance, likely driven by effective marketing, customer engagement, or product demand. This highlights the need to analyze sales data, marketing strategies, and product performance to identify key growth drivers. Leveraging these insights can help sustain revenue growth, improve customer retention, and guide future business strategies.

<br>

### MANAGERIAL IMPLICATIONS


1. **Focus on High-Performing Segments:**
    - Target key customer demographics (e.g., age group 41-55) and high-performing regions (e.g., Asia and Europe) to optimize sales strategies.
    - Prioritize top revenue-generating product categories like Electronics and Home & Kitchen for promotions and inventory management.


2. **Tailor Marketing Strategies:**
    - Use customer segmentation insights to design personalized campaigns and loyalty programs.
    - Align promotions with peak activity times (e.g., late evening hours) to maximize impact.


3. **Enhance Operational Efficiency:**
    - Ensure sufficient inventory and staffing during high-sales periods.
    - Continuously monitor for anomalies or threshold breaches to respond promptly.
    

4. **Leverage Diverse Customer Preferences:**
    - Maintain support for varied payment methods and product offerings to cater to a broad customer base.
    - Foster inclusivity by addressing the balanced representation of genders in your customer data.


5. **Drive Regional and Portfolio Growth:**
    - Expand efforts in high-performing regions while identifying opportunities in underperforming areas.
    - Diversify offerings by nurturing emerging product categories to sustain long-term growth.


6. **Data-Driven Decision Making:**
    - Regularly analyze sales trends, customer behavior, and revenue drivers to refine strategies.
    - Use insights from anomalies and performance spikes to replicate successful tactics across the business.
    
#### CONCLUSION

The analysis highlights critical insights into revenue drivers, customer demographics, and product performance, enabling targeted strategies for growth. Prioritizing high-performing segments, optimizing marketing efforts, and leveraging data-driven decisions can enhance efficiency and customer engagement. By addressing these areas, the business can sustain growth and capitalize on emerging opportunities effectively.
<br><br>
