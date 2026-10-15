# Data

The raw dataset isn't committed to this repo. Download it and place it in this folder before running the notebook.

## Where to get it

**DataCo Smart Supply Chain for Big Data Analysis**

- Kaggle: https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis
- Mendeley Data (original source): https://data.mendeley.com/datasets/8gx2fvg2k6/5
- Authors: Fabian Constante, Fernando Silva and António Pereira
- Check the licence shown on the dataset page before sharing or redistributing any of the data.

## Files to place here

| File | Needed | Notes |
|---|---|---|
| `DataCoSupplyChainDataset.csv` | Yes | The main file: 180,519 order lines and 53 columns |
| `DescriptionDataCoSupplyChain.csv` | Optional | Describes each column |
| `tokenized_access_logs.csv` | No | Clickstream data, not used in this project |

The main file is encoded as latin-1, not UTF-8. The notebook handles this when it loads the file.

## About the dataset

- **Coverage:** order lines from 1 Jan 2015 to 31 Jan 2018 (65,752 distinct orders).
- **Content:** orders, products, customers, shipping, delivery status and profit, across five markets and clothing, sports and electronics categories.
- **Grain:** one row per order line. An order can have several lines.

### Main columns used

| Column | Meaning |
|---|---|
| `Order Id`, `order date (DateOrders)`, `shipping date (DateOrders)` | Order identifier and dates |
| `Delivery Status` | Advance shipping, Late delivery, Shipping canceled or Shipping on time |
| `Days for shipment (scheduled)`, `Days for shipping (real)` | Promised and actual delivery days |
| `Shipping Mode` | Standard Class, First Class, Second Class or Same Day |
| `Market`, `Order Region` | Where the order is delivered |
| `Sales`, `Order Profit Per Order`, `Order Item Discount Rate` | Value, profit and discount of each line |
| `Category Name`, `Product Name`, `Product Price` | Product details |
| `Order Status`, `Customer Segment`, `Type` | Order state, customer type and transaction type |

## Data handling

- **Personal fields are removed.** The notebook drops customer name, email, password and street, plus the product image link, before any analysis.
- **Two empty columns are dropped:** `Product Description` (100% missing) and `Order Zipcode` (86.2% missing).
- **The cleaned file (`output/clean_orders.csv`) is not committed**, as it's large and derived from the raw data. Run the notebook to regenerate it.

## Known quirks

- The data changes shape from October 2017: every order has a single line, and average line value and monthly sales shift sharply. The notebook documents this and restricts the forecast to the earlier period.
- Several fields look rule-generated (for example, each of the 18 discount levels appears on almost exactly the same number of lines), so results should be read as patterns in this dataset.