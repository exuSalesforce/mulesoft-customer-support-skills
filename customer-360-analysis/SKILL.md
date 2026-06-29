---
name: Customer 360 Analysis
description: Build comprehensive customer profiles by orchestrating CRM, support, and billing data.
version: 1.1.0
author: data-team@acme.com
tags: [customer, analytics, multi-tool]
---

# Customer 360 Analysis

## When to use
Invoke when a user needs a complete view of a customer account, including CRM status, support history, and billing.

## MCP Servers Required
- **Salesforce MCP Server** (mcp-006): CRM data — accounts, contacts, opportunities
- **Zendesk MCP Server** (mcp-014): Support tickets, CSAT scores
- **SAP S/4HANA OData MCP Server** (mcp-001): Billing profile, payment history

## Workflow

### Step 1: Fetch CRM Data
- get_account: Account health score, owner, industry, last interaction date
- get_opportunity: Open pipeline, deal stages, expected close dates

### Step 2: Pull Support History
- search_tickets: All tickets from last 90 days, grouped by priority
- Calculate CSAT trend and average resolution time

### Step 3: Get Billing Profile
- query_business_partners: Payment terms, credit status, outstanding balance

### Step 4: Synthesize
Combine into unified profile with:
- Account health summary
- Support sentiment (positive / neutral / at-risk)
- Revenue and billing status
- Recommended next actions

## Output Format
- Account name, owner, and tier
- Health score with trend arrow
- Top 3 open opportunities with stage
- Support summary (open tickets, CSAT, last escalation)
- Billing status (current / overdue / at-risk)