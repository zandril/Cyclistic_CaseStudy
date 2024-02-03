-- combine all 12 datasets into larger dataset called combined_data
CREATE TABLE `2022.2022_combined_data` AS (

SELECT * FROM `2022.2022_01`
UNION ALL
SELECT * FROM `2022.2022_02`
UNION ALL
SELECT * FROM `2022.2022_03`
UNION ALL
SELECT * FROM `2022.2022_04`
UNION ALL
SELECT * FROM `2022.2022_05`
UNION ALL
SELECT * FROM `2022.2022_06`
UNION ALL
SELECT * FROM `2022.2022_07`
UNION ALL
SELECT * FROM `2022.2022_08`
UNION ALL
SELECT * FROM `2022.2022_09`
UNION ALL
SELECT * FROM `2022.2022_10`
UNION ALL
SELECT * FROM `2022.2022_11`
UNION ALL
SELECT * FROM `2022.2022_12`
)
-- next we removed rides that were less than one minute and over 8 hours
SELECT AVG(
  EXTRACT(HOUR FROM ride_length) * 60 +
  EXTRACT(MINUTE FROM ride_length) +
  EXTRACT(SECOND FROM ride_length) / 60.0
) AS avg_ride_length_minutes
FROM `tripdata-2022-412822.2022.combined_2022`;
-- finding the avg trip length, the result showed 16.93 so close to 17 mins
-- min ride value 
SELECT
  MIN(EXTRACT(HOUR FROM ride_length) * 60 +
      EXTRACT(MINUTE FROM ride_length) +
      EXTRACT(SECOND FROM ride_length) / 60.0
  ) AS min_ride_length_minutes
FROM `tripdata-2022-412822.2022.combined_2022`;
-- max ride value
SELECT
  MAX(EXTRACT(HOUR FROM ride_length) * 60 +
      EXTRACT(MINUTE FROM ride_length) +
      EXTRACT(SECOND FROM ride_length) / 60.0
  ) AS max_ride_length_minutes
FROM `tripdata-2022-412822.2022.combined_2022`;
-- looking for rides less than one mintue and over 8 hours
SELECT
  COUNT(*) AS rides_under_1_minute
FROM `tripdata-2022-412822.2022.combined_2022`
WHERE TIMESTAMP_DIFF(ended_at, started_at, SECOND) < 60;

SELECT
  COUNT(*) AS rides_over_8_hours
FROM `tripdata-2022-412822.2022.combined_2022`
WHERE TIMESTAMP_DIFF(ended_at, started_at, SECOND) > 8 * 60 * 60;
-- 2213 rides over one hour and 24280 rides under one minute 

-- Delete rides less than one minute
DELETE FROM `tripdata-2022-412822.2022.combined_2022`
WHERE TIMESTAMP_DIFF(ended_at, started_at, SECOND) < 60;

-- Delete rides over 8 hours
DELETE FROM `tripdata-2022-412822.2022.combined_2022`
WHERE TIMESTAMP_DIFF(ended_at, started_at, SECOND) > 8 * 60 * 60;

-- extract the name of the month and the name of the day for each ride
-- Add a new STRING column for month names
ALTER TABLE `tripdata-2022-412822.2022.combined_2022`
ADD COLUMN month_name STRING;

-- Update the new column with month names
UPDATE `tripdata-2022-412822.2022.combined_2022`
SET month_name = 
  CASE 
    WHEN started_at IS NOT NULL THEN 
      CASE EXTRACT(MONTH FROM TIMESTAMP(started_at))
        WHEN 1 THEN 'January'
        WHEN 2 THEN 'February'
        WHEN 3 THEN 'March'
        WHEN 4 THEN 'April'
        WHEN 5 THEN 'May'
        WHEN 6 THEN 'June'
        WHEN 7 THEN 'July'
        WHEN 8 THEN 'August'
        WHEN 9 THEN 'September'
        WHEN 10 THEN 'October'
        WHEN 11 THEN 'November'
        WHEN 12 THEN 'December'
        ELSE 'Unknown Month'
      END
    ELSE NULL
  END
  WHERE started_at IS NOT NULL;
-- we will add a new column that displays the month and convert the values in day_of_week to display the day as a text

-- Add a temporary string column to hold day names
ALTER TABLE `tripdata-2022-412822.2022.combined_2022`
ADD COLUMN day_name STRING;

-- Update the temporary column with day names
UPDATE `tripdata-2022-412822.2022.combined_2022`
SET day_name =
  CASE
    WHEN day_of_week = 1 THEN 'Sunday'
    WHEN day_of_week = 2 THEN 'Monday'
    WHEN day_of_week = 3 THEN 'Tuesday'
    WHEN day_of_week = 4 THEN 'Wednesday'
    WHEN day_of_week = 5 THEN 'Thursday'
    WHEN day_of_week = 6 THEN 'Friday'
    WHEN day_of_week = 7 THEN 'Saturday'
    ELSE 'Error'
  END
  WHERE 1 = 1;

-- we looked at some analysis information
-- bike types used by different riders
SELECT member_casual, rideable_type, COUNT(*) AS total_trips
FROM `tripdata-2022-412822.2022.combined_2022`
GROUP BY member_casual, rideable_type
ORDER BY member_casual, total_trips;

-- amount of rides per month for each rider 
SELECT month_name, member_casual, COUNT(ride_id) AS total_trips
FROM `tripdata-2022-412822.2022.combined_2022`
GROUP BY month_name, member_casual
ORDER BY member_casual;

-- the avg ride length for member types per month
SELECT month_name, member_casual, AVG(ride_length_new) / 60 * 100 AS avg_ride_duration
FROM `tripdata-2022-412822.2022.combined_2022`
GROUP BY month_name, member_casual;

-- number of trips started at different stations
SELECT start_station_name, member_casual,
  COUNT(ride_id) AS total_trips
FROM `tripdata-2022-412822.2022.combined_2022`
GROUP BY start_station_name, member_casual;

-- number of trips ended at different stations
SELECT end_station_name, member_casual,
  COUNT(ride_id) AS total_trips
FROM `tripdata-2022-412822.2022.combined_2022`
GROUP BY end_station_name, member_casual;
