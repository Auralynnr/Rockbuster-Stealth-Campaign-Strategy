# CF-Rockbuster-Stealth-Campaign-Strategy
Rockbuster Stealth LLC is pivoting from global brick-and-mortar rentals to an online video rental service, leveraging its existing film licenses to stay competitive with Netflix, Prime Video, and others. This repository documents the analytics work supporting that launch.

**Disclaimer:** Rockbuster Stealth LLC is a fictional company used for a practice assignment for CareerFoundry. All analysis, data structures, and outputs in this repo are for learning purposes only.

## Objective

Load, explore, and analyze Rockbuster’s database to identify revenue drivers, customer locations, and regional trends, then deliver executive-ready recommendations.


## Key Questions (from the Board)

1. Which movies contributed the most/least to **revenue**?
2. What is the **average rental duration**?
3. Which **countries** are our customers based in?
4. Where are **high lifetime value** customers located?
5. Do **sales vary by region**?

## Data

**Source & Context**
- Dataset: Rockbuster Stealth (DVD rental sample) used for a **practice assignment** with a **fictional company**.
- Storage: Loaded into an RDBMS (PostgreSQL) for SQL analysis.

**Core Tables**
- `film` — Film metadata (title, length, rating, rental_rate, replacement_cost).
- `inventory` — Copies of films per store (`film_id`, `store_id`).
- `rental` — Each rental event (dates, `inventory_id`, `customer_id`).
- `payment` — Payments linked to rentals (`rental_id`, amount, date).
- `customer` — Customer profile (`store_id`, `address_id`, active).
- `address` → `city` → `country` — Location hierarchy for customers/stores.
- `store` — Store details and location (`address_id`, manager).
- `staff` — Employees tied to stores.
- `category` & `film_category` — Film genres (many-to-many).
- `actor` & `film_actor` — Cast (many-to-many).
- `language` — Primary language of films.

**Common Keys**
- Primary keys: `*_id` in each table (e.g., `film_id`, `customer_id`).
- Foreign keys:  
  - `inventory.film_id` → `film.film_id`  
  - `rental.inventory_id` → `inventory.inventory_id`  
  - `payment.rental_id` → `rental.rental_id`  
  - `customer.address_id` → `address.address_id` → `city.city_id` → `country.country_id`  
  - `film_category.film_id` ↔ `category.category_id`; `film_actor.film_id` ↔ `actor.actor_id`
 
[Download the Data Dictionary (PDF)](https://coach-courses-us.s3.amazonaws.com/exercises/1054/69939/2853589c0601eaa792e8af0d0358fabe/Rockbuster-Stealth-Data-Dictionary.pdf)

## Deliverables

**SQL scripts:** schema, load, cleaning, and analysis queries.    
**Exploratory analysis:** results tables and interim findings.   
**Final report:** concise insights, visuals, and action items for leadership.    
**Segment strategy:** priority audiences and market entry recommendations.    

## Tools Used

**PostgreSQL** for the RDBMS  
**SQL** for analysis
