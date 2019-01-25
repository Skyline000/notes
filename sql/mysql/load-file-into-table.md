# Load file into table

```sql
load data local infile 'D:/Users/Desktop/CityU MSc Computer Science/CS5488 Big Data Algorithms and Tech/Project/NYC TLC Trip/yellow_tripdata_2017-01.csv' into table yellow_tripdata_2017_01
 fields terminated by ','
 enclosed by '"'
 lines terminated by '\n'
 IGNORE 1 LINES;
```

