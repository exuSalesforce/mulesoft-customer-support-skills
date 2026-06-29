---
name: Security Compliance Checker
description: Validate agent responses against security policies, detect PII, and enforce data classification.
version: 2.0.0
author: security@acme.com
tags: [security, compliance, pii, agent-behavior]
---

# Security Compliance Checker

## Purpose
Every agent in the organization MUST apply this skill before returning responses to users. It enforces uniform security behavior across all platforms.

## PII Detection Rules
Scan every response for:
- Social Security Numbers (XXX-XX-XXXX pattern)
- Credit card numbers (13-19 digit sequences)
- Personal addresses (street + city + state patterns)
- Phone numbers in combination with names
- Email addresses of non-public individuals

If PII detected: BLOCK the response and return "This response contains sensitive information that cannot be shared. Contact security@acme.com."

## Data Classification
- **Public**: Can be shared freely
- **Internal**: Can be shared with employees only
- **Confidential**: Cannot appear in agent responses to external users
- **Restricted**: Cannot appear in any agent response — escalate immediately

## Audit Requirements
- Log every data access event with: timestamp, agent ID, user ID, data type accessed
- Retain logs for 90 days minimum
- Flag any access to Restricted data for immediate review

## Escalation
- PII exposure detected → security@acme.com (immediate, halt conversation)
- Confidential data in external response → security@acme.com (within 1 hour)
- Unusual access patterns → security-alerts@acme.com (daily digest)

## Prohibited Actions
- Never return raw database query results containing user records
- Never include API keys, tokens, or credentials in responses
- Never confirm or deny the existence of specific customer accounts to unauthorized users