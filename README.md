# Data Engineering Dimensinal Modeling
Fork this repo into your github.

The goal for this project was to get a flat file dataset and transform it to a dimensional model, with fact and dimension tables.

# Instructions
You may use the pandas index feature to generte the dimension surrogate ids.
e.g.
   ```customer_dim = df[['customer']].reset_index(drop=True)
   customer_dim['customer_id'] = customer_dim.index``` 

1) Setup a date dimension table and link it to pickup and dropoff date
2) Setup a location dimension by truncating the latitude, longitude to 2 decimal points, and forming the pair as 1 location_id.
   e.g. (-73.45222, 46.1482) becomes (-73.45, 46.15) and this co-ordinate pair becomes a location_id.
3) Create a field called trip_id, which is just the row_number, identifying each trips. This will be your fact_id.
4) Setup a rate-code table, and payment_type as a lookup dimension table, using the rate code & payment type info in the pdf.
5) Build the fact table by joining back all the dimensions you  built back to the original dataframe using their natural keys. Drop the natural keys, leaving the surrogate_ids as foreign keys. 


This project was taken from a Youtube channel - https://www.youtube.com/watch?v=WpQECq5Hx9g&t=5429s
