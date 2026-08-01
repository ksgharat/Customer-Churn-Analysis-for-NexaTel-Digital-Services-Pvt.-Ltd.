# Customer-Churn-Analysis-for-NexaTel-Digital-Services-Pvt.-Ltd.
1. Project Overview
Welcome to the NexaTel Customer Churn Analytics project.

I have been hired as a Junior Data Analyst at NexaTel Digital Services Pvt. Ltd., a fast-growing Indian telecom and digital-services operator. The company's leadership team needs data-driven answers to one urgent question — why are customers leaving? — and that is where I come in.
This project simulates a real-world analytics assignment. I will work with a realistic dataset covering the company's customer base and operations, containing roughly 757,000 records across 24 interconnected tables. My job is to clean, explore, analyse, and present the data in a way that helps non-technical managers understand who is churning, why, how much revenue is at risk, and what can be done about it.

1.1  Business Context
NexaTel operates as an integrated telecom provider serving customers across India. It sells across multiple product lines — Prepaid Mobile, Postpaid Mobile, 4G, 5G, Fiber Broadband, Enterprise Connectivity, IoT Solutions, Smart Home, and OTT Bundles. The platform accepts multiple payment methods including UPI, Credit Card, Debit Card, Net Banking, Wallet, Auto Debit, Cash, IMPS, NEFT, and RTGS, and serves metro, Tier-2, and Tier-3 cities.
Over the last four quarters, blended monthly churn has risen from 1.9% to 2.7% while the cost of acquiring a new subscriber has climbed 22%. Management has the following pressing questions they need answered this quarter:
•	Which plans and customer segments have the highest churn — and why?
•	Are unresolved or repeat complaints driving customers away?
•	Which customers are the most valuable, and which of them are most at risk?
•	Are there network-quality black spots causing localised churn spikes?
•	Which states and circles are losing the most subscribers?
•	Do our retention campaigns actually keep customers, or are we wasting spend?
3. Dataset Description
I are provided 24 CSV files that together form the NexaTel database. Together they contain approximately 757,000 records and preserve full referential integrity through primary and foreign keys.

2.1  Files Provided
File	Records	Size	Description
customers.csv	19,076	4.5 MB	Customer profiles, segment, plan, tenure, churn status
subscriptions.csv	20,523	1.2 MB	Active and terminated subscriptions per customer
plans.csv	25	2 KB	Plan catalogue: charges, data/voice quota, billing cycle
plan_history.csv	19,349	1.1 MB	Plan upgrade / downgrade change events
contracts.csv	10,607	798 KB	Contracts for postpaid / fibre / enterprise customers
devices.csv	19,000	1.5 MB	Device per customer (handset / router / IoT)
billing.csv	115,313	8.7 MB	Monthly invoices with base, GST and total amounts
payments.csv	92,362	5.9 MB	Payments made against invoices
recharges.csv	146,501	7.2 MB	Prepaid recharge transactions
usage_voice.csv	57,000	2.2 MB	Monthly voice usage per customer
usage_sms.csv	57,000	1.9 MB	Monthly SMS usage per customer
usage_data.csv	57,000	2.1 MB	Monthly data (GB) usage per customer
network_quality.csv	57,000	3.1 MB	Monthly network experience per customer
support_tickets.csv	31,490	2.6 MB	Support tickets, priority, FCR, resolution time
complaints.csv	16,584	1.2 MB	Complaints with type, severity, resolution status
customer_feedback.csv	28,499	1.6 MB	CSAT / NPS survey responses
retention_campaigns.csv	6,475	524 KB	Customer-level retention offers and outcomes
marketing_campaigns.csv	40	3.8 KB	Campaign definitions, budget, reach, conversions
employees.csv	800	84 KB	Support / sales staff handling tickets
stores.csv	2,180	146 KB	Retail stores by city and region
regions.csv	4	< 1 KB	Operating zones (North / West / South / East)
cities.csv	68	3.7 KB	Cities with tier and PIN prefix
states.csv	36	< 1 KB	Indian states and union territories
data_quality_issue_log.csv	20	< 1 KB	Catalogue of intentionally injected DQ issues

