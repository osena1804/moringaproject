# Beginner-Toolkit-Using-Pandas-Library
🐼 Pandas Pilot: A Beginner's Toolkit for Data Mastery
Welcome to the Pandas Pilot Toolkit! This project is designed to take you from "Zero to Hero" in data manipulation using Python's most powerful library: pandas.

📖 Table of Contents
Overview

Setup Guide

The Dataset

The Master Script

Troubleshooting

Cheat Sheet

🌟 Overview
Pandas is the industry standard for data analysis. This toolkit focuses on the Full Data Lifecycle:

Ingest: Loading raw .csv files.

Clean: Fixing "messy" data (duplicates, nulls, casing).

Transform: Creating new insights through calculations.

Analyze: Summarizing data using groupby.

Visualize: Creating charts to tell a story.

🛠️ Setup Guide
To get started, you need a Python environment.

Install Pandas: Open your terminal and run: pip install pandas matplotlib

Verify: Run import pandas as pd in your script.

File Management: Always keep your Python script and your data file (moringa_toolkit.csv) in the same folder.

📂 The Dataset
Create a file named moringa_toolkit.csv and paste the following 20 rows of "messy" bookstore data:

Plaintext

Order_ID,Book_Title,Price,Quantity,Date
101,The Great Gatsby,15.99,1,2023-01-01
102,the great gatsby,15.99,1,2023-01-01
103,1984,,2,2023-01-02
... (add all 20 rows here)
🐍 The Master Script
This script performs the cleaning, transformation, and visualization automatically.

Python

import pandas as pd
import matplotlib.pyplot as plt

# 1. LOAD
try:
    df = pd.read_csv('moringa_toolkit.csv')
    
    # 2. CLEAN
    df['Book_Title'] = df['Book_Title'].str.strip().str.title()
    df = df.drop_duplicates()
    df['Price'] = df['Price'].fillna(df['Price'].median())
    df['Quantity'] = df['Quantity'].fillna(1)

    # 3. TRANSFORM
    df['Total_Revenue'] = df['Price'] * df['Quantity']

    # 4. ANALYZE
    top_books = df.groupby('Book_Title')['Total_Revenue'].sum().sort_values(ascending=False)

    # 5. VISUALIZE
    top_books.head(5).plot(kind='bar', title='Top 5 Books by Revenue')
    plt.ylabel('Revenue ($)')
    plt.show()

except FileNotFoundError:
    print("Error: Ensure 'moringa_toolkit.csv' is in the same folder as this script!")
🔍 Troubleshooting
Error	Likely Cause	Solution
FileNotFoundError	File is in a different folder	Move the CSV to the script's folder
KeyError	Typo in column name	Check df.columns for exact spelling
AttributeError	Used a string function on a whole table	Specify the column: df['Col'].str

Export to Sheets

📜 Quick Cheat Sheet
df.head(): Preview data.

df.info(): Check for missing values.

df.describe(): Get statistical summaries.

df.groupby(): Summarize data by categories.

plt.show(): Display your charts.
