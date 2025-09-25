# 🏦 Bank Data Warehouse

This repo is where we’ve created the foundational setup of a data warehouse that’s meant to work for a typical banking environment. It’s built to help make sense of data coming from different banking systems whether it’s transactions, UPI activity, customer info, or merchant operations.

The idea is to bring all of that into one place, shape it in a way that makes reporting and analytics easier, and do it in a way that works whether the bank is running on the cloud or on-prem.

It’s structured to be modular, so teams can plug in new sources or scale things out when needed. And while we’ve built this to meet compliance and reporting needs, the goal was to make it something clean and reliable something that other teams could actually reuse or build on without starting from scratch.

---

## 📌 Key Source Systems in a Digital Bank

| System              | What It’s For                                            | Tech (commonly used)             | Nature         | Example Data                          |
|---------------------|----------------------------------------------------------|----------------------------------|----------------|---------------------------------------|
| **CBS**             | Core banking — the money engine. Accounts, balances, deposits, TRMT | Oracle CBS, BaNCS, Finacle       | OLTP           | cust_id, acct_no, txn_id, balance     |
| **CRM**             | Customer info hub. KYC, contacts, preferences            | Salesforce + in-house tweaks     | OLTP / API     | email, phone, dob, KYC flag           |
| **UPI Switch**      | Routes UPI payments, logs everything (real time)         | NPCI switch, custom gateway      | OLTP+Streaming | vpa, upi_txn_id, response, payer/payee |
| **Merchant DB**     | Onboarding + merchant/terminal setup                     | MySQL / PostgreSQL               | OLTP           | merchant_id, category, region         |
| **Risk Engine**     | Fraud checks. Velocity rules, device scoring, flags bad stuff | Elastic, MongoDB, Redis          | Streaming/NoSQL| txn_id, cust_id, device_id, score     |
| **Report DB**       | A lighter CBS copy, made for RBI reports & audits        | Oracle / SQL Server              | OLAP (lite)    | snapshot tables, flattened data       |
| **Channel Logs**    | App trails — logins, OTPs, user clicks                   | ElasticSearch, Kafka             | Streaming      | user_id, device, ip, latency, screen  |
| **Reg APIs (NPCI)** | Sends data outward (compliance, TRMT, regulatory files)  | REST, flat files                 | API/File       | report_date, submission status        |

---

## 🗂️ Directory Structure

```bash
bank-data-warehouse/
├── docs/               # Diagrams, architecture, notes
├── scripts/            # SQL scripts, ETL code, transformations
├── usecases/           # Use-case-specific pipelines and marts
├── sample-dataset/     # Simulated data from CBS, UPI, CRM, etc.
└── README.md           # Project overview
```


