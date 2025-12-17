# INTERNSHIP-DATA_ANALYSIS USING-PANDAS
PANDAS
PYTHON FAST,FLEXIBLE PYTHON LIBRARY USED FOR DATA MANIPULATION,ANALYSIS,CLEANING.

NEED IN MACHINE LEARNING-
MAKE DATA CLEANING AND TRANSFORMATION EASIER
HANDLE STRUCTURED DATA(EXCEL)
GROUPING,FILTERING,MERGING,RESHAPING - FUNCTIONALITY

PROJECT PROCEDURE REFERENCE
1.LOAD THE DATASET.
2.VIEWING THE DATASET.
3.SELECTING COLUMNS/ROWS
4.HANDLING MISSING DATA

CODE FOR MY PROJECT
import pandas as pd
# Load the dataset
df = pd.read_excel("Indian Ecommerce_Orders.xlsx")
# -------------------------------------------------------
# Use "Total Amount After Discount" as Total Revenue
# -------------------------------------------------------
df["TotalAmount"] = df["Total Amount After Discount"]
# -------------------------------------------------------
# SUMMARY INSIGHTS
# -------------------------------------------------------
# 1. Total Revenue
total_revenue = df["TotalAmount"].sum()
print("Total Revenue: ₹", total_revenue)

# 2. Revenue by Category
revenue_by_category = df.groupby("Category")["TotalAmount"].sum()
print("\nRevenue by Category:\n", revenue_by_category)

# 3. Revenue by City
revenue_by_city = df.groupby("City")["TotalAmount"].sum()
print("\nRevenue by City:\n", revenue_by_city)

# 4. Most Purchased Product (by total quantity)
most_purchased_product = df.groupby("Product")["Quantity"].sum().idxmax()
print("\nMost Purchased Product:", most_purchased_product)

# 5. Customer-wise Revenue
customer_revenue = df.groupby("Customer Name")["TotalAmount"].sum()
print("\nCustomer-wise Revenue:\n", customer_revenue)

# 6. Daily Revenue Trend (Delivery Date used if Order Date missing)
df["Delivery Date"] = pd.to_datetime(df["Delivery Date"])
daily_revenue = df.groupby(df["Delivery Date"].dt.date)["TotalAmount"].sum()
print("\nDaily Revenue Trend:\n", daily_revenue)

# -------------------------------------------------------
# ADVANCED INSIGHTS
# -------------------------------------------------------

# AOV = Average Order Value
aov = df["TotalAmount"].mean()
print("\nAverage Order Value (AOV): ₹", aov)

# Payment Mode Usage
payment_mode_count = df["Payment Mode"].value_counts()
print("\nPayment Mode Usage Count:\n", payment_mode_count)

# Category-wise Average Price
category_avg_price = df.groupby("Category")["Price"].mean()
print("\nCategory-wise Average Price:\n", category_avg_price)

# Top City for Fashion Category
fashion_city = (
    df[df["Category"] == "Fashion"]
    .groupby("City")["TotalAmount"]
    .sum()
    .idxmax()
)

print("\nTop City for Fashion Category:", fashion_city)



