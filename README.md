# 📝 Coursework Assignment Collector

A secure, serverless, and fully responsive web portal designed for university students to submit coursework and assignments. The portal captures student details, assignment descriptions, and screenshot evidence, automatically saving the data into a Google Spreadsheet and Google Drive using Google Apps Script.

---

## ✨ Features

* **Real-Time Global Counter:** Fetches and displays the total number of submissions directly from the database (Google Sheets) on page load.
* **Access Code Protection:** Submissions are gatekept by a specific student access code to prevent unauthorized or spam entries.
* **Strict File Validation:** * Allows a maximum of **6 images** per submission.
  * Validates each image to ensure it is strictly **250KB or under** before uploading.
* **Smart Text Limits:** The description box includes a live word counter capped at 100 words.
* **Interactive UI/UX:** Features a sleek modal interface, dynamic toast notifications (Loading, Success, Error), and fluid typography.
* **Fully Responsive:** Optimized for both desktop monitors and mobile devices (prevents iOS auto-zoom on inputs).

---

## 🛠️ Tech Stack

* **Frontend:** HTML5, CSS3, Vanilla JavaScript.
* **Backend / Database:** Google Apps Script, Google Sheets, Google Drive.
* **Data Transfer:** Base64 Image Encoding & JSON Payloads via `fetch()` API.

---

## 🚀 Setup & Deployment Guide

This project requires two parts to work: hosting this frontend code (e.g., on GitHub Pages) and deploying a Google Apps Script to act as your backend API.

### Phase 1: Backend (Google Workspace)

1. **Create the Database:** Create a new Google Sheet named `Assignment Submissions`.
2. **Create the Storage:** Create a folder in Google Drive named `Assignment Uploads`. Open it and copy the **Folder ID** from the URL (the random string of characters after `/folders/`).
3. **Write the Script:**
   * Open your Google Sheet.
   * Go to **Extensions > Apps Script**.
   * Replace the default code with a `doPost(e)` function to handle incoming data and a `doGet(e)` function to return the total row count. 
   * *Ensure your backend script checks for the same `secretKey` sent by the frontend before writing to the Sheet.*
4. **Deploy as Web App:**
   * Click **Deploy > New deployment**.
   * Choose **Web app**.
   * Execute as: **Me**.
   * Who has access: **Anyone**.
   * Copy the generated **Web App URL**.

### Phase 2: Frontend Configuration

1. Clone this repository to your local machine:
   ```bash
   git clone [https://github.com/yourusername/assignment-collector.git](https://github.com/yourusername/assignment-collector.git)
