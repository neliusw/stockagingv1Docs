# Readme

## Stock Age Calculations

### 1.1 EOQ (Economic Order Quantity)

<details>

<summary>
Calculates the optimal order quantity to minimize the total inventory costs, including ordering and holding costs. Helps users reduce inventory costs and avoid overstocking or under-stocking.
</summary>

EndpointName: `/stock-age/eoq`

Excel Formula: `StockAgeEOQ("APIKEY", demand_rate, order_cost, holding_cost)`

API Input:

```json
{
  "demand_rate": 1000,
  "order_cost": 50,
  "holding_cost": 5
}
```

API Output:

```json
Copy code
{
  "eoq": 200
}
```
</details>

### 1.2 FIFO Report (First-In, First-Out)

<details>
<summary>
Generates a report based on the FIFO inventory method, where the oldest stock is sold first. Ensures accurate inventory valuation and compliance with accounting standards.
</summary>

EndpointName: `/stock-age/fifo-report`

Excel Formula: `StockAgeFIFO("APIKEY", receipts, total_sales)`

API Input:

```json
Copy code
{
  "receipts": [100, 200, 300],
  "total_sales": 150
}
```

API Output:

```json
Copy code
{
  "fifo_report": [100, 200, 150]
}
```

</details>

### 1.3 LIFO Report (Last-In, First-Out)

<details>
<summary>Generates a report based on the LIFO inventory method, where the most recently added stock is sold first. Provides an alternative inventory valuation method, beneficial in inflationary environments for tax purposes.</summary>

EndpointName: `/stock-age/lifo-report`

Excel Formula: `StockAgeLIFO("APIKEY", receipts, total_sales)`

API Input:

```json
{
  "receipts": [100, 200, 300],
  "total_sales": 150
}
```

API Output:
```json

{
  "lifo_report": [300, 150, 0]
}
```

</details>

### 1.4 Reorder Point

<details>
<summary>Calculates the inventory level at which a new order should be placed to avoid stockouts. Helps maintain optimal inventory levels and ensures product availability.</summary>

EndpointName: `/stock-age/reorder-point`

Excel Formula: `StockAgeReorderPoint("APIKEY", lead_time_demand, safety_stock)`

API Input:

```json
{
  "lead_time_demand": 500,
  "safety_stock": 100
}
```

API Output:

```json
{
  "reorder_point": 600
}
```

</details>

### 1.5 Stock Age Report

<details>
<summary>Provides an analysis of the age of inventory items. Helps identify slow-moving or obsolete stock, aiding in inventory management decisions.</summary>

EndpointName: `/stock-age/report`

Excel Formula: `StockAgeReport("APIKEY", receipts, current_date)`

API Input:

```json
{
  "receipts": [
    {"date": "2023-01-01", "quantity": 100},
    {"date": "2023-02-01", "quantity": 200},
    {"date": "2023-03-01", "quantity": 300}
  ],
  "current_date": "2024-06-01"
}
```

API Output:

```json
{
  "stock_age_report": [
    {"date": "2023-01-01", "age": 517},
    {"date": "2023-02-01", "age": 486},
    {"date": "2023-03-01", "age": 456}
  ]
}
```

</details>

### 1.6 Turnover Ratio

<details>
<summary>Measures how often inventory is sold and replaced over a period. Indicates inventory efficiency and product demand.</summary>

EndpointName: `/stock-age/turnover-ratio`

Excel Formula: `StockAgeTurnoverRatio("APIKEY", cost_of_goods_sold, average_inventory)`

API Input:

```json
{
  "cost_of_goods_sold": 10000,
  "average_inventory": 2000
}
```
API Output:

```json
{
  "turnover_ratio": 5
}
```
</details>

### 1.7 Weighted Average Cost

<details>
<summary>Calculates the average cost of inventory items based on their purchase cost and quantity.  Provides a balanced view of inventory valuation, useful for pricing and financial reporting.</summary>

