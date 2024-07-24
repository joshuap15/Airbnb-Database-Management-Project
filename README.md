# Airbnb-Database-Management-Project

This repository contains the work done for the Airbnb Platform Database Project. The project involves designing and implementing a relational database for managing Airbnb listings, guests, hosts, bookings, payments, reviews, and more.

## Project Structure

- `docs/`: Contains documentation files.
  - `5_phase1_ERD.pdf`: Entity-Relationship Diagram (ERD) for the project.
  - `5_phase3.pdf`: Presentation slides summarizing the project.
  - `5_phase2.txt`: Data Manipulation Language (DML) scripts and queries.

## Overview

### Business Scenario

The business is based on Airbnb, a platform that enables guests to find and book unique accommodations offered by hosts around the world. The platform features a diverse selection of properties, each with its own characteristics and comforts. The platform ensures a safe and smooth transaction experience by verifying the identity of both hosts and guests and managing the payments from guests to hosts.

### Mission Statement & Objectives

**Mission Statement:**  
"The purpose of our databases is to store, maintain, and organize data curated by users of our business to effectively broker deals between guests looking for a location to stay and hosts offering their space for accommodation."

**Objectives:**  
- Maintain data on hosts, properties, guests, reviews, payments, bookings, locations, amenities, guest referrals, local attractions, and languages.
- Track the status of payments, property availability, and guest referrals.
- Report on various metrics such as guest booking history, property offerings, host and guest reviews, and more.

### ERD and Schema

The entity-relationship diagram (ERD) and the relational schema provide a visual representation of the database structure, detailing the relationships between different entities.

![ERD Diagram](docs/5_phase1_ERD.pdf)

### Sample Queries

Here are some sample SQL queries used in the project:

1. **Properties with Above Average Reviews and Their Booking Frequency:**
    ```sql
    SELECT P.Title, P.Price_night, COUNT(B.Booking_id) AS Booking_count, GR.Guest_rating
    FROM Properties P
    JOIN Bookings B ON P.Property_id = B.Property_id
    JOIN Review_by_guests GR ON B.Booking_id = GR.Booking_id
    WHERE GR.Guest_rating > (SELECT AVG(Guest_rating) FROM Review_by_guests)
    GROUP BY P.Title, P.Price_night, GR.Guest_rating
    ORDER BY GR.Guest_rating DESC, P.Price_night ASC;
    ```

2. **Top 5 most frequent booking months:**
    ```sql
    SELECT
        YEAR(b.Check_in_date) AS Year,
        MONTHNAME(b.Check_in_date) AS Month,
        COUNT(b.Booking_id) AS Num_of_bookings
    FROM
        Bookings b
    GROUP BY
        Year, Month
    ORDER BY
        Num_of_bookings DESC
    LIMIT 5;
    ```

For more detailed queries, refer to `docs/5_phase2.txt`.

### Learning Experience

The project involved creating a website connected to a database to display SQL queries. Challenges included establishing the primary connection and resolving issues through online resources and guidance from professors.

## Contributors

- Aasna Shah
- Joshua Poozhikala
- Kelly Kao
- Kritika Nayyar
- Rodrigo Castro



