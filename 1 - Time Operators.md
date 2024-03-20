---
title: Time Operators
slug: bA4N-time-operators
createdAt: 2024-01-04T15:40:00.270Z
updatedAt: 2024-01-04T15:50:08.654Z
---

Time operators in Oxla allow you to perform various operations on dates, times, and intervals. Here's a guide to using these operators:

## **1. DATE + INTEGER**

Add a specific number of days to a date.

**Example**

```pgsql
select date '2022-03-15' + 14 as "result";
```

The result will be 14 days after '2022-03-15'.

```pgsql
   result   
------------
 2022-03-29
```

### 1.1. INTEGER + DATE

Adding and multiplying time operators can also be done in reverse order. For example, we add a number of days to a date in the format of `Integer + Date`.

```pgsql
select 14 + date '2022-03-15' AS "result";
```

The result will be the same, which is 14 days after '2022-03-15' is '2022-03-29'.

```pgsql
   result   
------------
 2022-03-29
```

## **2. DATE + INTERVAL**

Add a specified interval to a date.

**Example**

```pgsql
select date '2022-03-15' + interval '3 months' as "result";
```

The result will be the date three months after '2022-03-15'.

```pgsql
           result           
----------------------------
 2022-06-15 00:00:00.000000
```

## **3. DATE - INTEGER**

Subtract a certain number of days from a date.

**Example**

```pgsql
select date '2022-03-15' - 7 as "result";
```

The result will be 7 days before '2022-03-15'.

```pgsql
   result   
------------
 2022-03-08
```

## **4. DATE - INTERVAL**

Subtract a specified interval from a date.

**Example**

```pgsql
select date '2022-03-15' - interval '2 hour' as "result";
```

The result will be the timestamp with two hours before '2022-03-15'.

```pgsql
           result           
----------------------------
 2022-03-14 22:00:00.000000
```

## **5. DATE - DATE**

Subtract dates.

**Example**

```pgsql
select date '2023-03-15' - date '2023-01-10' as "result";
```

The number of days elapsed between '2023-03-15' and '2023-01-10' is 64 days.

```pgsql
 result 
--------
     64
```

## **6. DATE + TIME**

Add a time-of-day to a date.

**Example**

```pgsql
select date '2010-05-20' + time '02:00' as "result";
```

The result will be a timestamp with the specified time added to the given date.

```pgsql
           result           
----------------------------
 2010-05-20 02:00:00.000000
```

## **7. TIME + INTERVAL**

Add a certain interval to a given time.

**Example**

```pgsql
select time '12:30' + interval '1 hour' as "result";
```

The result will be the time 1 hour after '12:30'.

```pgsql
     result      
-----------------
 13:30:00.000000
```

## **8. TIME - INTERVAL**

Subtract a specified interval from a given time.

**Example**

```pgsql
select time '18:45' - interval '45 minutes' as "result";
```

The result will be the time 18:00.

```pgsql
     result      
-----------------
 18:00:00.000000
```

## **9. TIME - TIME**

Get a time difference by subtracting one time from another.

**Example**

```pgsql
select time '10:00' - TIME '08:20' as "result";
```

In this example, the time difference between the two provided times is 1 hour and 40 minutes.

```pgsql
     result      
-----------------
 01:40:00.000000
```

## **10. TIMESTAMP + INTERVAL**

Add a timestamp and an interval.&#x20;

**Example**

```pgsql
select timestamp '2021-01-05 12:00:00' + interval '5 days' as "result";
```

The result will be a new timestamp, adding 5 days to '2021-01-05 12:00:00'.

```pgsql
           result           
----------------------------
 2021-01-10 12:00:00.000000
```

## **11. TIMESTAMP - INTERVAL**

Subtract an interval from a timestamp.

**Example**

```pgsql
select timestamp '2022-01-04 12:00:00' - interval '3 days' as "result";
```

In this example, it subtracts 3 days from '2022-01-04 12:00:00'.

```pgsql
           result           
----------------------------
 2022-01-01 12:00:00.000000
```

## **12. TIMESTAMP - TIMESTAMP**

Get an interval by subtracting one timestamp from another.&#x20;

**Example**

```pgsql
select timestamp '2022-01-05 18:30:00' - timestamp '2022-01-01 12:00:00' as "result";
```

It gives the interval between the two timestamps, 102 hours and 30 minutes.

```pgsql
      result      
------------------
 102:30:00.000000
```

## **13. INTERVAL + INTERVAL**

Add intervals.

**Example**

```pgsql
select interval '2 months 2 days' + interval '6 days' as "result";
```

It adds 6 days to 2 days, resulting in a total of 2 months and 8 days.

```pgsql
    result     
---------------
 2 mons 8 days
```

## **14. INTERVAL - INTERVAL**

Subtract intervals.

**Example**

```pgsql
select interval '2 months' - interval '20 days' as "result";
```

It subtracts 20 days from 2 months.

```pgsql
     result      
-----------------
 2 mons -20 days
```

## **15. INTERVAL \* INTEGER**

Multiply an interval by an integer.

**Example**

```pgsql
select interval '2 hours' * 3 as "result";
```

It multiplies '2 hours' by 3, resulting in 6 hours.

```pgsql
     result      
-----------------
 06:00:00.000000
```

