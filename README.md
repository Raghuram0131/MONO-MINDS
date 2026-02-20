Here is a comprehensive project plan for **CodeRefine**, tailored for your team of four (MONO MINDS) and updated to match your specific technology requests: **HTML/JS (Frontend), Groq API (AI Backend), Database, and Firebase (Authentication)**.

### Technology Stack Alignment

Based on your instructions, we are pivoting slightly from the original architecture to make it incredibly fast to build and deploy:

* **Frontend:** Vanilla HTML, CSS (Tailwind via CDN for rapid styling), and Vanilla JavaScript.
* **Authentication:** Google Firebase Auth (Email/Password & Google Sign-in).
* **Database:** Firebase Firestore (simplifies the stack since you are already using Firebase, eliminating the need for a separate PostgreSQL/MongoDB instance).
* **AI Backend:** Groq API (using blazing-fast open-source models like LLaMA 3) hosted on Vercel Serverless Functions (to keep your Groq API key secure).
* **Deployment:** Vercel.

---

### Team Distribution (Team Size: 4)

To maximize efficiency, assign specific ownership to your team members:

* **Member 1: Frontend & UI/UX Developer:** Focuses on the HTML, Tailwind CSS styling, and making the dashboard responsive and intuitive.
* **Member 2: Auth & Database Engineer:** Handles Firebase setup, user authentication flows, and saving/retrieving review history in Firestore.
* **Member 3: AI Prompt & Backend Integration:** Writes the system prompts for Groq, handles the Vercel serverless function (Node.js) to connect the frontend to Groq, and parses the AI's response.
* **Member 4: QA & Project Manager:** Ensures the code snippets display correctly (using syntax highlighters), tests for bugs, manages version control (GitHub), and handles the Vercel deployment.

---

### Project Execution Plan

#### Phase 1: Setup & Scaffolding (Days 1-2)

* Set up a GitHub repository and invite all 4 members.
* Create a basic HTML template (`index.html`, `dashboard.html`) and link Tailwind CSS via CDN.
* Set up a Firebase project, register a web app, and enable Authentication and Firestore Database.
* Get a Groq API key and set up a basic Vercel project structure (`/public` for HTML, `/api` for serverless functions).

#### Phase 2: Core Features & Authentication (Days 3-5)

* **Auth:** Implement Firebase Auth on the `index.html` page so users can log in. Redirect successful logins to `dashboard.html`.
* **UI:** Build the main dashboard UI. It needs a large text area (or code editor integration like CodeMirror/Monaco) for input, a language selector, and an "Analyze Code" button.
* **Output UI:** Create placeholders for the AI's response (Tabs for: Bugs Found, Security Issues, Optimized Code, Explanation).

#### Phase 3: AI Engine Integration (Days 6-8)

* Create a Vercel Serverless Function (`/api/analyze.js`) that takes code from the frontend, constructs a prompt, and securely calls the Groq API.
* Instruct the Groq model to return data in a structured JSON format so it can be easily displayed on the frontend.
* Connect the frontend "Analyze Code" button to fetch data from this `/api/analyze` endpoint.

#### Phase 4: Database & History (Days 9-10)

* Once the AI returns a review, save the original code, the AI's response, and a timestamp to Firebase Firestore under the current user's ID.
* Build a sidebar or history page where users can view their past code reviews.

#### Phase 5: Polish & Deployment (Days 11-14)

* Integrate a syntax highlighter (like Prism.js or Highlight.js) so the AI's generated code looks good.
* Deploy the final code to Vercel (Vercel will automatically host the `public` HTML folder and the `/api` backend folder).
* Conduct testing to ensure the Groq API handles various programming languages properly.

---

### The Prompt for AI Code Generators (Antigravity / v0 / Bolt / Claude)

Copy and paste the detailed prompt below into your AI coding tool (like Antigravity, Cursor, v0, etc.) to generate the foundational codebase for CodeRefine.

**Master Prompt:**

> "I need to build a web application called 'CodeRefine', a Generative AI-powered code review and optimization engine. The app must be built using Vanilla HTML, Tailwind CSS (via CDN), and Vanilla JavaScript for easy deployment on Vercel.
> **Tech Stack constraints:**
> * Frontend: HTML, Tailwind CSS, JavaScript. Include Prism.js or Highlight.js via CDN for syntax highlighting.
> * Authentication: Google Firebase Auth (Web modular API).
> * Database: Firebase Firestore (Web modular API).
> * Backend/AI: A Vercel Serverless function (`/api/analyze.js`) that connects to the Groq API.
> 
> 
> **Please generate the following files:**
> 1. `index.html`: A clean, modern landing page explaining what CodeRefine is (Detects bugs, optimizes code, multi-language support). Include Firebase Authentication UI (Login / Sign in with Google).
> 2. `dashboard.html`: The main user interface. It should have:
> * A sidebar showing "Recent Reviews" (fetched from Firestore).
> * A main panel with a dropdown to select programming language (Python, JavaScript, Java, C++, etc.).
> * A large textarea or CodeMirror integration for the user to paste their source code.
> * An "Analyze Code" button.
> * A results section with tabs or distinct cards for: 'Syntax & Logical Errors', 'Security Vulnerabilities', 'Performance Optimization Suggestions', and 'Refactored Code'.
> 
> 
> 3. `app.js`: The frontend logic handling:
> * Firebase Auth state changes (protecting the dashboard).
> * Capturing the code input, sending it to the `/api/analyze` endpoint.
> * Displaying a loading state while waiting for the AI.
> * Parsing the AI response and rendering it into the results section with syntax highlighting.
> * Saving the review data to Firestore once generated.
> 
> 
> 4. `api/analyze.js`: A Node.js Vercel serverless function that:
> * Accepts a POST request with the user's source code and language.
> * Uses the Groq API SDK (with the model `llama3-70b-8192` or similar) to analyze the code.
> * Uses a system prompt instructing the AI to act as an expert senior developer and output the response in strictly formatted JSON containing arrays for `bugs`, `security`, `optimizations`, and a string for `refactoredCode`.
> * Returns this JSON to the frontend.
> 
> 
> 
> 
> Please provide the complete, ready-to-run code for these files, ensuring best practices for UI/UX and commenting where I need to insert my Firebase configuration and Groq API keys."

---

Would you like me to help you draft the specific system prompt that will run inside the backend to tell the Groq AI exactly how to review the code?
