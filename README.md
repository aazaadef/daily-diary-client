# Daily Diary Generator – Client-Side Web Application

## Overview

This project defines a **fully client-side web application** that generates a `daily_diary.xlsx` dataset from two Excel input files.

The application must run entirely in the browser using:

- HTML
- CSS
- JavaScript

No backend server, Python runtime, database, or external API is allowed.

---

## Goal

Build a browser-based tool that:

1. accepts a **Detailed Diary** Excel file
2. accepts a **Metadata** Excel file
3. asks the user for:
   - Country
   - Group
4. generates a final Excel file named:

`daily_diary.xlsx`

---

## Deployment Constraint

This application must be **serverless** and **client-side only**.

That means:

- no FastAPI
- no Node.js backend
- no Python backend
- no server execution
- no remote processing

All file reading, transformation, aggregation, and Excel generation must happen inside the browser.

---

## Input Files

### 1. Detailed Diary File

Example:

`samples/detailed_diary.xlsx`

This file contains event-level behavioral observations.

### 2. Metadata File

Example:

`samples/Papoilas.xlsx`

This file contains participant metadata such as sex, birth date, and code.

---

## User Inputs

The application must ask the user for:

- Country
- Group

These values must be written into the final output file.

---

## Output File

The final output must be an Excel file named:

`daily_diary.xlsx`

The output columns must be exactly:

1. `date`
2. `actor`
3. `receiver`
4. `dyad (AB is different from BA)`
5. `actor sex (male=0, female=1)`
6. `receiver sex (male=0, female=1)`
7. `actor age (months)`
8. `receiver age (months)`
9. `kinship (no kin=0, siblings =1, other kinship relation (cousins) = 2) if you do not have data NA (not applicable)`
10. `daily observation minutes of actor (from scan)`
11. `daily observation minutes of receiver (from scan)`
12. `daily observation minutes for dyad (from scan)`
13. `total number of daily aggression of the dyad`
14. `total number of daily social play interaction of the dyad`
15. `total number of social play with body contact of the dyad`
16. `total number of social play without body contact of the dyad`
17. `total number of social play with object of the dyad`
18. `total number of social play without object of the dyad`
19. `total number of play fighting of the dyad`
20. `total number of locomotor/acrobatic play of the dyad`
21. `total number of tickle of the dyad`
22. `total number of other of the dyad`
23. `total number of daily solitary play of child`
24. `total number of solitary play with object`
25. `total number of solitary play without object`
26. `total number of body contact interactions of dyad`
27. `total number of food sharing of dyad`
28. `total number of other affiliation of dyad`
29. `country`
30. `group`
31. `note`

---

## Data Rules

- Empty values must remain empty.
- The three columns:
  - `daily observation minutes of actor (from scan)`
  - `daily observation minutes of receiver (from scan)`
  - `daily observation minutes for dyad (from scan)`

  must always contain the same value for each row.

- If a child has no solitary play, do not create a solitary-play row for that child.
- For solitary play rows, the `dyad (AB is different from BA)` field must be empty.
- If a field has no value, leave it blank.
- `country` and `group` must come from the user form.
- The final file must be downloadable directly in the browser.

---

## Technical Requirements

The app must:

- read Excel files in the browser
- process and aggregate data in JavaScript
- generate Excel output in the browser
- use a clean, simple UI
- require no installation for end users

Recommended browser-side Excel library:

- SheetJS (xlsx)

---

## Expected User Workflow

1. User opens `app.html`
2. User uploads the Detailed Diary file
3. User uploads the Metadata file
4. User enters Country
5. User enters Group
6. User clicks **Generate**
7. Browser generates and downloads `daily_diary.xlsx`

---

## Antigravity Usage

Use `SKILL.md` as the project entry point.

The agent must read:

- `SKILL.md`
- `README.md`
- all files in `skills/`
- the sample files in `samples/`

before implementation.

---

## Final Outcome

The final deliverable must be a working browser-only application implemented with HTML, CSS, and JavaScript that produces the required aggregated Excel output without any backend server.# Daily Diary Generator

A **fully client-side** web application that generates a Daily Diary dataset from observational play behavior data.

## ✨ No installation required

Just open `app.html` in any modern browser (Chrome, Firefox, Edge, Safari).

Nothing is uploaded to any server. All processing happens on your computer.

---

## How to Use

1. Open `app.html` in your browser
2. Upload your **Detailed Behaviour dataset** (e.g. `detailed_diary.xlsx`)
3. Upload your **Metadata dataset** (e.g. `Papoilas.xlsx`)
4. Enter **Country** and **Group**
5. Click **Generate Daily Diary**
6. The output file `daily_diary_output.xlsx` downloads automatically

---

## Input Files

### 1. Detailed Behaviour Dataset
Columns needed (name matching is flexible, case-insensitive):
- `date` / `Date` / `Data`
- `actor` / `Actor`
- `receiver` / `Receiver`
- `target behaviours` / `behaviours` / `comportamento`
- `Duration` (optional)

### 2. Metadata Dataset
Columns needed:
- `Code` / `Código` / `ID`
- `Gender` / `Género` / `Sex`
- `Data de nascimento` / `birthdate` / `DOB`

---

## Output

An Excel file (`daily_diary_output.xlsx`) with columns:
- date, actor, receiver, dyad
- actor sex, receiver sex
- actor age (months), receiver age (months)
- kinship, observation minutes
- aggression counts, social play counts, solitary play counts, affiliation behaviours
- country, group

---

## Technical Notes

- Uses [SheetJS](https://sheetjs.com/) for Excel reading/writing (loaded from CDN)
- Requires internet connection only to load SheetJS on first use
- No Python, no server, no installation