EndpointName: `/stock-age/weighted-average-cost`

Excel Formula: `StockAgeWeightedAverageCost("APIKEY", receipts, quantities)`

API Input:

```json

{
  "receipts": [100, 200, 300],
  "quantities": [10, 20, 30]
}
```
API Output:

```json

{
  "weighted_average_cost": 233.33
}
```
</details>

## 2. Advanced Stock Metrics

### 2.1 Get Reorder Status

<details>
<summary>Checks the status of inventory items against their reorder points. Helps prevent stock-outs and ensures timely reordering.</summary>

EndpointName: `/stock-metrics/reorder-status`

Excel Formula: `GetReorderStatus("APIKEY", stock_levels, reorder_points)`

API Input:

```json
{
  "stock_levels": [100, 50, 30],
  "reorder_points": [50, 50, 40]
}
```

API Output:

```json
{
  "reorder_status": ["No", "Yes", "Yes"]
}
```

</details>

### 2.2 Get Stock Valuation

<details>
<summary>Provides the current valuation of inventory based on various accounting methods. Assists in accurate financial reporting and asset management.</summary>

EndpointName: `/stock-metrics/valuation`

Excel Formula: `GetStockValuation("APIKEY", stock_levels, unit_costs)`

API Input:

```json
{
  "stock_levels": [100, 200, 300],
  "unit_costs": [10, 15, 20]
}
```

API Output:

```json
{
  "stock_valuation": 10000
}
```

</details>

### 2.3 Get Stock Turnover

<details>
<summary>Measures how frequently inventory is sold within a period. Indicates sales performance and inventory efficiency.</summary>

EndpointName: `/stock-metrics/turnover`

Excel Formula: `GetStockTurnover("APIKEY", sales, inventory)`

API Input:

```json
{
  "sales": 5000,
  "inventory": 1000
}
```

API Output:

```json
{
  "turnover": 5
}
```

</details>

### 2.4 Get Stock Turnover Ratio

<details>
<summary>Calculates the ratio of cost of goods sold to average inventory. Helps assess how effectively inventory is managed and sold.</summary>

EndpointName: `/stock-metrics/turnover-ratio`

Excel Formula: `GetStockTurnoverRatio("APIKEY", cost_of_goods_sold, average_inventory)`

API Input:

```json
{
  "cost_of_goods_sold": 10000,
  "average_inventory": 2500
}
```

API Output:

```json
{
  "turnover_ratio": 4
}
```

</details>

### 2.5 Get Stock Availability

<details>
<summary>Provides information on the current availability of inventory items. Ensures product availability and customer satisfaction.</summary>

EndpointName: `/stock-metrics/availability`

Excel Formula: `GetStockAvailability("APIKEY", product_ids)`

API Input:

```json
{
  "product_ids": ["A1", "B2", "C3"]
}
```

API Output:

```json
{
  "availability": ["In Stock", "Out of Stock", "In Stock"]
}
```
</details>

### 2.6 Get Backorder Status

<details>
<summary>Checks the status of backordered items. Helps manage customer expectations and supply chain efficiency.</summary>

EndpointName: `/stock-metrics/backorder-status`

Excel Formula: `GetBackorderStatus("APIKEY", product_ids)`

API Input:

```json
{
  "product_ids": ["A1", "B2", "C3"]
}
```

API Output:

```json
{
  "backorder_status": ["No", "Yes", "No"]
}
```

</details>

### 2.7 Get Stock Performance

<details>
<summary>Analyzes the performance of inventory items based on sales and turnover. Identifies top-performing and underperforming products.</summary>

EndpointName: `/stock-metrics/performance`

Excel Formula: `GetStockPerformance("APIKEY", product_ids, sales_data)`

API Input:

```json
{
  "product_ids": ["A1", "B2", "C3"],
  "sales_data": [100, 200, 150]
}
```

API Output:

```json
{
  "performance": ["Good", "Excellent", "Average"]
}
```
</details>

