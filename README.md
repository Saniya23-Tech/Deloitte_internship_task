# Data Conversion Task – Deloitte Virtual Internship

## What is this project about?

This project is part of a Deloitte virtual internship.  
The goal is to solve a common real‑world problem: **different machines send data in different formats**, but we need all the data to look the same so it can be analyzed together.

I was given two different JSON files (data‑1.json and data‑2.json) that contain telemetry information from factory machines.  
I also received an example of the **unified format** (data‑result.json) that both should be converted into.

My job was to write the conversion rules so that any data coming in either format is transformed into the unified format.

---

## The Three Formats (Simple Explanation)

### Format 1 (data‑1.json)
- Device ID and device type are given directly.
- Timestamp is a number (milliseconds).
- Location is one long string with slashes, like:  
  `"japan/tokyo/area/factory/section"`
- The machine status is called `operationStatus`.
- Temperature is called `temp`.

### Format 2 (data‑2.json)
- Device ID and type are **inside** a separate `device` object.
- Timestamp is a date‑time string (e.g., `"2021-06-23T10:57:17.783Z"`).
- Location fields are separate (`country`, `city`, `area`, `factory`, `section`).
- Status and temperature are already inside a `data` object.

### Unified Format (what both should become)
- Device ID and type are direct fields (like Format 1).
- Timestamp is a number (milliseconds).
- Location is a single object containing all five parts (`country`, `city`, `area`, `factory`, `section`).
- Status and temperature are inside a `data` object.

---

## What the Conversion Does

### From Format 1 → Unified
- Splits the long location string into five pieces and puts them into a location object.
- Renames `operationStatus` to `status` and moves it inside `data`.
- Renames `temp` to `temperature` and moves it inside `data`.
- Keeps device ID, device type, and timestamp unchanged.

### From Format 2 → Unified
- Pulls device ID and type out of the nested `device` object to make them direct fields.
- Converts the date‑time string into a number (milliseconds since 1970).
- Takes the separate location fields and groups them into one location object.
- Keeps the existing `data` object exactly as it is.

---

## How to Run the Project

1. Make sure Python is installed on your computer.
2. Download all four files (`main.py`, `data-1.json`, `data-2.json`, `data-result.json`) into the same folder.
3. Open a terminal / command prompt in that folder.
4. Run the command:  
   `python main.py`
5. The script will run three tests and print `OK` if everything is correct.

---

## What the Tests Check

- **Test 1**: Converts Format 1 and compares with the expected result.
- **Test 2**: Converts Format 2 and compares with the expected result.
- **Test 3**: Makes sure the expected result file is valid.

If all tests pass, the conversion works perfectly.

---

## Why This Matters

Companies like Deloitte often help clients integrate data from different systems.  
Being able to take messy, inconsistent data and turn it into one clean format is a valuable skill.  
This project shows that I can understand different data structures, transform them, and verify that the output is correct.

---

## Repository Contents

- `main.py` – the conversion script and tests
- `data-1.json` – sample data in Format 1
- `data-2.json` – sample data in Format 2
- `data-result.json` – the expected unified format
- `README.md` – this explanation

---

*Submitted as part of the Deloitte Virtual Internship Program.*
