# pysparkNotes


```python
# create a spark dataframe from sql query
sqlDF = spark.sql("SELECT * FROM smartride.gps_trippoint_delta")
```

```python 
# subset a dataframe of only distinct values in 'trip_nb' column
trip_numbers = sqlDF.select('trip_nb').distinct()
```

```python
# convert a spark df to a pandas df
df_trip = oneTrip.toPandas()
pandas_df = df_trip[['trip_nb', 'vssspeed_am']]
pandas_df.head()

Out[113]: 
        trip_nb  vssspeed_am
0  404650791293          NaN
1  404650791293          0.0
2  404650791293          0.0
3  404650791293          0.0
4  404650791293          0.0
```

```python
# subset dataframe from a list of 1000 distinct trip numbers
trips_1k = trip_numbers.head(1000)
nums_1k = []
for trip in trips_1k:
  nums_1k.append(str(trip.trip_nb))
df_1k = sqlDF[sqlDF['trip_nb'].isin(nums_1k)]
```