### 2.8 Get Demand Forecast

<details>
<summary>Predicts future demand for inventory items based on historical data and trends. Aids in inventory planning and reduces the risk of stockouts or overstocking.</summary>

EndpointName: `/stock-metrics/demand-forecast`

Excel Formula: `GetDemandForecast("APIKEY", historical_sales)`

API Input:

```json
{
  "historical_sales": [500, 600, 700, 800]
}
```

API Output:

```json
{
  "demand_forecast": 750
}
```
</details>

### 2.9 Get Stock Discrepancy

<details>
<summary>Identifies discrepancies between recorded and actual inventory levels. Helps maintain inventory accuracy and reduce shrinkage.</summary>

EndpointName: `/stock-metrics/discrepancy`

Excel Formula: `GetStockDiscrepancy("APIKEY", system_stock, actual_stock)`

API Input:

```json
{
  "system_stock": [100, 200, 300],
  "actual_stock": [90, 210, 295]
}
```
API Output:

```json
{
  "discrepancy": [-10, 10, -5]
}
```
</details>

### 2.10 Get Supplier Performance

<details>
<summary>Evaluates suppliers based on their delivery performance and product quality. Enhances supply chain reliability and efficiency.</summary>

EndpointName: `/stock-metrics/supplier-performance`

Excel Formula: `GetSupplierPerformance("APIKEY", supplier_ids, delivery_times)`

API Input:

```json
{
  "supplier_ids": ["S1", "S2", "S3"],
  "delivery_times": [5, 7, 10]
}
```

API Output:

```json
{
  "performance": ["Excellent", "Good", "Poor"]
}
```
</details>

### 2.11 Get Inventory Turnover Days

<details>
<summary>Calculates the average number of days it takes to sell inventory. Provides insight into inventory liquidity and sales cycle.</summary>

EndpointName: `/stock-metrics/inventory-turnover-days`

Excel Formula: `GetInventoryTurnoverDays("APIKEY", cost_of_goods_sold, average_inventory)`

API Input:

```json
{
  "cost_of_goods_sold": 10000,
  "average_inventory": 2000
}
```

API Output:

```json
{
  "turnover_days": 73
}
```
</details>

### 2.12 Get Stock Cost Analysis

<details>
<summary>Analyzes the cost structure of inventory items. Helps optimize pricing strategies and cost management.</summary>

EndpointName: `/stock-metrics/cost-analysis`

Excel Formula: `GetStockCostAnalysis("APIKEY", product_ids, costs)`

API Input:

```json
{
  "product_ids": ["A1", "B2", "C3"],
  "costs": [1000, 2000, 3000]
}
```

API Output:

```json
{
  "cost_analysis": [1000, 2000, 3000]
}
```
</details>

### 2.13 Get Safety Stock Level

<details>
<summary>Calculates the minimum level of inventory required to prevent stockouts. Ensures continuous product availability and customer satisfaction.</summary>

EndpointName: `/stock-metrics/safety-stock-level`

Excel Formula: `GetSafetyStockLevel("APIKEY", demand_variability, lead_time_variability, service_level)`

API Input:

```json
{
  "demand_variability": 50,
  "lead_time_variability": 10,
  "service_level": 95
}
```

API Output:

```json
{
  "safety_stock_level": 75
}
```

</details>

## 3. Inventory Optimization

### 3.1 Stock Holding

<details>
<summary>Analyzes the current stock holding levels. Helps manage inventory levels efficiently and reduce holding costs.</summary>

EndpointName: `/inventory-optimization/stock-holding`

Excel Formula: `InventoryStockHolding("APIKEY", product_ids, stock_levels)`

API Input:

```json
{
  "product_ids": ["A1", "B2", "C3"],
  "stock_levels": [100, 200, 300]
}
```

API Output:

```json
{
  "stock_holding": [100, 200, 300]
}
```

</details>

### 3.2 Excess Stock

