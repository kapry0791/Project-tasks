# ✦ Project Tasks

A clean, fully functional task manager with real-time Supabase backend, built as part of an internship assignment.

**Live Demo:** [Replace with your Netlify link after deployment]  
**Repository:** [Replace with your GitHub link]

---

## Tech Stack

| Layer       | Technology |
|-------------|-----------|
| Frontend    | HTML5, CSS3, Vanilla JavaScript |
| Backend     | [Supabase](https://supabase.com) (PostgreSQL + REST API) |
| Hosting     | [Netlify](https://netlify.com) |
| Fonts       | Google Fonts (DM Serif Display + DM Sans) |

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

## Setup Steps

### 1. Create a Supabase Project

1. Go to [supabase.com](https://supabase.com) and create a free account
2. Click **New Project** → give it a name → click **Create**
3. Wait about 1 minute for the project to provision

### 2. Create the Database Table

1. In Supabase, click **SQL Editor** in the left sidebar
2. Paste this SQL and click **Run**:

```sql
create table tasks (
  id          uuid default gen_random_uuid() primary key,
  text        text        not null,
  priority    text        not null default 'medium',
  completed   boolean     not null default false,
  created_at  timestamptz not null default now()
);

-- Allow anonymous read and write (fine for a demo project)
alter table tasks enable row level security;

create policy "Allow all" on tasks
  for all using (true) with check (true);
```

### 3. Get Your API Keys

1. In Supabase, go to **Settings → API**
2. Copy:
   - **Project URL** (e.g. `https://abcxyz.supabase.co`)
   - **anon / public key** (long string starting with `eyJ`)

### 4. Add Keys to app.js

Open `app.js` and replace lines 11–12:

```js
const SUPABASE_URL      = "https://YOUR-PROJECT.supabase.co";
const SUPABASE_ANON_KEY = "eyJ...your-anon-key...";
```

### 5. Test Locally

Open `index.html` in any browser. Tasks you add should appear in the Supabase **Table Editor** under the `tasks` table in real time.

### 6. Deploy to Netlify

1. Push your project to GitHub (see section below)
2. Go to [netlify.com](https://netlify.com) → **Add new site → Import from Git**
3. Connect your GitHub repo
4. Leave all build settings blank (this is a plain HTML/JS project)
5. Click **Deploy site**
6. Netlify gives you a live URL like `https://your-app.netlify.app`

---

## Pushing to GitHub

```bash
# First time setup (run in your project folder)
git init
git add .
git commit -m "Initial commit: Project Tasks app"

# Create a new repo at github.com, then:
git remote add origin https://github.com/YOUR-USERNAME/project-tasks.git
git branch -M main
git push -u origin main
```

---

## Where AI Tools Were Used

| What | How AI helped |
|------|--------------|
| **HTML structure** | Claude.ai generated the full semantic HTML layout with header, stats bar, form, filter row, and task list |
| **CSS design** | Claude.ai designed the entire stylesheet — color palette (cream/ink/gold), typography pairing (DM Serif + DM Sans), responsive grid, animations (slideIn, popIn), progress ring |
| **JavaScript / Supabase** | Claude.ai wrote all CRUD functions — `addTask`, `loadTasks`, `toggleTask`, `deleteTask`, `clearCompleted` — with detailed comments explaining every Supabase API call |
| **SQL schema** | Claude.ai wrote the `CREATE TABLE` statement and Row Level Security policy |
| **README** | This file was generated and structured by Claude.ai |
| **Debugging** | Claude.ai explained how Supabase `.select()`, `.insert()`, `.update()`, `.delete()`, `.eq()`, and `.in()` work, and why `.single()` is needed after `.insert().select()` |

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
