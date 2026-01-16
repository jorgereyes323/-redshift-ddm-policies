# Redshift Dynamic Data Masking (DDM) Policies

Amazon Redshift Jupyter Notebook for implementing Dynamic Data Masking policies for DDMAP sensitive data.

## Overview

This repository contains Redshift DDM policies for protecting sensitive data including:
- SSN/TIN numbers (SHA2 hashing)
- PII fields (Full redaction)
- Date of Birth (Masked to 1900-01-01)
- Numeric identifiers (Masked to 999)
- ZIP codes (Partial masking)

## Contents

- `DDMAP_DDM_Policies.ipynb` - Main Redshift notebook with DDM policies

## Masking Policies

### SHA2 Hash Masking
- Applied to SSN, TIN, and account numbers
- Uses SHA2-256 hashing for one-way encryption

### Full Redaction
- Applied to names, addresses, contact information
- Replaces values with `*REDACTED*`

### Date Masking
- Applied to date of birth fields
- Replaces with `1900-01-01`

### Numeric Masking
- Applied to numeric identifiers
- Replaces with `999`

## Roles

- **admin_role** - Full access to unmasked data
- **analyst_role** - Partial access with some masking
- **regular_role** - Full masking applied

## Usage

1. Open the notebook in Amazon Redshift Query Editor V2
2. Execute cells sequentially to create roles and policies
3. Attach policies to appropriate tables and columns

## Tables Covered

- xstg_* tables (external staging)
- tstg_* tables (temporary staging)
- tfac_* tables (fact tables)
- tdim_* tables (dimension tables)

## Requirements

- Amazon Redshift cluster
- Superuser or sys:secadmin privileges
- Redshift Query Editor V2 or compatible notebook environment