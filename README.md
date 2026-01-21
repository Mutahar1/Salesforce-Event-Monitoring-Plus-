# Event Monitoring Plus

A lightweight yet powerful collection of **CRM Analytics (CRMA) dashboards** designed to give Salesforce teams deep visibility into **Event Monitoring data** across user behavior, performance, security, and adoption.

This project helps admins, developers, architects, and product owners **understand how Salesforce is actually being used**, detect risk early, and improve overall platform performance.

---

## Overview

Event Monitoring Plus extends Salesforce’s native Event Monitoring Analytics by providing:

- Ready-to-use CRM Analytics dashboards  
- Actionable insights into user journeys and UI interactions  
- Performance analysis for Apex and Lightning  
- Security, compliance, and audit-focused reporting  
- Optimized, scalable analytics without external tools  

---

## Key Capabilities

### Event Visibility
- Login history and user activity analysis  
- API usage tracking  
- Report execution and export monitoring  

### Security & Compliance
- Identify suspicious or risky behavior patterns  
- Support audit and compliance reviews  
- Monitor high-risk user and system actions  

### Admin-Friendly UX
- Lightning Web Component–based dashboards  
- Filters by user, event type, date range  
- Clear, readable, decision-ready visuals  

### Performance-Aware Design
- Optimized SOQL usage  
- Aggregated datasets (not raw logs)  
- Bulk-safe Apex logic  

---

## Business Impact

This solution helps organizations:

- Detect risky behavior earlier  
- Improve Salesforce security posture  
- Reduce audit preparation time  
- Give admins real operational visibility  
- Scale monitoring without relying on external tools  

---

## Deployment Guide

### Easy Option: Automated Deployment (Recommended)

Use the **Heroku deployment app** to deploy dashboards and recipes automatically.

> **Important:**  
> When prompted, enter `main` in the **Branch / Tag / Commit** field.

**Deploy to Salesforce**

---

### Manual Deployment

Manual deployment is recommended if you prefer full control or need customization.

#### Prerequisites
- Salesforce DX or Workbench  
- Admin access to CRM Analytics  
- Event Monitoring Analytics app already created  

#### Important Notes Before Deployment

- This package assumes **only one instance** of the Event Monitoring Analytics app exists  
- Multiple instances create duplicate datasets (e.g. `ApexExecutionWithUsers1`)  
- If multiple instances exist:
  - Coordinate with stakeholders  
  - Consolidate into a single app where possible  
  - Identify the correct dataset API names that are actively refreshed  

---
Dataset Mapping Notice
---------------------
If your org contains multiple versions of datasets, update references as needed:

- LightningPageViewWithUsers → LightningPageViewWithUsers1

Ensure consistency across all dashboards and recipes.


Dataset Usage by Dashboard
--------------------------

User_Activities.wdash
- LightningInteractionWithUsers
- LightningPageViewWithUsers

Apex_Performance.wdash
- ApexExecutionWithUsers

Apex_Exceptions.wdash
- ApexUnexpectedException

⚠️ If you are using the default ~WithUsers datasets, ensure the Event Monitoring
Analytics dataflow is scheduled.


Deployment Options
------------------

You may deploy using one of the following methods:

1) Salesforce DX
- Authenticate and deploy via manifest/package.xml

2) Metadata API (Ant / SFDX)
- Use misc/mdapi/package.xml and payload

3) Workbench
- Zip contents of misc/mdapi/ (no root folder)
- Upload as a Single Package

4) JSON Import (Not Recommended)
- Copy JSON files from misc/json/
- Paste into a new CRM Analytics dashboard

⚠️ This method loses XMD metadata (colors, thresholds, rich formatting).


Dashboards Included
-------------------

User Journeys
Purpose:
- Understand how users interact with the Lightning UI

Audience:
- Sponsors
- Admins
- Product Owners
- Developers

Capabilities:
- App, object, and component usage
- Click and view behavior
- Identification of valuable vs unused customizations

Uses:
- LightningInteraction event log


User Activities
---------------
- Focused insight into user behavior patterns
- Engagement and adoption visibility


Apex Performance
----------------
Purpose:
- Identify slow or degrading Apex code

Audience:
- Developers
- QA
- Release Managers

Capabilities:
- Consistently slow methods
- Newly degraded executions
- Performance trends over time

Uses:
- ApexExecutionWithUsers


Apex Exceptions
---------------
Purpose:
- Detect and prevent breaking Apex failures

Audience:
- Developers
- QA
- Product Owners

Capabilities:
- Unhandled exception volume
- Error trends over time
- Release risk indicators

Uses:
- ApexUnexpectedException


Lightning Page Performance (EPT)
--------------------------------
Purpose:
- Identify poor-performing Lightning pages

Capabilities:
- Performance by app, object, and GEO
- Estimated Productivity Time (EPT) loss
- Page load analysis

Uses:
- LightningPageViewWithUsers
- LightningInteraction


Experience Cloud Page Performance
---------------------------------
- Experience Cloud–focused version of the Lightning EPT dashboard
- Site URL analysis
- User geo and browser segmentation
- Optimized for Experience Cloud templates

⚠️ Not tested with Aura or LWR Build-Your-Own sites


Report Adoption
---------------
Analyzes reports across three Event Monitoring pillars:

Adoption:
- Who runs reports vs who builds new ones

Performance:
- Rows returned vs database time

Security:
- CSV, Excel, and printable exports


Org Performance Overview
------------------------
A high-level performance lens across:
- Business logic
- API usage
- Platform bottlenecks
- Org-wide failure hotspots

Ideal as a starting point before deeper investigation.


Notes & Observations
--------------------
- Dashboards are deployed inside the “Event Monitoring Plus” app
- ⚠️ Do NOT click Reconfigure — it will delete dashboards
- Uses ~WithUsers datasets (as of January 2023)
- Default security: Manager access for Entire Org
- Dataset access remains the primary security control
- Dashboards can safely be copied into existing Event Monitoring apps


License
-------
This project is released under the MIT License.


## Dataset Mapping & Adjustments

### Example Dataset Rename
```text
LightningPageViewWithUsers → LightningPageViewWithUsers1
