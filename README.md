# YouTube Copyright Scanner

An automated YouTube copyright risk screening workflow built with n8n that analyzes potential video matches, evaluates copyright risk using configurable rules, and routes higher-risk results for human review.

> **Portfolio Project — MV Design**

---

## Overview

The YouTube Copyright Scanner automates the initial screening process for potential copyright matches on YouTube.

The workflow accepts a YouTube video, retrieves information about the original content, searches for potential matching videos, processes the candidates, evaluates matching signals, and routes higher-risk results for human review.

The system is designed as an **initial screening and automation workflow**, not as a system that makes a final legal determination of copyright ownership.

---

## Workflow Architecture

```text
Video Submission
       |
       v
Extract Video ID
       |
       v
Get YouTube Channel
       |
       v
Get Original Video
       |
       v
Search YouTube Candidates
       |
       v
Normalize Candidates
       |
       v
Get Candidate Details
       |
       v
Process Candidates
       |
       v
Copyright Scan
       |
       v
Is Original?
    /       \
  YES        NO
   |          |
   |          v
   |    Evaluate Copyright Risk
   |          |
   |       Risk Level
   |          |
   |      MEDIUM / HIGH
   |          |
   |          v
   |    Review Required
   |          |
   |          v
   |      Gmail Alert
   |
   v
Prepare Results
       |
       v
Google Sheets
```

---

## Problem

Manually screening YouTube videos for potential copyright matches can require repetitive work:

- Finding potential matching videos
- Reviewing candidate video information
- Comparing channels and video metadata
- Identifying possible matching signals
- Determining which cases need additional review
- Notifying the person responsible for investigation
- Recording the results

The goal of this project is to automate the initial screening process and reduce repetitive manual work.

---

## Solution

The workflow connects YouTube, n8n, Gmail, and Google Sheets into a multi-step automation.

### 1. Video Submission

The workflow receives a YouTube video URL through an n8n form.

### 2. Extract Video ID

The submitted URL is processed to extract the YouTube video ID.

### 3. Retrieve Original Video

The workflow retrieves information about the submitted video through the YouTube Data API.

### 4. Search for Candidates

YouTube is searched for potential candidate videos that may be related to the submitted content.

### 5. Normalize Candidates

Candidate results are normalized into a consistent structure for further processing.

### 6. Retrieve Candidate Details

Additional information about candidate videos is retrieved from YouTube.

### 7. Process Candidates

Candidate information is prepared for comparison and evaluation.

### 8. Copyright Scan

The workflow evaluates several matching signals.

The current scoring logic includes:

| Matching Signal | Score |
|---|---:|
| Same video ID | +100 |
| Same YouTube channel | +40 |
| Exact title match | +30 |

The resulting score is used to classify the candidate risk level.

### 9. Risk Evaluation

The workflow evaluates the copyright scan result and determines whether additional review is required.

### 10. Human Review

Higher-risk results are routed to a review-required path.

A Gmail notification is generated so that a person can investigate the result.

### 11. Results Logging

Workflow results are prepared for storage in Google Sheets.

---

## Risk Classification

The copyright scan uses configurable rules to calculate a matching score.

The current workflow uses the following categories:

```text
ORIGINAL
HIGH
MEDIUM
LOW
```

These classifications are intended to support **initial screening**, not to establish legal copyright ownership.

---

## Human-in-the-Loop Design

The workflow deliberately keeps a human involved in higher-risk cases.

```text
Automation
     |
     v
Candidate Analysis
     |
     v
Risk Evaluation
     |
     v
Review Required
     |
     v
Human Investigation
```

This approach allows automation to handle repetitive screening while keeping final investigation and judgment with a human reviewer.

---

## Key Features

- YouTube Data API integration
- n8n form submission
- Automated video ID extraction
- Candidate video discovery
- Video metadata processing
- Rule-based copyright risk scoring
- Conditional workflow branching
- Human-in-the-loop review
- Gmail notifications
- Google Sheets logging
- Multi-step workflow orchestration

---

## Technology Stack

| Technology | Purpose |
|---|---|
| n8n | Workflow automation and orchestration |
| YouTube Data API v3 | Retrieve and search YouTube data |
| JavaScript | Data transformation and scoring logic |
| Gmail | Review notifications |
| Google Sheets | Results logging |
| REST APIs | Application integration |
| GitHub | Version control and project documentation |

---

## Automation Concepts Demonstrated

This project demonstrates:

- API integration
- Form-based workflows
- Data extraction
- Data normalization
- Data transformation
- Conditional branching
- Rule-based decision logic
- Risk scoring
- Human-in-the-loop automation
- External service integration
- Automated notifications
- Results logging
- Multi-step workflow orchestration

---

## Example Execution

```text
YouTube Video URL
        |
        v
Extract Video ID
        |
        v
Retrieve Video Data
        |
        v
Search Candidate Videos
        |
        v
Process Candidates
        |
        v
Copyright Scan
        |
        v
Evaluate Risk
        |
        v
   +----+----+
   |         |
 SAFE     REVIEW
            REQUIRED
               |
               v
          Gmail Alert
               |
               v
        Google Sheets
```

---

## Security

Credentials and private configuration have been removed from the published workflow.

The public workflow contains placeholders instead of:

- YouTube API keys
- OAuth credential information
- Private email addresses
- Google Sheets identifiers
- Private webhook information

To run the workflow, users must configure their own credentials and service connections in n8n.

---

## Current Status

**Status:** Portfolio Project / In Development

The core automation workflow has been built and tested as an automation learning and portfolio project.

---

## Testing

The workflow has been tested end-to-end in a self-hosted n8n environment.

Verified components include:

- YouTube Data API integration
- Video metadata retrieval
- Candidate video search
- Candidate processing
- Copyright scan
- Risk evaluation
- Google Sheets result logging
- Workflow branching

---

### Future Improvements

- More sophisticated video similarity analysis
- Additional matching signals
- Improved candidate filtering
- More advanced risk scoring
- Persistent scan history
- Dashboard or reporting interface
- Detailed audit logs
- Automated testing
- Production deployment
- Additional notification channels
  
---

## Project Goals

This project was built to explore how workflow automation can be used to create a multi-step screening system with external API integrations, automated decision logic, and human review.

The main learning goals were:

1. Building multi-step n8n workflows
2. Integrating external APIs
3. Processing and transforming API responses
4. Creating conditional workflow branches
5. Implementing rule-based risk scoring
6. Designing human-in-the-loop systems
7. Connecting multiple business services
8. Preparing an automation workflow for portfolio presentation

---

## Author

**MV Design**

Building AI-Powered Business Automation

[GitHub](https://github.com/mvdesignautomation)

[Portfolio](https://mvdesignautomation.github.io/)
