Q3. 
SELECT COUNT(1)
FROM green_taxi_trips
WHERE DATE(lpep_pickup_datetime) = '2019-09-18'
AND DATE(lpep_dropoff_datetime) = '2019-09-18'

Q4. 
SELECT * FROM green_taxi_trips
WHERE DATE(lpep_pickup_datetime) = DATE(lpep_dropoff_datetime)
ORDER BY trip_distance DESC

Q5.
SELECT lookup."Borough", ROUND(SUM(total_amount)) FROM green_taxi_trips as green
INNER JOIN taxi_zone_lookup as lookup
ON green."PULocationID" = lookup."LocationID"
WHERE lookup."Borough" != 'Unknown'
AND DATE(green.lpep_pickup_datetime) = '2019-09-18'
GROUP BY lookup."Borough"

Q6.
SELECT "Zone" from taxi_zone_lookup
WHERE "LocationID" IN (
	SELECT green."DOLocationID" FROM green_taxi_trips as green
	INNER JOIN taxi_zone_lookup as lookup
	ON green."PULocationID" = lookup."LocationID"
	WHERE lookup."Zone" = 'Astoria'
	ORDER BY tip_amount DESC
	LIMIT 1)
