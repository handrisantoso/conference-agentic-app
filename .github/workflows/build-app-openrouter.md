---
on:
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read
  issues: read

engine:
  id: codex
  model: openai/gpt-4o
  api-target: openrouter.ai
  env:
    OPENAI_API_KEY: ${{ secrets.OPENROUTER_API_KEY }}

network:
  allowed:
    - defaults
    - openrouter.ai
    - registry.npmjs.org

safe-outputs:
  create-pull-request:
    title-prefix: "[conference-site] "
    allowed-files:
      - "README.md"
      - ".env.example"
      - "package.json"
      - "package-lock.json"
      - "frontend/**"
      - "backend/**"
      - "src/**"
      - "app/**"
      - "public/**"
      - "components/**"
      - "pages/**"
      - "tests/**"
    max: 1
---

# Build International Conference Website

You are an AI software engineer. Build a full-stack website for an international academic conference.

## Goal

Create a professional international conference website with frontend and backend.

## Suggested Stack

Use:

- Frontend: React / Next.js
- Backend: Node.js / Express
- Database: JSON file or SQLite for prototype
- Styling: Tailwind CSS if suitable

## Frontend Pages

Create these pages:

1. Home
2. About Conference
3. Important Dates
4. Call for Papers
5. Speakers
6. Committee
7. Registration
8. Paper Submission
9. Program Schedule
10. Venue
11. Contact

## Frontend Features

The website should include:

- Modern academic conference design
- Hero section
- Conference title
- Conference date and location
- Countdown or important dates section
- Keynote speaker cards
- Topic tracks
- Registration button
- Paper submission button
- Responsive layout for desktop and mobile

## Backend Features

Create backend API endpoints for:

1. Conference information
2. Speaker list
3. Committee list
4. Important dates
5. Registration form submission
6. Paper submission metadata
7. Contact form submission

## Example API Routes

- GET /api/conference
- GET /api/speakers
- GET /api/committee
- GET /api/dates
- POST /api/register
- POST /api/submit-paper
- POST /api/contact

## Data Model

Registration should include:

- Full name
- Institution
- Email
- Country
- Participant type
- Payment status placeholder

Paper submission should include:

- Paper title
- Authors
- Corresponding email
- Abstract
- Keywords
- Track
- File upload placeholder

## Security Requirements

- Do not expose OpenRouter API key to frontend
- Do not commit real secrets
- Use environment variables
- Add .env.example
- Add basic input validation
- Add README setup guide

## Deliverables

Create a pull request containing:

1. Full project source code
2. README.md with installation instructions
3. .env.example
4. Frontend and backend structure
5. Basic test or sample API testing instructions

## Output

Create one pull request with the complete implementation.