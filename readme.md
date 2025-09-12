# Vibe Coding — Prototype

**Author:** Keerthi Raj  
**Role:** AI Intern Candidate — Submission for “Lovable clone: Vibe Coding” challenge  

---

## 📌 What this is
A prototype web app that generates HTML + CSS from a plain-English “vibe” prompt using an **n8n workflow** + **Google Gemini API**.  

Users type a description such as:  

> “A large rounded blue button that says *Click Me* and changes to a lighter blue on hover.”  

The system responds with generated HTML/CSS code.  

---

## 🏗️ Architecture

- **Frontend:**  
  Single `index.html` file (TailwindCSS + vanilla JS).  
  - Text input for “vibe” prompt.  
  - Sends request to n8n webhook.  
  - Displays generated HTML/CSS in a code box.  

- **Backend (n8n Workflow):**  
  1. **Webhook node** → Receives prompt from frontend (`?prompt=...`).  
  2. **HTTP Request node** → Sends the prompt to Gemini API.  
  3. **Respond to Webhook node** → Returns Gemini’s response back to frontend.  

- **AI:**  
  Google Gemini (Generative Language API).  

---

## 🌐 Live Demo (Frontend only)

GitHub Pages:  
👉 https://<your-username>.github.io/Vibe-Coding-Prototype/  

⚠️ **Note:** The frontend is live, but the backend (n8n) is running locally on my machine.  
For a working end-to-end demo, see the “Run locally” or “ngrok" .  

---

## 📂 Files in this repo

- `index.html` → static frontend UI  
- `workflow.json` → exported n8n workflow (API key replaced with placeholder `YOUR_API_KEY_HERE`)  
- `README.md` → documentation (this file)  
- (optional) `screenshots/` → demo images  

---

## ▶️ How to Run Locally

1. Serve the frontend:
   ```bash
   python -m http.server 8000
   # Open http://localhost:8000/index.html 

2. Run n8n (Docker):

docker-compose up -d
# or
docker run -it --rm -p 5678:5678 n8nio/n8n


3. Import workflow.json into n8n (Workflows → Import).

4. In the frontend (index.html), set backend URL to:

http://localhost:5678/webhook/<your-webhook-id>


5. Type a prompt and click Generate Code.

🔍 Notes & Limitations

Gemini sometimes wraps outputs in <iframe> or includes <html>/<body> tags.

For this prototype, the raw output is returned directly.

A future improvement would add a cleaning step in n8n to strip wrappers and return pure HTML/CSS.

🚀 Future Improvements

Add cleaning/post-processing node to always return clean snippets.

Deploy n8n to a cloud host (Render/Railway) for a persistent public backend.

Support JavaScript generation and live preview inside frontend.

Store past generations and allow users to copy/share code snippets.

📞 Contact

Keerthi Raj
Email: keerthirajprofessional@gmail.com
