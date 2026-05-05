CloudPulse – Serverless Uptime & Latency Monitoring System
📌 Project Title
CloudPulse – Serverless Uptime, Latency Monitoring, Alerting & Auto-Recovery System

📖 Project Overview
CloudPulse is a fully serverless monitoring system built using AWS services.
It continuously checks whether a website is UP or DOWN, measures response latency, analyzes performance trends, calculates uptime SLA, sends intelligent alerts, and performs automatic recovery actions when failures persist.

The project follows SRE (Site Reliability Engineering) principles such as:

Monitoring
Alerting
SLA measurement
Self-healing (auto-recovery)
No servers are managed manually.

🏗️ Overall Architecture
Amazon S3 – Hosts the static website
Amazon CloudFront – Serves the website securely over HTTPS
Amazon EventBridge – Schedules monitoring every 5 minutes
AWS Lambda – Executes monitoring, analysis, alerting & recovery logic
Amazon DynamoDB – Stores historical monitoring records
Amazon CloudWatch – Displays latency & SLA metrics
Amazon SNS – Sends alert and recovery notifications
🔄 High-Level Workflow
Website is hosted on Amazon S3 and served via CloudFront.
EventBridge triggers Lambda every 5 minutes.
Lambda sends HTTP request to the website.
Lambda measures:
Availability (UP / DOWN)
Response time (latency)
Results are stored in DynamoDB.
CloudWatch metrics are updated.
Alerts or recovery actions are triggered if needed.
🟢 DAY 1 — STATIC WEBSITE HOSTING
What was done
Created a static website using HTML and CSS.
Hosted the website using Amazon S3.
Outcome
Website accessible publicly.
Base system to monitor is ready.
🟢 DAY 2 — EVENT-DRIVEN MONITORING
What was done
Created an AWS Lambda function.
Lambda sends HTTP request to the website.
Measures:
HTTP status code
Response time (latency)
Outcome
Automated website checking logic created.
🟢 DAY 3 — DATA STORAGE WITH DYNAMODB
What was done
Created a DynamoDB table.
Used:
Partition Key (pk) → Website identifier
Sort Key (sk) → Timestamp
Lambda stores:
Status (UP / DOWN)
Latency
Error (if any)
Outcome
Historical monitoring data stored reliably.
🟢 DAY 4 — AUTOMATION WITH EVENTBRIDGE
What was done
Configured Amazon EventBridge.
Lambda runs automatically every 5 minutes.
Outcome
Fully automated monitoring without manual execution.
🟢 DAY 5 — LATENCY TREND DETECTION
What was done
Lambda fetches last 10 latency records from DynamoDB.
Splits data into:
Older latency values
Recent latency values
Calculates average for both.
Compares averages.
Logic
If Recent Avg > Older Avg → DEGRADING Else → NORMAL

Outcome
Detects performance degradation before downtime occurs.
🟢 DAY 6 — UPTIME SLA CALCULATION
What was done
Lambda reads last 50 monitoring records.
Counts:
Total checks
UP checks
Calculates SLA using:
Uptime % = (UP checks / Total checks) × 100

Publishes SLA metric to CloudWatch.
Outcome
Business-grade uptime percentage calculation.
🟢 DAY 7 — SMART ALERTING (SNS)
What was done
Integrated Amazon SNS for alerts.
Alerts are triggered only when:
Website is DOWN for 3 consecutive checks
OR latency exceeds threshold repeatedly
Why this matters
Avoids alert spam.
Sends alerts only when issue is real.
Outcome
Intelligent, production-like alerting system.
🟢 DAY 8 — AUTO-RECOVERY (SELF-HEALING)
What was done
Added auto-recovery logic.
If website is DOWN for 7 consecutive checks:
Lambda triggers CloudFront cache invalidation
Attempts automatic recovery
Sends recovery notification via SNS
Why auto-recovery is needed
Humans may miss alerts.
System attempts recovery automatically.
Reduces downtime without manual intervention.
Outcome
Monitoring + Action combined.
SRE-level self-healing feature implemented.
📊 Monitoring & Visualization
CloudWatch dashboards show:
Website latency graph
Uptime SLA percentage
Supports:
1 hour
3 hours
Daily / weekly views
🛠️ Technologies Used
AWS Lambda (Python)
Amazon S3
Amazon CloudFront
Amazon EventBridge
Amazon DynamoDB
Amazon CloudWatch
Amazon SNS
🎯 Key Learnings
Serverless architecture
Event-driven design
DynamoDB data modeling
CloudWatch custom metrics
Intelligent alerting
Auto-recovery mechanisms
Real-world SRE concepts
🔮 Future Enhancements
Multi-website monitoring
Region-wise health checks
Monthly SLA reports
QuickSight dashboards
Incident history analysis
✅ Project Status
Completed successfully (Day 1 to Day 8)
All features tested and validated.
