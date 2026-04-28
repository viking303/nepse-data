# NEPSE Daily Data

Automated daily scrape of Nepal Stock Exchange (NEPSE) data from
[merolagani.com](https://merolagani.com). Updated every weekday at
3:15 PM NPT via GitHub Actions.

## Folder Structure

```
nepse-data/
├── daily_price_data/          ← daily stock prices
│   └── data_YYYY-MM-DD_todays_price.csv
├── nepse_daily_floorsheet/    ← daily floorsheet transactions
│   └── floorsheet_YYYY-MM-DD.csv
└── last_updated.txt           ← timestamp of last successful run
```

## Data: `daily_price_data/`

One CSV per trading day. Filename: `data_YYYY-MM-DD_todays_price.csv`

| Column | Type | Description |
|---|---|---|
| Date | string | Scrape date in NPT (YYYY-MM-DD) |
| # | integer | Serial number |
| Symbol | string | Stock ticker symbol (e.g. NABIL, NICA) |
| LTP | float | Last traded price (NPR) |
| % Change | float | Price change from previous close |
| High | float | Day's highest price (NPR) |
| Low | float | Day's lowest price (NPR) |
| Open | float | Opening price (NPR) |
| Qty. | integer | Total quantity traded |
| Turnover | float | Total turnover (NPR) |
| Page | integer | Source page number |

## Data: `nepse_daily_floorsheet/`

One CSV per trading day. Filename: `floorsheet_YYYY-MM-DD.csv`

| Column | Type | Description |
|---|---|---|
| Date | string | Scrape date in NPT (YYYY-MM-DD) |
| # | integer | Serial number |
| Transact. No. | string | Unique transaction number |
| Symbol | string | Stock ticker symbol (e.g. NABIL, NICA) |
| Buyer | integer | Broker number of buyer |
| Seller | integer | Broker number of seller |
| Quantity | integer | Number of shares traded |
| Rate | float | Price per share (NPR) |
| Amount | float | Total transaction amount (NPR) |
| Page | integer | Source page number |

## Update Schedule

- **Frequency:** Every weekday (Monday–Friday)
- **Time:** ~3:15 PM NPT (Nepal Time, UTC+5:45)
- **Source:** [merolagani.com](https://merolagani.com)
- **Market:** Nepal Stock Exchange (NEPSE)

## Usage Examples

### Python
```python
import pandas as pd

# Load latest daily price
df = pd.read_csv("daily_price_data/data_2025-04-29_todays_price.csv")

# Load latest floorsheet
fs = pd.read_csv("nepse_daily_floorsheet/floorsheet_2025-04-29.csv")
```

### Direct CSV URL
```
https://raw.githubusercontent.com/viking303/nepse-data/main/daily_price_data/data_YYYY-MM-DD_todays_price.csv
https://raw.githubusercontent.com/viking303/nepse-data/main/nepse_daily_floorsheet/floorsheet_YYYY-MM-DD.csv
```

## Notes
- NEPSE trades Monday-friday in Nepal
- All prices are in Nepali Rupees (NPR)
- Data is scraped as-is from merolagani.com — no modifications
-This is for edutional purposes only
