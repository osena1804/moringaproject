🐼 Pandas Pilot: A Beginner's Toolkit
Welcome to the Pandas Pilot Toolkit! This project is designed to take you from "Zero to Hero" in data manipulation using Python's most powerful library: pandas.

📖 Table of Contents
Overview

Key Features

Setup Guide

The Master Script

Interactive Data Bot

Testing & QA

References

🌟 Overview
This project was developed as a Capstone to demonstrate the power of Generative AI-assisted software development. The goal was to build a comprehensive "First-Steps" toolkit for aspiring data analysts.

Using a custom-built dataset (moringa_toolkit.csv), this repository guides users through the core pillars of the Pandas library: data wrangling, feature engineering, and visual storytelling.

why chose these tools

Feature	       Pandas (What we used)	   Excel (The Alternative)
Automation	   Fully automated scripts.	   Manual clicking/macros.
Data Size Handles millions of rows easily.Slows down with large files.
Reproducibility	One click to repeat on new data.	Prone to human error in copy-paste.
Cost	Free and Open Source.	Requires a paid license.

🛠️ Key Features
Step-by-Step Setup: Detailed instructions for local Python environments.

Realistic Data Cleaning: A dataset designed to teach text standardization and null value handling.

Automated Transformation: Instant calculation of business metrics like Total_Revenue.

Visual Analysis: Built-in Matplotlib logic to turn raw rows into actionable charts.

Interactive Data Bot: A built-in "Discovery Bot" to query your data using simple text prompts.

🐍 The Master Script
This script performs the cleaning, transformation, and visualization automatically.

Python

import pandas as pd
import matplotlib.pyplot as plt

try:
    # 1. LOAD
    df = pd.read_csv('moringa_toolkit.csv')
    
    # 2. CLEAN
    df['Book_Title'] = df['Book_Title'].str.strip().str.title()
    df = df.drop_duplicates()
    df['Price'] = df['Price'].fillna(df['Price'].median())
    df['Quantity'] = df['Quantity'].fillna(1)

    # 3. TRANSFORM
    df['Total_Revenue'] = df['Price'] * df['Quantity']

    # 4. VISUALIZE
    top_books = df.groupby('Book_Title')['Total_Revenue'].sum().sort_values(ascending=False)
    top_books.head(5).plot(kind='bar', color='skyblue', title='Top 5 Books by Revenue')
    plt.ylabel('Revenue ($)')
    plt.show()

except FileNotFoundError:
    print("Error: Ensure 'moringa_toolkit.csv' is in the folder!")
🤖 Interactive Data Bot (Bonus)
We added a "Themed Hello World" chatbot to allow users to interact with the data without writing extra code.

How to run it: Call the data_bot() function in your notebook. It will prompt you for input:

1: View Total Sales Revenue.

2: Identify the Top Selling Book.

3: See Total Quantity Sold.

🧪 Testing & Quality Assurance
To ensure the toolkit remains functional, the following tests were performed:

Data Integrity Check: Verified the final output contained zero null values.

Path Validation: Confirmed the script handles missing files gracefully.

Transformation Accuracy: Manually verified the formula

Total_Revenue=Price×Quantity
.

Visualization Logic: Confirmed the bar chart displays the Top 5 items correctly.

🔄 Iteration History
V1.0: Basic data loading.

V1.1: Added cleaning and standardization logic.

V1.2: Integrated Matplotlib reporting.

V1.3 (Final): Added Error Handling and the Interactive Data Bot.

📚 References
Alex The Analyst. (2023). Pandas for Beginners

Pandas Development Team. (2025). Pandas User Guide