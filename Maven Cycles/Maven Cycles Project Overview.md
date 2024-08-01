![Maven_Cycles_Logo](https://github.com/user-attachments/assets/3040750c-cd35-4725-81c4-eea3dfb09f5d)

Maven Cycles is a fictional Bicycles Company. 

The data used in this project is located in the Data Folder.
The .pbix is the Power Bi File itself. 
This data

# **Goal**

The Goal of this project was to explore Power Bi and create reports and Dashboard that would allow stakeholders (fictional) the ability to make data driven decisions. 

To this extent, I aimed to identify KPIs, Top/Bottom performing products, and the effects of seasonality and location on sales. 


# **Data Prep**

The data was initial formatted as flat .csv files. Therefore, the data was imported and modified using the Power Query editor. Several tables need to be clean and transformed using operations such as Unpivot, Make First Row the Header, and correcting column headers and data types. 


# **Data Modeling**

Once all the data was imported and ready to use, I created a snowflake schema and created the relationships between the tables. The resulting model looked like this: 

![image](https://github.com/user-attachments/assets/84434363-4119-4b29-b672-6640dd8837be)



# **Data Analysis**

I then proceeded to create various measures, calculated columns, and calculated tables to create useful insights into the data. 

The most impactful measures I created include: 

* Total Revenue 
* Total Cost 
* Total Orders
* Quantity Sold 
* Profit 
* Profit Margin 

Additionally measures made include: 

* All Profit
* Last Month Profit 
* Last Month Profit Margin
* Last Month Revenue
* Mid Price Range Revenue 
* Percentage of Profit
* Quantity Sold (Stock Date)
* Quantity Sold YTD

Several calculated tables were also created to gain additional insights into product performance. 
These tables include: 

1. Top 5 Bikes
2. Top 5 Accessories
3. Top 5 Clothing
4. Bot 5 Bikes
5. Bot 5 Accessories
6. Bot 5 Clothing
7. United States Regional Sales

Here is the DAX used to create the Top 5 Accessories table. 

```DAX
Top 5 Accessories = 
TOPN(5,
    FILTER(
        SUMMARIZE( 'Maven Cycles Sales',
            'Maven Cycles Product Categories'[Product Category],
            'Maven Cycles Products'[Product],
            "Quantity Sold",
            [Quantity Sold],
            "Revenue",
            [Total Revenue]
        ),
        'Maven Cycles Product Categories'[Product Category] = "Accessories"
    ),
    [Total Revenue],
    DESC
)
```

This DAX formula was modified to create the Top 5 and Bot 5 tables by changing the TOPN value as well as the filter order. 

The new calculated tables were not connected.
![image](https://github.com/user-attachments/assets/412e3364-e7d2-41d0-a9f7-ba0a44d62e4f)


# **Data Visualization**

Finally, I created a report allowing stakeholders the ability to visual KPIs, Top/Bottom performing products, and the effects of seasonality and location on sales as well as much more. 

The report consists of 7 pages. 

##  Executive View

The first page is the "Executive View". The goal of this page was to provide a high-level overview of the company's performance with Country and Category Filters and Date Slicers. 

![image](https://github.com/user-attachments/assets/ac86a731-aa75-4c81-8b35-22f07866cdc0)


## Highest Performers By Category 

The second page shows the "Highest Performers By Category". The goal of this page is to quickly identify the Top 5 products for each category (Bikes, Accessories, Clothing). 

These products could be considered our money makers as they contribute greatly to the total company revenue. For example, the Top 5 Accessories contribute to roughly 29% of the company's total revenue. Additionally, the Top 5 Bikes contributes roughly 16% to the total revenue. Those 10 products therefore bring in roughly 45% of the company's total revenue. With this information, stakeholders can determine whether to double down on these products or even use the products as a baseline for new product lines. 

![image](https://github.com/user-attachments/assets/a0e63f95-0c1d-4765-b9c0-808ba89a944a)


## Lowest Performers By Category 

The third page shows the "Lowest Performers By Category". This page is similar to the one before but aims to identify opportunities for cost savings. 

For example, the lowest 5 bikes all have an average profit margin of 38% - 46%. Furthermore, the Trek-650 Red,50 and the GT MTB-500 Black,52 has only been sold 95 and 76 times over the 5-year period of our data.  This means they are averaging 19 and 15 sales a year. With this data, stakeholders can determine if there are viable products to discontinue based on data. 

![image](https://github.com/user-attachments/assets/c1deda55-e107-44cb-9ae8-02f2869445a0)

## Seasonality & Location Analysis 

The fourth page examines the company's performance of over time as well as per country. 

From this data we can see that the company had a relatively slow start in 2015 through 2016 before growing rapidly in 2017. Between 2018 and 2020 the company continued to perform quite well despite a few rough quarters. 

We can als see that the United States and Australia are our best performing markets while the UK, Germany. France, and Canada are still growing. 

The company's best performing months are June, May, and then December. It could be speculated that during the summer months more people are looking to do activities outside which would contribute to the higher sales in May and June. Whereas many parents may gift their children bikes or bike accessories during the Holiday Season. 

![image](https://github.com/user-attachments/assets/1539e846-5b7f-4e11-928f-7827eb532067)


## Regional Analysis 

The fifth page takes a closer look into the regional performance of the United States. 

The company has multiple US locations grouped into 5 regions: Northwest, Southwest, Central, Northeast, Southeast. 

Of these 5 regions, the Southwest and Northwest stores are the most profitable. The Southwest and Northwest regions both makes more than the UK, Germany, France, and Canada market individually. 

This data could enable stakeholders to make data driven decision about growth opportunities or cost savings for the Central, Southeast, and Northeast regions.

![image](https://github.com/user-attachments/assets/e10bb64d-989b-4e4b-a00f-217e4a7b9916)


## Age & Gender Analysis 

The sixth page allows stakeholdersto view our company's target demographics. 

From this data we can see that, there are roughly equal amount of Female and Male customers. However, roughly half of all sales come from Adults aged 35 - 64.  Roughly another third of the sales comes from Young adults ages 25 - 34. While sales to Youths less than 25 years of age account for 14% of all sales. 

With this data our marketing team might be able to make data driven decisions regarding ad targeting. 

![image](https://github.com/user-attachments/assets/b04f1e58-5b1e-4d78-9bbe-b6b56f187ae9)



## Decomposition Tree 

Finally, the seventh page contains a Decomposition tree which allows the user to perform ad-hoc data exploration. 

The default view starts with Total Revenue before being expanded by Country, Year, Quarter, Product Category, Product SubCategory, and Age Group. 

![image](https://github.com/user-attachments/assets/74b53f1f-3fb8-4bda-9f34-40b542ee77ec)


