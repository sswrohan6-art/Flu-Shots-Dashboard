# Flu-Shots-Dashboard 💉

A comprehensive dashboard for tracking and visualizing flu shot administration across patients in 2022. This project provides detailed analytics stratified by age, race, county, and overall statistics.

## 📊 Project Overview

This Flu Shots Dashboard for 2022 displays vaccination rates and trends using hospital patient data. It enables healthcare administrators and providers to monitor flu shot distribution and identify vaccination gaps across different patient demographics.

## 🎯 Objectives

The dashboard provides the following key metrics:

1. **Total % of Patients Getting Flu Shots** - Stratified by:
   - Age groups
   - Race/Ethnicity
   - County (with geographic visualization on a map)
   - Overall vaccination rate

2. **Running Total of Flu Shots** - Track cumulative vaccinations over the course of 2022

3. **Total Number of Flu Shots Given in 2022** - Summary statistic

4. **Patient List** - Comprehensive list showing each patient and their flu shot status (received/not received)

## 📋 Requirements

- Patients must have been **"Active at our hospital"** during the period 2020–2022
- Data extracted from hospital encounters between 2020-2022
- Only living patients (no null deathdate)
- Age filtered appropriately (≥6 months old)

## 📁 Project Files

- **README.md** - This file, project documentation
- **Flu_shot.PNG** - Dashboard screenshot/visualization
- **tables_req.txt** - Database schema and table creation scripts
- **resultant_sql.txt** - SQL queries used for data extraction and analysis

## 🗄️ Database Schema

The project uses PostgreSQL with the following tables:

### Patients Table
- `id` (Primary Key)
- `first`, `last` - Patient name
- `birthdate`, `deathdate` - Birth and death dates
- `gender`, `race` - Demographics
- `county`, `state`, `zip_code` - Location information
- `phone`, `email` - Contact information

### Encounters Table
- `encounter_id` (Primary Key)
- `patient` (Foreign Key to Patients)
- `start`, `end_time` - Encounter timestamps
- `provider_id`, `visit_type`, `department` - Visit details

### Immunizations Table
- Tracks immunization codes and dates
- Code `5302` identifies flu shots

## 🔧 Setup Instructions

1. **Create the database schema:**
   ```sql
   CREATE SCHEMA IF NOT EXISTS "postgres"."Hospital_Data";
   ```

2. **Create the required tables** using the scripts in `tables_req.txt`

3. **Load patient and immunization data** into the respective tables

4. **Run the SQL queries** from `resultant_sql.txt` to extract flu shot analytics

## 📈 Key SQL Query

The main analysis query:
- Identifies active patients from encounters (2020-2022)
- Finds earliest flu shot date for each patient in 2022 (immunization code 5302)
- Calculates age as of December 31, 2022
- Returns patient demographics and vaccination status

## 🚀 Usage

Use the dashboard to:
- Monitor vaccination coverage by demographics
- Identify underserved populations
- Track vaccination progress throughout 2022
- Generate reports for hospital administration
- Measure compliance with vaccination goals

## 📝 Notes

- The age calculation in the SQL query may need adjustment based on specific requirements
- Alternative age calculation methods are documented in the query comments
- All dates are in UTC timestamp format