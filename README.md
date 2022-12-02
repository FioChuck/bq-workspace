# Overview

TL;DR
A GCP BigQuery Dataform project to copy tables partitioned on ingestion time and maintain partitioning structure.

# Setup

Source Table

```sql
CREATE TABLE
  dataform.secondary_transactions (name STRING,
    transaction_id STRING,
    date DATE)
PARTITION BY
  DATE_TRUNC(_PARTITIONTIME, HOUR)
```

Target Table

```sql
CREATE TABLE
  dataform.transactions (name STRING,
    transaction_id STRING,
    date DATE)
PARTITION BY
  DATE_TRUNC(_PARTITIONTIME, HOUR)
```

| Action Secret              | Value                                                          |
| -------------------------- | -------------------------------------------------------------- |
| CREDENTIALS_GPG_PASSPHRASE | Service Account Key used to authenticate GitHub to GCP Project |
