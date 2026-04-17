# Submitter: University Assignment Portal

**Submitter** is a lightweight, responsive web application designed for university students to securely upload assignment screenshots and metadata. It replaces messy email threads and manual tracking with a centralized **Google Sheets database**.

## 🚀 Key Features

* **Multi-Image Support:** Students can upload up to 6 screenshots per submission.
* **Live Counter:** Fetches the real-time submission count directly from the database.
* **Zero-Server Hosting:** Uses Google Apps Script as a serverless backend—no monthly hosting fees.
* **Adaptive UI:** Fully responsive design built with Poppins typography for a professional academic feel.
* **Data Validation:** Prevents over-limit uploads and ensures all required fields (Matric Number, Dept, etc.) are captured.

## 🛠️ Tech Stack

* **Frontend:** HTML5, CSS3 (Custom Variables & Media Queries), JavaScript (Fetch API & Base64 Encoding).
* **Backend:** Google Apps Script (GAS).
* **Database:** Google Sheets.
* **Storage:** Google Drive (for image hosting).

---

## ⚙️ Setup Instructions

To get this portal running for your specific course, follow these steps exactly:

<Steps>
{/* Reason: This is a multi-environment setup where skipping a step (like deploying as a Web App) results in a total system failure. */}
  <Step title="Prepare the Database" subtitle="Google Sheets">
    Create a new Google Sheet and name the first row headers: `Timestamp`, `Full Name`, `Matric Number`, `Department`, `Level`, `Description`, and `Image Links`. Note the **Sheet ID** from the URL.
  </Step>
  <Step title="Configure the Backend" subtitle="Apps Script">
    Open **Extensions > Apps Script** from your sheet. Paste the provided `doPost` and `doGet` functions. Ensure you replace the `folderId` variable with the ID of a dedicated Google Drive folder where images should be stored.
  </Step>
  <Step title="Deploy as Web App" subtitle="Crucial for access">
    Click **Deploy > New Deployment**. Select **Web App**. Set 'Execute as' to **Me** and 'Who has access' to **Anyone**. Copy the provided **Web App URL**.
  </Step>
  <Step title="Connect the Frontend" subtitle="HTML Update">
    In your `index.html` file, find the `GOOGLE_SCRIPT_URL` constant and paste your Web App URL between the quotes.
  </Step>
</Steps>

---

## 📂 Project Structure

```text
├── index.html        # The main frontend (UI, Logic, and Styles)
├── backend.gs        # The Google Apps Script code (Server-side)
└── README.md         # Project documentation
```

## 🛡️ Security & Limitations

* **CORS Handling:** The script includes a `doOptions` function to handle browser pre-flight requests.
* **File Size:** Google Apps Script has a payload limit of ~50MB. Encourage students to keep screenshots under 5MB each for optimal performance.
* **Privacy:** Since "Anyone" has access to the Web App URL to submit, do not share the Sheet itself publicly.

---

> **Tip for University Mates:** If you are deploying this via GitHub Pages, ensure your `GOOGLE_SCRIPT_URL` uses `https` to avoid mixed-content blocking.

<FollowUp label="Want me to show you how to add a 'Submission Deadline' countdown timer to this portal?" query="How can I add a live countdown timer to the landing page that automatically disables the 'Submit' button when the assignment deadline passes?" />