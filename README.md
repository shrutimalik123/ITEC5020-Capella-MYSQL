#ITEC 5020/5025 Project: Hypotify Clinical Insights Bot Database

Overview

This repository contains the foundational relational database and scripts developed for ITEC 5020: Database Development. This database serves as the core data infrastructure for the Hypotify Clinical Insights Bot, an AI virtual assistant that will be built and integrated in the subsequent course, ITEC 5025: Application Development and AI.

Project Domain

Domain: Healthcare (Clinical Research Informatics)

Concept: A non-commercial AI chatbot designed to help researchers query complex Electronic Medical Records (EMR) data using natural language, and run predictive risk models.

Data Source: A synthetic (artificial) patient dataset, structured to simulate the complexity of real-world EMR systems while maintaining ethical compliance (no HIPAA or PII risk).

💾 Database Architecture

The database is built on a highly normalized Third Normal Form (3NF) relational model using MySQL to ensure data integrity, minimize redundancy, and optimize performance for machine learning processes.

Entity (Table)

Purpose

Key Attributes

PATIENT

Stores unique patient demographics (Master Data).

PatientID (PK)

ADMISSION

Stores clinical encounters/hospital stays.

AdmissionID (PK), PatientID (FK)

DIAGNOSIS

Stores the primary diagnosis for each admission.

DiagnosisRecordID (PK), AdmissionID (FK)

LAB_OBSERVATION

Stores high-volume time-series data (107M records in the full set).

LabRecordID (PK), AdmissionID (FK)

Key Design Principle: Separation of Environments

The entire development process was conducted in the isolated artificial_emr1 schema to prevent accidental changes to the larger, original 500-patient dataset (artificial_emr), demonstrating professional data governance best practices.

📦 Repository Contents

This repository contains all necessary files to recreate the database and validate the assignment requirements.

File Name

Description

Purpose in Project

ITEC5020_Database_Script.sql

Primary SQL Deliverable. Contains all CREATE TABLE, INSERT (sample data), and required CRUD/DML queries for the assignment. This script builds the clean artificial_emr1 database.

Week 3/4 Deliverable

PATIENT_Data.csv

Sample Data. Contains the 500-patient dataset files (reduced from 100,000) used for final data population in later stages.

Data for ITEC 5025

ADMISSION_Data.csv

(and other CSV files)

Data for ITEC 5025

ITEC5020_SQL_Generator.ipynb

Google Colab Notebook used to automate the generation and integrity checking of the primary SQL script.

Reproducibility & Automation

Final_Concept_Documentation.pdf

Final report detailing the AI concept, normalization steps, and the justification for the relational design.

Week 5 Deliverable

🚀 Future AI Integration (ITEC 5025)

The clean, 3NF structure of this database is essential for the AI component:

NLP Models: Will be built to translate natural language user queries directly into efficient SQL JOIN statements against these structured tables.

ML Models: Will use the structured, non-redundant data (e.g., age, lab values) to train and run classification models (Predictive Risk Modeling) reliably and safely.

The data integrity enforced by MySQL is the critical factor that makes the entire AI solution trustworthy.
