Grafana Backup Monitoring & Alerting Lab
Overview
This project demonstrates a backup monitoring and alerting solution using Grafana, PostgreSQL, and Red Hat Enterprise Linux (RHEL).

The solution simulates enterprise backup jobs and generates alerts when backup failures occur. Dashboard panels display backup health, successful jobs, failed jobs, and backup history.

Architecture
PostgreSQL
     │
     ▼
Grafana Data Source
     │
     ▼
Dashboard Panels
     │
     ▼
Alert Rules
Technologies Used
Grafana
PostgreSQL
RHEL 10.2
SQL
Linux Administration
Features
Backup Job Monitoring
Success / Failure Tracking
Real-Time Dashboard
Alert Rule Creation
Alert Recovery Testing
PostgreSQL Integration
Backup History Visualization
Database Schema
CREATE TABLE backup_jobs (
 id SERIAL PRIMARY KEY,
 job_name VARCHAR(100),
 status VARCHAR(20),
 duration INT,
 backup_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
Sample Data
INSERT INTO backup_jobs
(job_name,status,duration)
VALUES
('Daily_VM_Backup','SUCCESS',35),
('SQL_Backup','SUCCESS',20),
('Oracle_Backup','FAILED',120);
Dashboard Panels
Failed Backup Jobs
SELECT COUNT(*) AS failed_jobs
FROM backup_jobs
*HERE status='FAILED*;
Successful Jobs
FROM backup_jobs
WHERE status='SUCCESS';
Total Jobs
SELECT COUNT(*) AS total_jobs
FROM backup*jobs;
*``

### Backup History

```sql
SEL*CT
job_name,
status,
duration,
bac*up_time
FROM backup_jobs
ORDER BY *ackup_time DESC*
Alert Rule
SELECT COUNT(*) AS failed_jobs
FROM backup_jobs
WHERE status='FAILED';
Condition:

WHEN failed_jobs > 0
Testing Alerts
Generate Alert:

INSERT INTO backup_jobs
(job_name,status,duration)
VALUES
('Veeam_Test_Backup','FAILED',95);
Clear Alert:

UPDATE backup_jobs
SET status='SUCCESS'
WHERE job_name='Veeam_Test_Backup';
Screenshots
Add screenshots inside:

screenshots/
Examples:

screenshots/dashboard.png
screenshots/alert-firing.png
screenshots/alert-normal.png
Skills Demonstrated
Grafana Dashboards
Grafana Alerting
PostgreSQL
SQL
Linux Administration
Monitoring & Alerting
Backup Monitoring
Incident Management
Author
Vipin Tanwar

Backup Engineer - L2

Specializations:

Veeam Backup & Replication
Commvault
Grafana
Linux Administration
Disaster Recovery
