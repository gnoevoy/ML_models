# Dataset overview
The attached file dataset.csv contains a subset of deliveries in a subset of the cities. Each row in this file corresponds to one unique delivery. Note all money (dollar) values given in the data are in cents and all time duration values given are in seconds
**The target value to predict here is the total minutes value between `created_at` and `actual_delivery_time`.**

## Columns Explanations

### Time features

| Column Name             | Description                                                |
|-------------------------|------------------------------------------------------------|
| `market_id`             | A city/region in which operates, given in the data as an id|
| `created_at`            | Timestamp in UTC when the order was submitted by the consumer|
| `actual_delivery_time`  | Timestamp in UTC when the order was delivered to the consumer|

### Store features

| Column Name             | Description                                                |
|-------------------------|------------------------------------------------------------|
| `store_id`              | An id representing the restaurant the order was submitted for|
| `store_primary_category`| Cuisine category of the restaurant, e.g., Italian, Asian    |
| `order_protocol`        | A store can receive orders through many modes. This field represents an id denoting the protocol|

### Order features

| Column Name             | Description                                                |
|-------------------------|------------------------------------------------------------|
| `total_items`           | Total number of items in the order                          |
| `subtotal`              | Total value of the order submitted (in cents)               |
| `num_distinct_items`    | Number of distinct items included in the order              |
| `min_item_price`        | Price of the item with the least cost in the order (in cents)|
| `max_item_price`        | Price of the item with the highest cost in the order (in cents)|

### Market features

There's information on the state of the marketplace when the order is placed, that can be used to estimate delivery time. The following features are values at the time of `created_at` (order submission time):

| Column Name               | Description                                                            |
|---------------------------|------------------------------------------------------------------------|
| `total_onshift_dashers`   | Number of available dashers who are within 10 miles of the store at the time of order creation |
| `total_busy_dashers`      | Subset of above `total_onshift_dashers` who are currently working on an order |
| `total_outstanding_orders`| Number of orders within 10 miles of this order that are currently being processed|

### Predictions from other models

| Column Name                                | Description                                                            |
|--------------------------------------------|------------------------------------------------------------------------|
| `estimated_order_place_duration`           | Estimated time for the restaurant to receive the order (in seconds)    |
| `estimated_store_to_consumer_driving_duration`| Estimated travel time between store and consumer (in seconds)       |
