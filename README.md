# Daily Diary Generator

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
