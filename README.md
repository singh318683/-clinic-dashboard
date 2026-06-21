Riverside Family Clinic — dashboard
Single-file static app. No build step, no dependencies to install.
Deploy to Vercel (same flow as your other static projects)
Push `index.html` to the root of a GitHub repo (e.g. `singh318683/clinic-dashboard`).
In Vercel, Add New → Project → Import that repo.
Framework preset: Other (framework-less static). Leave build command and output directory blank.
Deploy — Vercel will serve `index.html` directly.
What's inside
Doctor view and assistant view, toggled at the top. Three doctors with seeded demo appointments, queue actions (check in, call next patient, mark complete, mark no-show), and an "add appointment" form for walk-ins or future bookings. State is in-memory only — it resets on page reload. Let me know if you want it wired to Vercel KV, Supabase, or another store so the queue persists across reloads and across doctors/assistants viewing from different devices.
