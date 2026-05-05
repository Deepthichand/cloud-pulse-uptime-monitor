CloudPulse – Serverless Uptime & Latency Monitoring System
📌 Project Title

CloudPulse – Serverless Uptime, Latency Monitoring, Alerting & Auto-Recovery System

📖 Project Overview

CloudPulse is a fully serverless monitoring system built using AWS services. It continuously checks whether a website is UP or DOWN, measures response latency, analyzes performance trends, calculates uptime SLA, sends intelligent alerts, and performs automatic recovery actions when failures persist.

The project follows SRE (Site Reliability Engineering) principles:

Monitoring
Alerting
SLA Measurement
Self-healing (Auto-Recovery)
No manual server management
🏗️ Overall Architecture
Amazon S3 – Hosts the static website
Amazon CloudFront – Secure HTTPS delivery
Amazon EventBridge – Schedules monitoring (every 5 min)
AWS Lambda – Monitoring, analysis, alerting & recovery
Amazon DynamoDB – Stores monitoring data
Amazon CloudWatch – Metrics & dashboards
Amazon SNS – Alerts & notifications
🔄 High-Level Workflow
Website hosted on S3 and served via CloudFront
EventBridge triggers Lambda every 5 minutes
Lambda sends HTTP request
Measures:
Availability (UP/DOWN)
Latency
Stores results in DynamoDB
Updates CloudWatch metrics
Triggers alerts or recovery if needed
🟢 DAY 1 — Static Website Hosting

What was done

Created static website (HTML, CSS)
Hosted on Amazon S3

Outcome

Website publicly accessible
Monitoring target ready
🟢 DAY 2 — Event-Driven Monitoring

What was done

Created AWS Lambda function
Sends HTTP request
Measures status & latency

Outcome

Automated monitoring logic implemented
🟢 DAY 3 — Data Storage (DynamoDB)

What was done

Created DynamoDB table
Partition Key: pk (website)
Sort Key: sk (timestamp)
Stored:
Status
Latency
Errors

Outcome

Reliable historical data storage
🟢 DAY 4 — Automation (EventBridge)

What was done

Configured scheduled trigger (5 min)

Outcome

Fully automated monitoring
🟢 DAY 5 — Latency Trend Detection

What was done

Fetch last 10 records
Split into old vs recent
Compare averages

Logic

Recent Avg > Older Avg → DEGRADING
Else → NORMAL

Outcome

Early performance issue detection
🟢 DAY 6 — Uptime SLA Calculation

What was done

Read last 50 records
Calculate uptime

Formula

Uptime % = (UP checks / Total checks) × 100

Outcome

Business-level SLA tracking
🟢 DAY 7 — Smart Alerting (SNS)

What was done

Integrated Amazon SNS

Triggers

3 consecutive failures
High latency repeatedly

Outcome

No alert spam
Real issue detection
🟢 DAY 8 — Auto-Recovery (Self-Healing)

What was done

Auto-recovery logic added
If DOWN for 7 checks:
Trigger CloudFront invalidation
Attempt recovery
Send notification

Outcome

Reduced downtime
Fully automated recovery
📊 Monitoring & Visualization

CloudWatch dashboards include:

Latency graphs
Uptime SLA %

Supports:

Hourly
Daily
Weekly views
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
Event-driven systems
DynamoDB design
CloudWatch metrics
Intelligent alerting
Auto-recovery systems
SRE concepts
🔮 Future Enhancements
Multi-website monitoring
Region-based health checks
Monthly SLA reports
QuickSight dashboards
Incident analysis
✅ Project Status

✔ Completed (Day 1 → Day 8)
✔ All features tested and validated

🔥 Tip

After adding this:

git add README.md
git commit -m "Added project README"
git push origin master
