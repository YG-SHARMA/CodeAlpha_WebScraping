# CodeAlpha_WebScraping
# 🌐 Web Scraping Project Using Python

A Python-based web scraping project that demonstrates how to extract information from a website using **Requests**, **BeautifulSoup**, and **Pandas**.

The project sends an HTTP request to the GeeksforGeeks website, parses the returned HTML content, extracts HTML elements, and demonstrates how scraped data can be converted into a Pandas DataFrame and exported as a CSV file.

---

## 📌 Project Overview

Web scraping is the process of automatically collecting information from websites.

In this project, Python is used to:

* Send HTTP requests to a website
* Retrieve HTML content
* Parse HTML using BeautifulSoup
* Extract headings and page elements
* Identify structured product information
* Store scraped information in a Pandas DataFrame
* Export the collected data to a CSV file

The notebook uses the following website as the scraping target:

**GeeksforGeeks:** https://www.geeksforgeeks.org/

---

## 🎯 Objectives

The main objectives of this project are:

1. Understand the basics of web scraping.
2. Learn how to send HTTP requests using Python.
3. Parse HTML using BeautifulSoup.
4. Extract information from HTML tags.
5. Convert scraped data into a Pandas DataFrame.
6. Export data into CSV format.
7. Understand how website HTML structure affects scraping.

---

## 🛠️ Technologies Used

| Technology       | Purpose                                |
| ---------------- | -------------------------------------- |
| Python           | Programming language                   |
| Requests         | Sending HTTP requests                  |
| BeautifulSoup    | Parsing HTML                           |
| Pandas           | Data processing and DataFrame creation |
| Jupyter Notebook | Development environment                |

---

## 📂 Project Structure

```text
Web-Scraping-Project/
│
├── WebScraping_project.ipynb
├── products.csv
└── README.md
```

---

## 📦 Installation

Make sure Python is installed on your system.

Install the required libraries:

```bash
pip install requests beautifulsoup4 pandas
```

If you are using Jupyter Notebook:

```bash
pip install notebook
```

---

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/YG_SHARMA/Web-Scraping-Project.git
```

### 2. Navigate to the Project Folder

```bash
cd Web-Scraping-Project
```

### 3. Install Dependencies

```bash
pip install requests beautifulsoup4 pandas
```

### 4. Open the Notebook

```bash
jupyter notebook
```

Then open:

```text
WebScraping_project.ipynb
```

Run the notebook cells sequentially.

---

## 🔄 Project Workflow

```text
Website
   ↓
HTTP Request
   ↓
HTML Response
   ↓
BeautifulSoup
   ↓
HTML Parsing
   ↓
Data Extraction
   ↓
Pandas DataFrame
   ↓
CSV File
```

---

## 💻 Implementation

### Step 1 — Import Requests

```python
import requests
```

The `requests` library is used to send HTTP requests to the target website.

---

### Step 2 — Send Request

```python
url = "https://www.geeksforgeeks.org/"
response = requests.get(url)
```

The project sends a GET request to the website and receives its HTML response.

---

### Step 3 — Check Response

```python
print(response.status_code)
print(response.text[:500])
```

A successful HTTP request returns status code:

```text
200
```

The first part of the HTML response can then be inspected.

---

### Step 4 — Parse HTML

```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(response.text, "html.parser")
```

BeautifulSoup converts the HTML response into a structure that can be searched and navigated.

---

### Step 5 — Extract HTML Elements

For example:

```python
title = soup.find("h1")
print(title.text.strip())
```

The notebook also demonstrates accessing heading elements such as:

```python
soup.h1.text
soup.h2.text
```

---

### Step 6 — Extract Structured Data

The notebook demonstrates searching for elements using:

```python
products = soup.find_all("div", class_="product")
```

For each product, it attempts to extract:

```python
name = product.find("h2").text.strip()
price = product.find("span", class_="price").text.strip()
```

The extracted values are stored as dictionaries:

```python
data.append({
    "Product": name,
    "Price": price
})
```

---

### Step 7 — Create DataFrame

```python
import pandas as pd

df = pd.DataFrame(data)

print(df.head())
```

The scraped data is converted into a Pandas DataFrame for further analysis.

---

### Step 8 — Export to CSV

```python
df.to_csv("products.csv", index=False)
```

This saves the extracted data into:

```text
products.csv
```

---

## ⚠️ Important Note

The current notebook demonstrates the **concept of structured product scraping**, but the selected GeeksforGeeks page does not contain matching elements for:

```python
<div class="product">
```

As a result, the current notebook produces an empty DataFrame:

```text
Empty DataFrame
Columns: []
Index: []
```

This is visible in the uploaded notebook output.

This happens because web scraping depends on the actual HTML structure of the target page. If the website structure changes or the selected page does not contain the expected HTML classes/tags, the scraper will not find the requested elements.

---

## 📊 Current Project Features

The current implementation includes:

* ✅ HTTP request handling
* ✅ Website response validation
* ✅ HTML parsing
* ✅ Heading extraction
* ✅ HTML element searching
* ✅ Data extraction structure
* ✅ Pandas DataFrame creation
* ✅ CSV export

---

## 🔮 Future Improvements

This project can be extended into a more advanced web scraping system.

### 1. Extract Article Data

Instead of product data, extract:

* Article titles
* Article categories
* Author names
* Publication dates
* Article links
* Article descriptions

### 2. URL Extraction

Collect links from the website:

```python
links = soup.find_all("a", href=True)

for link in links:
    print(link["href"])
```

### 3. Data Cleaning

Clean scraped text using:

* Duplicate removal
* Missing-value handling
* Text normalization
* Whitespace removal

### 4. Data Analysis

Use Pandas to calculate:

* Number of articles
* Number of categories
* Average title length
* Most common categories
* Duplicate records

### 5. Visualization

Use Matplotlib/Seaborn to create:

* Category distribution
* Article count by category
* Title-length distribution
* Top categories

### 6. Pagination

Scrape multiple pages instead of only one page.

### 7. Error Handling

Add exception handling for:

* Connection errors
* Timeout errors
* Missing HTML elements
* Invalid URLs
* HTTP errors

Example:

```python
try:
    response = requests.get(url, timeout=10)
    response.raise_for_status()
except requests.RequestException as e:
    print("Error:", e)
```

### 8. Advanced Scraping

For JavaScript-rendered websites, tools such as **Selenium** or **Playwright** can be explored.

---

## 🔐 Ethical Web Scraping

When scraping websites:

* Respect the website's Terms of Service.
* Check `robots.txt`.
* Avoid sending excessive requests.
* Use reasonable delays between requests.
* Do not collect private or sensitive information.
* Use scraped data responsibly.

---

## 📚 Learning Outcomes

After completing this project, you will understand:

* Basics of web scraping
* HTTP requests
* HTML structure
* HTML parsing
* CSS classes and HTML tags
* BeautifulSoup selectors
* Data extraction
* Pandas DataFrames
* CSV data storage
* Basic web scraping limitations

---

## 👨‍💻 Author

**Yogesh Sharma**

Data Science Student | Python | SQL | Power BI | Machine Learning

---

## ⭐ Future Scope

This project can be converted into a complete **Web Scraping + Data Analysis + Machine Learning pipeline**:

```text
Website
   ↓
Web Scraping
   ↓
Data Cleaning
   ↓
Data Validation
   ↓
Exploratory Data Analysis
   ↓
Visualization
   ↓
Feature Engineering
   ↓
Machine Learning
   ↓
Insights
```

---

## 📄 License

This project is created for educational and learning purposes.
