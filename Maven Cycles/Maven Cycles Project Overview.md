![Maven_Cycles_Logo](https://github.com/user-attachments/assets/3040750c-cd35-4725-81c4-eea3dfb09f5d)

Maven Cycles is a Fictious Bicycles Company. 

The data used in this project is located in the Data Folder.
The .pbix is the Power Bi File itself. 
This data

# **Goal**

The Goal of this project was to explore Power Bi and create reports and Dashboard that would allow stakeholders (fictious) the ability to make data driven decisions. 

To this extent, I aimed to identify KPIs, Top/Bottom performing products, and the effects of seasonality and location on sales. 


# **Data Prep**

The data was initial formated as ... 

Therefore I needed to modify and clean the data by ... 


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


