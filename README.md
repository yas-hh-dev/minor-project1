# minor-project1
# WhatsApp Chat Analyzer (From Scratch)

A lightweight, purely procedural Python text-processing pipeline that transforms raw, unformatted WhatsApp chat export logs (`.txt`) into a clean, screenshot-ready terminal analytics dashboard. 

This project was built entirely from scratch using fundamental Python data structures and **NumPy**—explicitly avoiding advanced high-level libraries like Pandas or built-in utilities like `collections.Counter`.

---

## Features Implemented

### 1. Structural Regex-Free File Parsing & Cleaning
* Processes raw logs line-by-line using index-based character matching (`/` and `:` timestamps).
* Smartly handles **multi-line messages** by stitching broken trailing text blocks back into the last active message dictionary.
* Identifies, flags, and separates human conversational content from background system-level updates (e.g., group creations, contact additions).

### 2. Group Overview & Leaderboard Statistics
* Tracks unique chat participants using Python `set` collections to avoid redundant allocations.
* Tally-counts overall individual contributions using custom dictionary scores.
* Compiles a ranked leaderboard sorted in descending order to automatically identify top participants alongside their total percentage group shares.

### 3. Peak Activity Time Tracking
* Extracts temporal data fragments to compute the single overall busiest calendar date across the dataset.
* Normalizes time frames to track hour-by-hour (00:00 to 23:00) group volume trends, identifying the absolute rush-hour of the chat group.

### 4. Text-Art Activity Heatmap Matrix (Powered by NumPy)
* Initializes and manages a `6x24` two-dimensional mathematical matrix using **NumPy** (`np.zeros`).
* Maps each chat participant to a dedicated row index and links each hour to a specific column index.
* Normalizes data rows against each individual's personal messaging peak, converting numbers into custom text-shading thresholds (`.`, `░`, `▒`, `▓`, `█`) to generate a console heatmap.

### 5. Custom Word Frequency Engine & Bar Graphs
* Converts chat strings into tokenized lowercase collections to guarantee uniform matching.
* Cleans boundary punctuation characters (e.g., `,`, `.`, `!`, `?`) from words using custom strip rules.
* Filters out custom academic stop-word arrays to surface truly unique conversational vocabulary.
* Renders a custom terminal horizontal bar chart using block characters (`█`) scaled proportionally to the raw frequency totals.

---

## 🛠️ Constraints Met
* **No Pandas / Polars:** Data is structured solely using basic dictionaries and lists.
* **No `collections.Counter`:** All word tokenization and frequency metrics use manual loops and structural `if-else` tallies.
* **No Graphical Engines (`matplotlib` / `seaborn`):** All visual graphics, shading scales, and bar charts are rendered completely as plain text using specific formatting alignments inside the console wrapper.

---

## 📈 Sample Terminal Output Preview

```text
========================================================
GROUP OVERVIEW
========================================================
Group          : Hostel Bois 4ever
Period         : 01 April 2024 to 30 May 2024 (60 days)
Total messages : 3174
Participants   : 6
========================================================
ACTIVITY HEATMAP (messages by hour)
========================================================
           00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 16 17 18 19 20 21 22 23
Aman        █  ▓  ▒  .  .  .  .  .  ░  ░  ▒  ▒  ▒  ▓  ▓  █  ▒  ░  .  .  ░  ▒  ▓  █ 
Priya       .  .  .  .  .  .  ░  ▒  █  ▓  ▓  ▒  ▒  ▒  ▒  ░  .  .  .  ░  ▒  ▓  █  ▓ 
========================================================
GROUP'S FAVOURITE WORDS
========================================================
bhai         : 421   ████████████████████████████
scene        : 215   ██████████████
yaar         : 189   ████████████
========================================================
