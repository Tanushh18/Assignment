# Full-Stack Flashcard Generator (MERN)

## 📸 Application Screenshots
Below are real screenshots of the running application (not logos):

---

## 🎯 Project Overview
This repository contains a small full-stack application built for the Product Engineering Internship assignment. The app demonstrates:

- A React frontend (Create React App)
- A Node.js + Express backend that calls the OpenAI API
- Validation to ensure 15 flashcards are returned with the required difficulty distribution
- Simple Prev/Next navigation and keyboard support

---

## 📁 Repo Structure
```
Assignment/                # repo root (this README)
├─ backend/                # Express server + OpenAI logic
├─ frontend/               # React app (Create React App)
├─ Public/                 # screenshots and images used in README / UI
└─ README.md
```

---

## ✨ Screenshots
These are live screenshots of the running frontend application, stored in the Public folder.

![Screenshot 1](Public/Screenshot 2025-11-15 at 8.03.14 PM.png)
![Screenshot 2](Public/Screenshot 2025-11-15 at 8.03.18 PM.png)
![Screenshot 3](Public/Screenshot 2025-11-15 at 8.03.22 PM.png)
![Screenshot 4](Public/Screenshot 2025-11-15 at 8.03.26 PM.png)
![Screenshot 5](Public/Screenshot 2025-11-15 at 8.03.29 PM.png)

---

## 🔧 Prerequisites
- Node.js v18+ (or compatible LTS)
- npm (comes with Node)
- An OpenAI API key (or other LLM key if you modify the backend)
- Git + GitHub account (SSH key already created in your environment)

---

## 🛠️ Backend — Setup & Run (Designer steps)
Follow these commands inside the project root. These commands assume the backend folder is `backend/`.

1. Open a terminal and go to the backend folder:

```bash
cd /Users/t/Desktop/Tanush/Assignment/backend
```

2. Install dependencies:

```bash
npm install express cors dotenv openai
npm install --save-dev nodemon
```

3. Create a `.env` file in the `backend` folder and add the following (use your real OpenAI key):

```
PORT=3001
OPENAI_API_KEY=your_openai_api_key_here
ALLOWED_ORIGIN=http://localhost:3000
```

4. Ensure `package.json` scripts contain:

```json
"scripts": {
  "start": "node server.js",
  "dev": "nodemon server.js"
}
```

5. If your `server.js` uses `import` syntax, set the package type to module (run once):

```bash
npm pkg set type=module
```

6. Start the backend (development mode):

```bash
npm run dev
```

**Result:** your terminal should show `Backend listening on port 3001`.

---

## 🎨 Frontend — Setup & Run (Designer steps)
Follow these commands inside the project root. This example uses Create React App.

1. Open a new terminal and go to the frontend folder:

```bash
cd /Users/t/Desktop/Tanush/Assignment/frontend
```

2. Install dependencies and axios if needed:

```bash
npm install
npm install axios
```

3. (Optional) To avoid CORS and use relative URLs in the app, add a proxy to `frontend/package.json`:

```json
"proxy": "http://localhost:3001"
```

4. Start the frontend:

```bash
npm start
```

**Result:** the app opens at `http://localhost:3000`.

---

## 🔁 Example API Request (Backend)
You can test the backend directly with `curl` (no frontend running required):

```bash
curl -X POST http://localhost:3001/generate-flashcards \
  -H "Content-Type: application/json" \
  -d '{"topic":"Photosynthesis"}'
```

**Expected response:** a JSON array of 15 objects:

```json
[
  { "question": "...", "answer": "...", "difficulty": "easy" },
  ...14 more cards
]
```

---

## ✅ How the Flow Works
1. Frontend sends `POST /generate-flashcards` with `{ "topic": "..." }`.
2. Backend builds a precise prompt and calls the OpenAI API.
3. Backend parses and validates the model response (exactly 15 cards, difficulty distribution 5/5/5).
4. Backend returns the array to frontend.
5. Frontend shows one flashcard at a time with Prev/Next and keyboard navigation.

---

## 📦 Git: Make sure only this folder is pushed (fix accidental upload)
If you accidentally uploaded your entire Desktop or other folders, fix it locally and push only the `Assignment/` repo.

Run these commands from inside `/Users/t/Desktop/Tanush/Assignment` (single-line commands):

```bash
# set the git remote to your repo and push current branch
git remote set-url origin git@github.com:Tanushh18/Assignment.git && git add . && git commit -m "final: assignment upload" && git push origin main
```

If you need to remove files that were accidentally committed (like your whole Desktop), see these steps (careful: destructive):

```bash
# remove large or unwanted files from git history (use only if you understand implications)
git rm -r --cached path/to/unwanted_folder_or_file
git commit -m "remove unwanted files"
git push origin main
```

---

## 📁 Where to place images so README renders correctly
Put the images inside the repo at:

```
/Users/t/Desktop/Tanush/Assignment/Public/
```

Then reference them in the README as `Public/<filename.png>` — this README already uses that path.

---

## 🎯 Designer-friendly run checklist
1. Start backend: `cd backend && npm run dev` → see `Backend listening on port 3001`.
2. Start frontend: `cd frontend && npm start` → app at `http://localhost:3000`.
3. Enter a topic (e.g., "Photosynthesis") and press **Generate**.
4. Use Prev/Next buttons or ← → keys to navigate cards.

---

## 💡 Tips & Troubleshooting (quick)
- **CORS errors:** either set `ALLOWED_ORIGIN=http://localhost:3000` in backend `.env` or use the CRA proxy.
- **Import syntax errors:** run `npm pkg set type=module` in backend if you're using `import`.
- **OpenAI errors:** ensure `OPENAI_API_KEY` is valid and has quota.

---

## 🧾 Attribution & Credits
- OpenAI for LLM generation
- React & Express examples adapted for quick assignment submission

---

## ❤️ Final notes
This README is intentionally visual and designer-friendly: images are included and the run steps are presented as short, clear commands. If you want I can produce a compact single-page PDF or a short demo script you can send along with your submission.
