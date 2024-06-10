The attached file historical_data.csv contains a subset of deliveries received in early 2015 in a subset of the cities. Each row in this file corresponds to one unique delivery. Each column corresponds to a feature as explained below. Note all money (dollar) values given in the data are in cents and all time duration values given are in seconds

**The target value to predict here is the total minutes value between `created_at` and `actual_delivery_time`.**

## Columns in historical_data.csv

### Time features
- `market_id`: A city/region in which operates, given in the data as an id
- `created_at`: Timestamp in UTC when the order was submitted by the consumer
- `actual_delivery_time`: Timestamp in UTC when the order was delivered to the consumer

### Store features
- `store_id`: an id representing the restaurant the order was submitted for
- `store_primary_category`: cuisine category of the restaurant, e.g., italian, asian
- `order_protocol`: a store can receive orders through many modes. This field represents an id denoting the protocol

### Order features
- `total_items`: total number of items in the order
- `subtotal`: total value of the order submitted (in cents)
- `num_distinct_items`: number of distinct items included in the order
- `min_item_price`: price of the item with the least cost in the order (in cents)
- `max_item_price`: price of the item with the highest cost in the order (in cents)

### Market features
There's information on the state of marketplace when the order is placed, that can be used to estimate delivery time. The following features are values at the time of `created_at` (order submission time):

- `total_onshift_dashers`: Number of available dashers who are within 10 miles of the store at the time of order creation
- `total_busy_dashers`: Subset of above `total_onshift_dashers` who are currently working on an order
- `total_outstanding_orders`: Number of orders within 10 miles of this order that are currently being processed.

### Predictions from other models
Predictions from other models for various stages of delivery process that can be used:

- `estimated_order_place_duration`: Estimated time for the restaurant to receive the order (in seconds)
- `estimated_store_to_consumer_driving_duration`: Estimated travel time between store and consumer (in seconds)