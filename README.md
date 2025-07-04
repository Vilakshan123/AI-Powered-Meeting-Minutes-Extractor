# 🧠 AI-Powered Meeting Minutes Extractor

A lightweight **Node.js + Express** backend service that uses the **OpenAI API** to analyze meeting notes and return structured summaries, key decisions, and action items in JSON format.

---

## 🎯 Project Goal

This API allows you to:

- Submit raw meeting notes (as text or `.txt` file)
- Automatically extract:
  - ✅ A 2–3 sentence **summary**
  - ✅ A list of **key decisions**
  - ✅ A structured list of **action items** (`task`, `owner`, `deadline`)
- Receive results as a clean, well-structured **JSON response**

---

## 🛠️ Tech Stack

| Area           | Details             |
|----------------|---------------------|
| **Language**   | JavaScript          |
| **Framework**  | Node.js + Express.js|
| **AI Provider**| OpenAI API (GPT)    |
| **Endpoints**  | `POST /process-meeting` |
| **Input Format**| Raw text or `.txt` file |
| **Output Format**| JSON               |

---

## 📁 Project Structure

```
AI-Powered-Meeting-Minutes-Extractor/
├── routes/
│   └── meeting.js            # Route handler for POST /process-meeting
├── utils/
│   └── openai.js             # OpenAI API interaction logic
├── samples/
│   ├── team_sync_1.txt       # Sample meeting file 1
│   └── team_sync_2.txt       # Sample meeting file 2
├── .env                      # API key configuration
├── app.js                    # Express app entry point
├── package.json
└── README.md                 # Project documentation
```

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Vilakshan123/AI-Powered-Meeting-Minutes-Extractor.git
cd AI-Powered-Meeting-Minutes-Extractor
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Add Your OpenAI API Key

Create a `.env` file in the root directory:

```
OPENAI_API_KEY=your_openai_api_key_here
```

### 4. Start the Server

```bash
node app.js
```

By default, the server runs at: `http://localhost:3000`

---

## 🧪 API Usage

### 🔹 Endpoint

```
POST /process-meeting
```

### 🔹 Request Options

You can send either:
- Raw text in the JSON body
- `.txt` file using `multipart/form-data`

---

### 📬 Example 1: Using Raw Text (`curl`)

```bash
curl -X POST http://localhost:3000/process-meeting \
-H "Content-Type: application/json" \
-d '{
  "text": "Team Sync – May 26\n\n- We’ll launch the new product on June 10.\n- Ravi to prepare onboarding docs by June 5.\n- Priya will follow up with logistics team on packaging delay.\n- Beta users requested a mobile-first dashboard."
}'
```

### 📬 Example 2: Using Postman

- Method: `POST`
- URL: `http://localhost:3000/process-meeting`
- Choose:
  - `Body > raw > JSON` (for text input), or
  - `Body > form-data` with key `file` (to upload `.txt`)

---

## 🧾 Sample Input

Sample meeting notes (`text` or `.txt` file content):

```
Team Sync – May 26

- We’ll launch the new product on June 10.
- Ravi to prepare onboarding docs by June 5.
- Priya will follow up with logistics team on packaging delay.
- Beta users requested a mobile-first dashboard.
```

---

## 📤 Sample Output

```json
{
  "summary": "The team confirmed the product launch on June 10, assigned onboarding preparation and logistics follow-up, and discussed user feedback on mobile design.",
  "decisions": [
    "Launch set for June 10",
    "Need mobile-first dashboard for beta users"
  ],
  "actionItems": [
    {
      "task": "Prepare onboarding docs",
      "owner": "Ravi",
      "due": "June 5"
    },
    {
      "task": "Follow up with logistics team",
      "owner": "Priya"
    }
  ]
}
```

---

## ⚠️ Error Handling

The API will return appropriate error messages for:

- Missing input (neither `text` nor file provided)
- API key/token errors
- Timeout or network issues
- Invalid file types

---

## 🧷 Sample Files Included

You can test the API with the following sample `.txt` files in the `/samples` folder:

- `team_sync_1.txt`
- `team_sync_2.txt`

---

## ⏱️ Timeline

- Project delivery expected within **2 days**
- Contains:
  - Source code
  - 2 sample files
  - README with usage instructions and sample output

---

## 🙋‍♂️ Contact

Developed by [Vilakshan Panchal](https://www.linkedin.com/in/vilakshanpanchal)

For support or questions, feel free to raise a GitHub issue or connect via LinkedIn.

---
