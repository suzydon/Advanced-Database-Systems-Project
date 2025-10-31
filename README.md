  Advanced Database Systems Project

 Course:  Advanced Database Systems (UTS)  
 Core Competencies:  Data Governance, Master Data Management (MDM), Database Design, Cloud Data Warehouse (Snowflake), Performance Tuning

---

  Project Overview

This project demonstrates the end-to-end capability of diagnosing a complex business problem and understanding its underlying technical implementation. It consists of two main parts:

   Part 1 (Strategy):  A case study on Vodafone, designing a Master Data Management (MDM) solution to resolve critical data silo issues.
   Part 2 (Technical):  A hands-on lab in Snowflake, analyzing its caching mechanisms to optimize performance and reduce compute costs.

---

  Part 1: Case Study - Vodafone Customer Data Unification Strategy


   The Business Problem

Vodafone faced significant operational challenges due to customer data being fragmented across multiple, siloed systems (e.g., pre-paid, post-paid). This resulted in billing inaccuracies, poor customer experience, and an inability to form a "Single Customer View" for analytics or marketing.

   The Solution: Master Data Management (MDM)

A data governance strategy was proposed, centered on establishing a "Golden Record" for each customer using a stable, unique identifier ( `License ID`).

This solution involved designing a new `Customer_Master` table to act as the central hub, linking all customer-related services and products via foreign keys to create a unified data model.


<img width="452" height="546" alt="Picture 1" src="https://github.com/user-attachments/assets/008e1a50-af7b-497b-9828-dea7bbfb2fe4" />


> [View Full Analysis Report](./project-1-folder/Vodafone solution.docx)> (Note: Replace `project-1-folder` and `YOUR_REPORT_1_FILE.pdf` with your actual folder and file names)*

--- 

---

  Part 2: Technical Lab - Snowflake Performance & Cost Optimization

   Objective

When implementing large-scale data solutions like the one for Vodafone, controlling cloud compute costs and ensuring query performance are critical. This lab analyzed Snowflake's core caching features to understand their impact.

   Key Findings

A series of controlled SQL queries were executed to validate Snowflake's multi-layered cache:

   Finding 1: Result Cache 
       Behavior:  An identical query run a second time returned results in milliseconds (~0ms).
       Conclusion:  The Query Profile confirmed "Result Cache Used," demonstrating high optimization for recurring queries, such as from BI dashboards.

   Finding 2: Warehouse Cache (Local Disk Cache) 
       Behavior:  A  similar  (but not identical) query accessing the same dataset (e.g., `MAX()` instead of `AVG()`) was significantly faster on its second run.
       Conclusion:  The Query Profile showed data was read from "LOCAL_DISK_CACHE," avoiding expensive remote storage reads and accelerating exploratory analysis.

>  [View SQL Validation Scripts](./snowflake-labs/)  