<details>
<summary>Identifies items that are overstocked. Helps reduce excess inventory and free up capital.</summary>

EndpointName: `/inventory-optimization/excess-stock`

Excel Formula: `InventoryExcessStock("APIKEY", stock_levels, excess_threshold)`

API Input:

```json
{
  "stock_levels": [100, 200, 300],
  "excess_threshold": 150
}
```

API Output:

```json
{
  "excess_stock": [0, 50, 150]
}
```

</details>

### 3.3 Over Stock

<details>
<summary>Analyzes inventory levels that exceed the required amount. Identifies potential waste and helps in inventory reduction strategies.</summary>

EndpointName: `/inventory-optimization/over-stock`

Excel Formula: `InventoryOverStock("APIKEY", stock_levels, optimal_stock)`

API Input:

```json
{
  "stock_levels": [100, 200, 300],
  "optimal_stock": 150
}
```

API Output:

```json
{
  "over_stock": [0, 50, 150]
}
```

</details>

### 3.4 Surplus Orders

<details>
<summary>Identifies surplus orders that exceed demand. Helps in aligning orders with actual demand to avoid overstocking.</summary>

EndpointName: `/inventory-optimization/surplus-orders`

Excel Formula: `InventorySurplusOrders("APIKEY", order_quantities, demand_forecast)`

API Input:

```json
{
  "order_quantities": [150, 250, 350],
  "demand_forecast": 200
}
```

API Output:

```json
{
  "surplus_orders": [0, 50, 150]
}
```
</details>

### 3.5 Potential Stock Outs

<details>
<summary>Predicts items that are at risk of stockouts. Helps take proactive measures to replenish stock and avoid lost sales.</summary>

EndpointName: `/inventory-optimization/potential-stock-outs`

Excel Formula: `InventoryPotentialStockOuts("APIKEY", stock_levels, reorder_points)`

API Input:

```json
{
  "stock_levels": [50, 60, 70],
  "reorder_points": [100, 60, 80]
}
```

API Output:

```json
{
  "potential_stock_outs": [50, 0, 10]
}
```

</details>

### 3.6 Automatic Inventory Classification

<details>
<summary>Automatically classifies inventory items based on sales value and velocity. Provides an intuitive matrix of product importance, aiding in inventory prioritization.</summary>

EndpointName: `/inventory-optimization/automatic-classification`

Excel Formula: `InventoryAutoClassification("APIKEY", product_ids, sales_value, sales_velocity)`

API Input:

```json
{
  "product_ids": ["A1", "B2", "C3"],
  "sales_value": [1000, 1500, 2000],
  "sales_velocity": [5, 10, 15]
}
```

API Output:

```json
{
  "classification": ["A", "B", "C"]
}
```
</details>

### 3.7 Monitor and Measure Product-Specific Lead Times

<details>
<summary>Tracks and measures lead times for individual products. Helps optimize ordering schedules and improve supply chain efficiency.</summary>

EndpointName: `/inventory-optimization/lead-time-monitor`

Excel Formula: `MonitorLeadTime("APIKEY", product_ids, lead_times)`

API Input:

```json
{
  "product_ids": ["A1", "B2", "C3"],
  "lead_times": [5, 7, 10]
}
```

API Output:

```json
{
  "lead_time_monitor": [5, 7, 10]
}
```
</details>

### 3.8 Measure and Adjust Lead Time per Item

<details>
<summary>Measures and adjusts lead time for each inventory item based on performance. Ensures accurate lead time estimation and better inventory planning.</summary>

EndpointName: `/inventory-optimization/lead-time-adjustment`

Excel Formula: `AdjustLeadTime("APIKEY", product_ids, actual_lead_times)`

API Input:

```json
{
  "product_ids": ["A1", "B2", "C3"],
  "actual_lead_times": [4, 6, 9]
}
```

API Output:

```json
{
  "lead_time_adjustment": [4, 6, 9]
}
```
</details>
