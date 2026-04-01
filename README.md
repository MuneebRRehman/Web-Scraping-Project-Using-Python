# 📊 Largest U.S. Companies Web Scraper

A Python-based web scraping project that extracts data from Wikipedia and converts it into a structured dataset for analysis.

---

## 🚀 Project Overview

This project scrapes the list of the **largest companies in the United States by revenue** from Wikipedia and stores the data in a clean CSV format.

It demonstrates how to:

* Fetch real-world data from a website
* Parse HTML using BeautifulSoup
* Structure data using Pandas
* Export datasets for analysis

---

## 🌐 Data Source

Wikipedia page:
https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue

---

## 🛠️ Tech Stack

* Python
* BeautifulSoup
* Requests
* Pandas

---

## ⚙️ Installation

```bash
pip install beautifulsoup4 requests pandas
```

---

## ▶️ How to Run

1. Clone the repository:

```bash
git clone https://github.com/your-username/largest-us-companies-web-scraper.git
```

2. Navigate to the project folder:

```bash
cd largest-us-companies-web-scraper
```

3. Run the script:

```bash
python scraper.py
```

---

## 💻 Code Example

```python
from bs4 import BeautifulSoup
import requests
import pandas as pd

url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue'

page = requests.get(url, headers={'User-Agent': 'Mozilla/5.0'})
soup = BeautifulSoup(page.text, 'html.parser')

table = soup.find_all('table')[0]

# Extract headers
headers = table.find_all('th')
columns = [title.text.strip() for title in headers]

df = pd.DataFrame(columns=columns)

# Extract rows
rows = table.find_all('tr')

for row in rows[1:]:
    cols = row.find_all('td')
    data = [col.text.strip() for col in cols]
    df.loc[len(df)] = data

# Save to CSV
df.to_csv('output.csv', index=False)
```

---

## 📊 Output

* A CSV file containing:

  * Rank
  * Company Name
  * Industry
  * Revenue
  * Growth
  * Employees
  * Headquarters

---

## 🎯 Learning Outcomes

* Web scraping fundamentals
* HTML structure understanding
* Data cleaning and transformation
* Working with Pandas DataFrames

---

## ⚠️ Common Issues Solved

* ResultSet vs single element errors
* Mismatched DataFrame columns
* File path errors in Python

---

## 🔮 Future Improvements

* Add data visualization
* Automate periodic scraping
* Store data in a database
* Build a dashboard

---

## 🤝 Contributing

Feel free to fork this repo and improve it!

---

## ⭐ Support

If you like this project, give it a star ⭐
