# YouTube Copyright Scanner

An AI-assisted automation workflow built with n8n that analyzes YouTube videos for potential copyright matches and routes higher-risk results for human review.

> Portfolio Project — MV Design

---

## Overview

The YouTube Copyright Scanner is an automation system designed to help identify potential copyright risks in submitted YouTube videos.

Instead of manually searching YouTube and reviewing every possible match, the workflow automates the initial research and evaluation process.

The system:

1. Receives a submitted YouTube video ID
2. Retrieves information about the original video
3. Searches YouTube for potential matching content
4. Normalizes and processes candidate videos
5. Performs a copyright scan
6. Evaluates the potential copyright risk
7. Determines whether human review is required
8. Sends an email notification when review is required

---

## Workflow Architecture

```text
                    ┌─────────────────────┐
                    │   Submitted Video   │
                    │      Video ID       │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │  Get Original Video │
                    │    YouTube API      │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Search YouTube    │
                    │  Candidate Videos   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Normalize Candidates│
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Process Candidates  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Copyright Scan    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │  Risk Evaluation    │
                    └──────────┬──────────┘
                               │
                         ┌─────┴─────┐
                         │           │
                         ▼           ▼
                      SAFE       REVIEW
                                   REQUIRED
                                      │
                                      ▼
                              ┌─────────────┐
                              │ Gmail Alert │
                              └─────────────┘


## Problem

Manually checking a YouTube video for potential copyright matches can involve:

Searching for similar videos
Reviewing multiple candidates
Comparing video information
Evaluating potential matches
Deciding which cases require further investigation
Notifying a person responsible for review

This can become repetitive and time-consuming.

The goal of this project is to automate the initial screening process while keeping a human involved when a result requires additional review.


## Solution

The workflow uses n8n to connect the different stages of the process.

1. Video Submission

The workflow receives a YouTube video ID.

2. Original Video Retrieval

The workflow retrieves information about the submitted video using the YouTube API.

3. Candidate Search

YouTube is searched for videos that may potentially match or relate to the submitted content.

4. Candidate Processing

The returned candidates are normalized and processed so that they can be evaluated consistently.

5. Copyright Scan

The workflow performs an automated copyright scan against the candidate results.

6. Risk Evaluation

The results are evaluated to determine whether the situation appears safe or requires additional human review.

7. Human Review

When the workflow determines that a result requires review, an email notification is generated.


## Automation Concepts Demonstrated

This project demonstrates several important automation concepts:

API integration
Webhooks
Data transformation
Candidate filtering
Conditional branching
Automated decision-making
AI-assisted analysis
Human-in-the-loop workflows
Email notifications
Multi-step workflow orchestration
Error and edge-case handling



## Technology Stack

| Technology       | Purpose                               |
| ---------------- | ------------------------------------- |
| n8n              | Workflow automation and orchestration |
| YouTube Data API | Retrieve and search YouTube data      |
| AI               | Assist with analysis and evaluation   |
| Gmail            | Review notifications                  |
| JavaScript       | Data transformation and logic         |
| REST APIs        | Application integration               |
| GitHub           | Version control and documentation     |


## Example Workflow

A simplified execution looks like:

Input YouTube Video
        ↓
Retrieve Video Data
        ↓
Search Potential Matches
        ↓
Process Candidates
        ↓
Copyright Scan
        ↓
Evaluate Risk
        ↓
      Decision
     /        \
    /          \
 SAFE       REVIEW REQUIRED
               ↓
          Email Notification


## Human-in-the-Loop Design

The system is not intended to automatically make a final legal determination about copyright ownership.

Instead, automation is used to perform the initial screening and identify cases that may require additional investigation.

This creates a workflow where:

Automation
     ↓
Initial Analysis
     ↓
Risk Assessment
     ↓
Human Review

The human remains responsible for reviewing cases that require further investigation.


## Current Status

Status: Portfolio Project / In Development

The core workflow has been built and tested as an automation learning project.

Future improvements may include:

More sophisticated similarity analysis
Better candidate filtering
Additional video metadata analysis
Improved risk scoring
Persistent scan history
Dashboard or reporting interface
More detailed audit logs
Automated testing
Production deployment


## Project Goals

This project was built to explore how AI and workflow automation can be combined to create systems that perform multi-step analysis with minimal manual intervention.

The main learning goals were:

1. Building multi-step n8n workflows
2. Working with external APIs
3. Processing and transforming API responses
4. Creating conditional workflow branches
5. Combining automation with AI analysis
6. Designing human-in-the-loop systems
7. Documenting an automation project for production-style use

## Author

MV Design

Building AI-Powered Business Automation

GitHub:
https://github.com/mvdesignautomation

##



Portfolio:
https://mvdesignautomation.github.io/

