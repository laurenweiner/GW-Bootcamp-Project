# GW-Bootcamp-Project

## Database Resources
PostgreSQL

__Sample Create Table statement__

The below "CREATE TABLE" statement was used to test/confirm the correct column data type.  If the correct data type is NOT defined in the table, the import process will fail using the GUI or command line.

  **CREATE DATABASE Final_Project;** -- Syntax to create Test database.

  **CREATE TABLE** county_market_tracker (
    period_begin date NULL,
    period_end date NULL,
    period_duration integer NULL,
    region_type varchar(50) NULL,
    region_type_id varchar(50) NULL,
    table_id varchar(50) NULL,
    is_seasonally_adjusted char(1) NULL,
    region varchar(50) NULL,
    city varchar(50) NULL,
    state varchar(50) NULL,
    state_code char(2) NULL,
    property_type varchar(50) NULL,
    property_type_id varchar(50) NULL,
    median_sale_price double precision NULL,
    median_sale_price_mom double precision NULL,
    median_sale_price_yoy double precision NULL,
    median_list_price double precision NULL,
    median_list_price_mom double precision NULL,
    median_list_price_yoy double precision NULL,
    median_ppsf double precision NULL,
    median_ppsf_mom double precision NULL,
    median_ppsf_yoy double precision NULL,
    median_list_ppsf double precision NULL,
    median_list_ppsf_mom double precision NULL,
    median_list_ppsf_yoy double precision NULL,
    homes_sold double precision NULL,
    homes_sold_mom double precision NULL,
    homes_sold_yoy double precision NULL,
    pending_sales integer NULL,
    pending_sales_mom double precision NULL,
    pending_sales_yoy double precision NULL,
    new_listings integer NULL,
    new_listings_mom double precision NULL,
    new_listings_yoy double precision NULL,
    inventory integer NULL,
    inventory_mom double precision NULL,
    inventory_yoy double precision NULL,
    months_of_supply double precision NULL,
    months_of_supply_mom double precision NULL,
    months_of_supply_yoy double precision NULL,
    median_dom integer NULL,
    median_dom_mom integer NULL,
    median_dom_yoy integer NULL,
    avg_sale_to_list double precision NULL,
    avg_sale_to_list_mom double precision NULL,
    avg_sale_to_list_yoy double precision NULL,
    sold_above_list double precision NULL,
    sold_above_list_mom double precision NULL,
    sold_above_list_yoy double precision NULL,
    price_drops double precision NULL,
    price_drops_mom double precision NULL,
    price_drops_yoy double precision NULL,
    off_market_in_two_weeks double precision NULL,
    off_market_in_two_weeks_mom double precision NULL,
    off_market_in_two_weeks_yoy double precision NULL,
    parent_metro_region varchar(50) NULL,
    parent_metro_region_metro_code integer NULL,
    last_updated timestamp NULL);


__Command line syntax to import test dataset__

The below command will be used to import the "live" dataset into a PostgreSQL database table.

**COPY** county_market_tracker
**FROM** 'C:\temp\county_market_tracker.tsv000'
**DELIMITER** E'\t' CSV HEADER;  -- \t is tab delimiter

__SQL syntax to join two tabless which will be used to join the housing data in PostgreSQL__

SELECT smt.*, 
mpd.popestimate2010
,mpd.popestimate2011
,mpd.popestimate2012
INTO zzsample_table 
FROM market_pop_data mpd
 JOIN state_market_tracker smt on mpd.state_name = smt.state_name;
**
**Python code to import sqlalchemy and connect to the AWS PostgreSQL database ****

import sqlalchemy
from sqlalchemy.ext.automap import automap_base
from sqlalchemy.orm import Session

from sqlalchemy import create_engine
import pandas as pd
import psycopg2

#The below string will connect directly to 
#db_string = f"postgresql://postgres:70IsGoodGolfM@@127.0.0.1:5432/zzsw"

#The below string will connect directly to the AWS/RDS PostgreSQL database
db_string = f"postgresql://postgres:XB0j1ma!17@housingdata.cng7z9pmjc4z.us-east-1.rds.amazonaws.com:5432/zzsw"

engine = create_engine(db_string)

conn = engine.connect()