2.2  Key Columns Reference
Below are the most important columns I will use throughout this project. Refer to the full Data Dictionary for every column definition.
customers.csv — The Central Table
Column	Type	Example	Description
customer_id	VARCHAR	C0000001	Unique customer ID (primary key)
customer_segment	VARCHAR	Premium	Mass / Value / Premium / Enterprise
product_line	VARCHAR	Fiber Broadband	Primary product the customer is on
plan_id	VARCHAR	PL015	Links to plans.csv
city_name / city_tier	VARCHAR	Pune / Metro	Location and city tier
acquisition_date	DATE (DD-MM-YYYY)	12-07-2021	When the customer joined
tenure_months	INT	57	Length of relationship in months
annual_income_inr	DECIMAL	850000.00	Estimated annual income in INR
customer_status	VARCHAR	Active	Active / Churned
churn_date	DATE	05-02-2026	Date the customer churned (blank if active)

subscriptions.csv — Plans Held
Column	Type	Example	Description
subscription_id	VARCHAR	S0000001	Unique subscription ID
customer_id	VARCHAR	C0000001	Links to customers.csv
plan_id	VARCHAR	PL009	Links to plans.csv
billing_cycle	VARCHAR	Monthly	Monthly / Annual
monthly_charge_inr	DECIMAL	999.00	Recurring charge in INR
subscription_status	VARCHAR	Active	Active / Terminated

billing.csv — Invoices
Column	Type	Example	Description
invoice_id	VARCHAR	INV00000001	Unique invoice ID
customer_id	VARCHAR	C0000001	Links to customers.csv
billing_date	DATE (DD-MM-YYYY)	01-03-2026	Date the invoice was raised
base_amount_inr	DECIMAL	999.00	Charge before GST
gst_amount_inr	DECIMAL	179.82	18% GST component
total_amount_inr	DECIMAL	1178.82	Total payable in INR
payment_status	VARCHAR	Paid	Paid / Unpaid / Overdue

complaints.csv & support_tickets.csv — Service Experience
Column	Type	Example	Description
complaint_id / ticket_id	VARCHAR	CMP00000001	Unique ID
customer_id	VARCHAR	C0000001	Links to customers.csv
status	VARCHAR	Unresolved	Resolved / Unresolved / Pending
severity / priority	VARCHAR	Major / High	Severity or priority level
first_contact_resolution	VARCHAR	No	Was it solved on first contact (tickets)
resolution_hours	DECIMAL	36.5	Hours taken to resolve (tickets)

usage_data.csv — Monthly Data Usage
Column	Type	Example	Description
usage_id	VARCHAR	UD00000001	Unique usage record
customer_id	VARCHAR	C0000001	Links to customers.csv
usage_month	TEXT	03-2026	Month of usage (MM-YYYY)
data_gb_used	DECIMAL	42.6	Data consumed in GB
data_sessions	INT	540	Number of data sessions

3. Project Tasks & Deliverables
The project is divided into 4 phases. Complete them in order — each phase builds on the last. The estimated time per phase is shown below.
Phase	Deliverable	Skills Used	Difficulty
Phase 1 (Week 1)	Data Loading, Cleaning & Quality Report	Python / Excel, Pandas	Beginner-Intermediate
Phase 2 (Week 2)	Exploratory Data Analysis (EDA) with Charts	Pandas, Matplotlib / Seaborn	Intermediate
Phase 3 (Week 2-3)	Churn KPI Calculations & Insights	Python / SQL / Excel	Intermediate
Phase 4 (Week 3-4)	Dashboard + Management Summary Report	Power BI / Excel / Python	Intermediate
