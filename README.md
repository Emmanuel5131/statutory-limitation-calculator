# Statutory Limitation Period Calculator

A Python and Jupyter Notebook project that parses user dates, loads structural legal databases (`Laws.json`), and calculates statutory limitation deadlines across multiple global jurisdictions (UK, USA, Nigeria, Australia).

This project documents my iterative problem-solving and debugging journey as I built out input loops, data types, and search algorithms for my very first repository!

---

## 🛠️ Project Structure
- `index.ipynb`: The main Jupyter Notebook detailing code cells, experimental tests, and final logic blocks.
- `Laws.json`: A structured dataset containing 50 statutory limitation rules with rule IDs, jurisdictions, claim types, and legal citations.

---

## 📈 Learning Journey & Iterative Mistakes Overcome

Building this project involved troubleshooting several common programming hurdles:

### 1. Date Input Validation & Looping
* **The Mistake:** Initial input prompts crashed or trapped execution when users typed invalid dates or forgot standard formatting.
* **The Fix:** Implemented a robust `while True` loop combined with `try...except ValueError` blocks to cleanly catch incorrect inputs and prompt the user again without breaking the script.

### 2. Handling `timedelta` Limitations
* **The Mistake:** Attempted to pass years directly into Python's `timedelta(years=val)`, which raised a `TypeError` because `timedelta` only accepts days, seconds, weeks, etc.
* **The Fix:** Created a normalization step converting multi-year or multi-month blocks into standard day integers (`val * 365` for years, `val * 30` for months) before running date arithmetic.

### 3. Case-Insensitive Search & `NoneType` Handling
* **The Mistake:** Strict string lookups failed when queries had mismatched casing (e.g., searching `"tort"` vs `"Actions founded on tort"`), and optional fields containing `null` values caused crashes.
* **The Fix:** Standardized search logic by converting both search queries and database fields to lowercase strings (`str(rule.get(field, "")).lower()`), ensuring partial and case-insensitive matching.

---

## 🚀 How to Run Locally

1. Clone or download this repository.
2. Ensure `index.ipynb` and `Laws.json` are in the same directory.
3. Open Jupyter Notebook and run through the cells sequentially:
   ```bash
   jupyter notebook index.ipynb
