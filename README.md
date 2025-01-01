# Exploring API with Python

This project demonstrates how to interact with the Alpha Vantage API to retrieve various types of financial data, including stock market data, cryptocurrency prices, economic indicators, and more. The project uses both the `alpha_vantage` Python package and raw `requests` library calls.

## Getting Started

### Prerequisites
1. Obtain a free API key from Alpha Vantage: [Alpha Vantage API Key](https://www.alphavantage.co/support/#api-key)
2. Install the required Python libraries:
    ```bash
    pip install alpha_vantage requests beautifulsoup4 pandas
    ```

### Setup
1. Save your API key in a file named `API_key.txt` in the same directory as the notebook.
   ```plaintext
   YOUR_API_KEY
   ```
2. Ensure your working directory contains the `.ipynb` file and the `API_key.txt` file.

## Features

### Stock Data Retrieval
- **Monthly Data**: Retrieve monthly stock data for a specified symbol (e.g., Microsoft).
- **Weekly Data**: Retrieve weekly stock data.
- **Intraday Data**: Retrieve stock data at specific intervals (e.g., 60 minutes).

### Fundamental Data Retrieval
- Income statements and cash flow statements for a specified company.

### Foreign Exchange Rates
- Real-time and historical exchange rates for currency pairs (e.g., USD to EUR).

### Cryptocurrency Data
- Weekly prices of cryptocurrencies (e.g., Bitcoin in EUR).

### Economic Indicators
- U.S. quarterly GDP, monthly CPI, and unemployment rates.

### News & Sentiment Analysis
- Fetch news and sentiment analysis for a specific stock ticker.

### Technical Indicators
- Calculate technical indicators such as:
  - Simple Moving Average (SMA)
  - Weighted Moving Average (WMA)
  - Rate of Change Ratio (ROCR)
  - Bollinger Bands (BBANDS)

## Usage Examples

### Using `alpha_vantage` Package
```python
from alpha_vantage.timeseries import TimeSeries

# Initialize TimeSeries object
ts = TimeSeries(key=API_key)

# Get monthly stock data
monthly_data, meta_data = ts.get_monthly('MSFT')
print(monthly_data.head())
```

### Using `requests` Library
```python
import requests
import pandas as pd
import io

# Fetch weekly stock data as CSV
url = "https://www.alphavantage.co/query?function=TIME_SERIES_WEEKLY&symbol=MSFT&apikey=" + API_key + "&datatype=csv"
response = requests.get(url)
data = pd.read_csv(io.StringIO(response.content.decode('utf-8')))
print(data.head())
```

## Notes
- The free API key has a limit of 25 requests per day.
- Ensure you handle API rate limits to avoid exceeding the quota.

## Project Structure
- `API_key.txt`: Contains the Alpha Vantage API key.
- `api.ipynb`: The Jupyter notebook demonstrating API usage and data retrieval.

## References
- [Alpha Vantage API Documentation](https://www.alphavantage.co/documentation/)

