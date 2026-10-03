# EDA-Projrct-Group-14

import pandas as pd
import matplotlib.pyplot as plt


df = pd.read_csv("ecommerce_dataset (3).csv")

print(df.shape)

print(df.isnull().sum())

print("Duplicate rows:", df.duplicated().sum())

print("Duplicate product IDs:", 

df["product_id"].duplicated().sum())

df["sales_value"] = df["price"] * df["units_sold"]

print(df[["price", "units_sold", "rating", "sales_value"]].describe())

summary = df.groupby("category").agg(
    records=("product_id", "count"),
    average_price=("price", "mean"),
    total_units=("units_sold", "sum"),
    average_rating=("rating", "mean"),
    stock_rate=("in_stock", "mean"),
    sales_value=("sales_value", "sum")
)

print(summary)

print(df[["price", "units_sold", "rating", "sales_value"]].corr())

df["price"].plot(kind="hist", bins=25, edgecolor="black")

plt.title("Distribution of Product Prices")

plt.xlabel("Price")

plt.ylabel("Number of Records")

plt.tight_layout()
plt.show()

