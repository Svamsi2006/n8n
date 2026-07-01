# How This Project Works

## Overview

This project is an AI-powered investment research assistant built with Next.js, TypeScript, and LangGraph. It helps users analyze a company or stock by combining:

- Live financial and company data from Yahoo Finance
- Deterministic local scoring logic
- News sentiment signals
- AI-generated investment memos using LLMs

The app is designed to provide a structured research summary with a recommendation such as INVEST, WATCH, or PASS.

---

## Main Flow

### 1. User Input
A user enters either:
- a company name, or
- a stock ticker

The interface supports autocomplete suggestions so the user can quickly choose a valid symbol.

### 2. Search and Ticker Resolution
The app first tries to resolve the query into a stock ticker. This is handled by the search API, which queries Yahoo Finance and returns matching stock results.

### 3. Research Analysis
Once a ticker is selected, the analyze API starts the research workflow.

The workflow is orchestrated using LangGraph and runs in three steps:

1. Fetch Research Data
   - Resolves the ticker
   - Fetches company profile and financial metrics
   - Retrieves recent news
   - Uses retry logic and in-memory caching for reliability

2. Compute Score
   - Calculates local scores for:
     - Growth
     - Profitability
     - Risk
     - Valuation
     - News sentiment
   - Produces a weighted total score

3. Generate Memo
   - Sends the research data and score breakdown to an LLM
   - Uses Gemini first
   - Falls back to Groq if Gemini fails or times out
   - Returns a structured investment memo in JSON

---

## Core Components

### Frontend
The user interface is a Next.js page that:
- accepts search input
- shows autocomplete suggestions
- displays the final research report
- shows logs and LLM transcript details

### Backend APIs
The app has two main API routes:

- /api/search
  - Used for symbol lookup and autocomplete

- /api/analyze
  - Runs the full research workflow for a selected ticker

### Agent Logic
The core logic is implemented in the agent layer:
- It defines the workflow nodes
- Connects them in sequence
- Passes structured state between each step

---

## Why It Works Well

### Deterministic Scoring
The app does not rely only on LLMs for core numbers. It calculates financial and valuation scores locally using clear rules, which makes the output more consistent and less prone to hallucination.

### Multi-Model LLM Support
The app uses:
- Gemini as the primary model
- Groq as a fallback provider

This improves reliability if one model times out or rate-limits.

### Caching and Retries
The project includes:
- in-memory caches for repeated search and profile requests
- retry logic with exponential backoff for unreliable external APIs

This makes the system more robust in production.

---

## Output

After analysis, the app returns:

- the resolved ticker
- company name
- research data
- score breakdown
- final AI-generated memo
- provider used by the LLM
- raw transcript/log details

This gives the user both a machine-readable analysis and a human-friendly investment summary.

---

## In Short

The project works like this:

User query → ticker resolution → data collection → scoring → AI memo generation → report display

It combines traditional financial analysis with modern LLM-based reasoning in a single workflow.