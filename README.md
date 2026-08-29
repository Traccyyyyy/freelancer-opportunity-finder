# Freelancer Opportunity Finder

An AI-assisted job monitoring project that combines web scraping, Microsoft Power Platform and Copilot Studio to collect, store, filter and summarise Freelancer.com project listings.

## Architecture

```text
Freelancer.com
    ↓
Puppeteer scraper (Node.js)
    ↓
Power Automate webhook
    ↓
Dataverse
    ↓
Copilot Studio
    ↓
Power Automate query/filter flow
    ↓
Matched projects + GPT-generated summary
```

## What it does

- Scrapes Freelancer.com project listings with Puppeteer.
- Filters listings by keywords and budget rules.
- Tracks previously sent project URLs to reduce duplicates.
- Sends new project data to a Power Automate webhook.
- Stores structured project data in Dataverse.
- Uses Copilot Studio to interpret user requests such as keywords and budget.
- Triggers Power Automate flows to query and filter Dataverse records.
- Returns matched projects and can generate a project summary and suggested next steps.

## Technology

- Node.js
- Puppeteer
- Axios
- Microsoft Power Automate
- Microsoft Dataverse
- Microsoft Copilot Studio
- GPT-based prompt logic

## Key files

- `send.js` — scraper and webhook integration.
- `sent_projects.json` — local history used to avoid resending the same projects.
- `docs/copilot-agent-logic.txt` — Copilot Studio topic/interaction logic.
- `docs/example-user-intent-prompt.txt` — prompt example for extracting search intent.
- `docs/test-and-error-handling.txt` — end-to-end test and troubleshooting notes.
- `docs/power-automate-overview.png` — Power Automate workflow evidence.
- `docs/power-automate-details-1.png` / `docs/power-automate-details-2.png` — flow details.
- `docs/dataverse-schema.png` — Dataverse table schema evidence.

## Setup

1. Install dependencies:

```bash
npm install
```

2. Copy the environment template and provide your own Power Automate webhook URL:

```bash
cp .env.example .env
```

3. Run the scraper:

```bash
node send.js
```

The local `.env`, dependency folder and runtime logs are intentionally excluded from version control.

## Testing and troubleshooting

The repository includes an end-to-end testing guide covering:

- scraper execution;
- webhook delivery;
- Dataverse persistence;
- Copilot Studio queries;
- Power Automate run-history checks;
- common integration failures.

See `docs/test-and-error-handling.txt`.

## Project scope

This is a portfolio project demonstrating Power Platform workflow automation, Dataverse integration, browser automation and Copilot Studio orchestration. It is not presented as a production-scale service.
