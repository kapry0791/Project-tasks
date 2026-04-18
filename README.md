# ✦ Project Tasks

A clean, fully functional task manager with a real-time Supabase backend, built as part of an internship assignment, hosted using Netlify and code imported using Git.

Live Demo: https://kissanth18.netlify.app/ 
Repository: https://github.com/kapry0791/Project-tasks

---

## Tech Stack

| Layer       | Technology |
|-------------|-----------|
| Frontend    | HTML5, CSS3, JavaScript |
| Backend     | [Supabase](https://supabase.com) (PostgreSQL + REST API) |
| Hosting     | [Netlify](https://netlify.com) |


---

## Features

- Add tasks with a priority level (Low / Medium / High)
- Mark tasks as completed or pending (checkbox toggle)
- Edit task text and priority via a modal popup
- Delete individual tasks
- Bulk-clear all completed tasks
- Filter view: All / Pending / Completed
- Live stats bar: total, pending, done count + progress ring
- Toast notifications for every action
- Fully connected to Supabase — all data persists after refresh

---

#How I Built It

1. Started with the basics
I began by setting up three core files — index.html, style.css, and app.js. The initial focus was on building a simple, functional UI with an input field, a task list, and filter buttons (All / Pending / Completed).

2. Implemented core functionality
Next, I added interactivity using JavaScript. Users can add, complete, and delete tasks. The filtering logic was the most challenging part, as it required dynamically updating the visible tasks without reloading the page.

3. Integrated Supabase for persistence
To move beyond in-memory storage, I connected the app to Supabase. Using async/await, I implemented CRUD operations (fetch, insert, update, delete) with a PostgreSQL database. This ensured that tasks are stored persistently.

4. Added an activity log
I created a separate activity_log table to track all user actions — ADDED, COMPLETED, UNCOMPLETED, and DELETED — along with timestamps. Each interaction is automatically recorded, providing a clear audit trail.

5. Deployed with GitHub and Netlify
Finally, I pushed the project to GitHub and connected the repository to Netlify. This setup enables continuous deployment, so every push to the main branch automatically updates the live site.

git init
git add.
git commit -m "Initial commit — Project Tasks."
git remote add origin https://github.com/kapry0791/Project-tasks.git
git branch -M main
git push -u origin main

---

## Where AI Tools Were Used

GitHub Copilot — Had this running in VS Code. It auto-completed a lot of the repetitive JavaScript (like the fetch functions), which saved a lot of time.

ChatGPT (OpenAI) — Used this to ask questions like "what does async/await actually do? What is Supabase Row Level Security, and do I need it? And why is my Netlify deploy failing? — good for quick concept explanations and debugging help.

---

## File Structure

```
project-tasks/
├── index.html   ← Page structure (header, form, task list, modal)
├── style.css    ← All styling and animations
├── app.js       ← All JavaScript logic + Supabase calls
└── README.md    ← This file
```

---

## Database Schema

```
tasks
├── id          UUID       Primary key, auto-generated
├── text        TEXT       The task description
├── priority    TEXT       "low" | "medium" | "high"
├── completed   BOOLEAN    false = pending, true = done
└── created_at  TIMESTAMP  Auto-set on insert
```

<div align="center">

Built by Kishore B &nbsp;·&nbsp; HTML + CSS + JS + Supabase + Netlify

</div>

