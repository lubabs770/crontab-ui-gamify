# Glassmorphic UI Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Apply a glassmorphic visual skin (Aurora static gradient background, subtle frosted glass surfaces) to the Crontab UI frontend.

**Architecture:** A single new CSS file (`public/css/glass.css`) overrides Bootstrap 3 defaults. One `<link>` tag added to `views/index.ejs` loads it after Bootstrap. The stopped-row inline style in `index.ejs` is replaced with a class to allow clean CSS targeting.

**Tech Stack:** Plain CSS3, Bootstrap 3 override pattern, EJS templates, Node.js (`npm start` runs the app on port 8000 by default)

---

## File Map

| File | Action | Purpose |
|---|---|---|
| `public/css/glass.css` | **Create** | Full glassmorphic override stylesheet |
| `views/index.ejs` | **Modify** | Add `<link>` tag; swap stopped-row inline style for class |

---

## Task 1: Body background & navbar glass

**Files:**
- Create: `public/css/glass.css`

- [ ] **Step 1: Create `public/css/glass.css` with body and navbar styles**

```css
/* ── BASE ── */
body {
  background: linear-gradient(135deg, #0d1b2a 0%, #1b4332 45%, #0a3255 100%);
  background-attachment: fixed;
  color: #e2e8f0;
  min-height: 100vh;
}

h2, h3, h4 {
  color: #f8fafc;
}

/* ── NAVBAR ── */
.navbar-default {
  background: rgba(255, 255, 255, 0.06);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.12);
  border-top: none;
  border-left: none;
  border-right: none;
  border-radius: 0;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.2);
}

.navbar-default .navbar-brand {
  color: #5eead4;
  font-weight: 700;
}
.navbar-default .navbar-brand:hover,
.navbar-default .navbar-brand:focus {
  color: #2dd4bf;
  background: transparent;
}

.navbar-default .navbar-nav > li > a {
  color: rgba(255, 255, 255, 0.6);
}
.navbar-default .navbar-nav > li > a:hover,
.navbar-default .navbar-nav > li > a:focus {
  color: #5eead4;
  background: transparent;
}

.navbar-default .navbar-nav > .open > a,
.navbar-default .navbar-nav > .open > a:hover,
.navbar-default .navbar-nav > .open > a:focus {
  background: rgba(255, 255, 255, 0.08);
  color: #5eead4;
}

.navbar-default .navbar-toggle {
  border-color: rgba(255, 255, 255, 0.2);
}
.navbar-default .navbar-toggle .icon-bar {
  background: rgba(255, 255, 255, 0.6);
}
.navbar-default .navbar-toggle:hover,
.navbar-default .navbar-toggle:focus {
  background: rgba(255, 255, 255, 0.08);
}

/* ── DROPDOWN ── */
.dropdown-menu {
  background: rgba(10, 22, 38, 0.92);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 10px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
}
.dropdown-menu > li > a {
  color: rgba(255, 255, 255, 0.75);
}
.dropdown-menu > li > a:hover,
.dropdown-menu > li > a:focus {
  background: rgba(255, 255, 255, 0.08);
  color: #5eead4;
}
.dropdown-menu .divider {
  background: rgba(255, 255, 255, 0.08);
}
```

- [ ] **Step 2: Start the app and verify visually**

```bash
cd /path/to/crontab-ui-gamify
npm start
```

Open `http://localhost:8000` in browser.

Expected: dark Aurora gradient background, glass navbar with teal brand text. Bootstrap CSS is not yet linked to this file — that comes in Task 5.

> Note: the stylesheet isn't linked yet so you won't see changes until Task 5. This step just confirms the app starts without errors.

- [ ] **Step 3: Commit**

```bash
git add public/css/glass.css
git commit -m "feat: add glass.css with body gradient and navbar overrides"
```

---

## Task 2: Button overrides

**Files:**
- Modify: `public/css/glass.css`

- [ ] **Step 1: Append button styles to `public/css/glass.css`**

```css
/* ── BUTTONS ── */
.btn {
  background-image: none;
  border-radius: 8px;
  font-weight: 500;
  text-shadow: none;
  box-shadow: none;
  transition: background 0.15s ease, border-color 0.15s ease;
}
.btn:active,
.btn.active {
  box-shadow: none;
}

.btn-default {
  background: rgba(255, 255, 255, 0.08);
  border-color: rgba(255, 255, 255, 0.15);
  color: #cbd5e1;
}
.btn-default:hover,
.btn-default:focus {
  background: rgba(255, 255, 255, 0.14);
  border-color: rgba(255, 255, 255, 0.25);
  color: #f1f5f9;
}

.btn-primary {
  background: rgba(20, 184, 166, 0.15);
  border-color: rgba(20, 184, 166, 0.35);
  color: #5eead4;
}
.btn-primary:hover,
.btn-primary:focus,
.btn-primary:active,
.btn-primary.active {
  background: rgba(20, 184, 166, 0.28);
  border-color: rgba(20, 184, 166, 0.5);
  color: #5eead4;
}

.btn-info {
  background: rgba(56, 189, 248, 0.1);
  border-color: rgba(56, 189, 248, 0.3);
  color: #7dd3fc;
}
.btn-info:hover,
.btn-info:focus,
.btn-info:active,
.btn-info.active {
  background: rgba(56, 189, 248, 0.22);
  border-color: rgba(56, 189, 248, 0.45);
  color: #7dd3fc;
}

.btn-warning {
  background: rgba(251, 191, 36, 0.1);
  border-color: rgba(251, 191, 36, 0.3);
  color: #fde68a;
}
.btn-warning:hover,
.btn-warning:focus,
.btn-warning:active,
.btn-warning.active {
  background: rgba(251, 191, 36, 0.22);
  border-color: rgba(251, 191, 36, 0.45);
  color: #fde68a;
}

.btn-success {
  background: rgba(52, 211, 153, 0.1);
  border-color: rgba(52, 211, 153, 0.3);
  color: #6ee7b7;
}
.btn-success:hover,
.btn-success:focus,
.btn-success:active,
.btn-success.active {
  background: rgba(52, 211, 153, 0.22);
  border-color: rgba(52, 211, 153, 0.45);
  color: #6ee7b7;
}

.btn-danger {
  background: rgba(239, 68, 68, 0.1);
  border-color: rgba(239, 68, 68, 0.3);
  color: #fca5a5;
}
.btn-danger:hover,
.btn-danger:focus,
.btn-danger:active,
.btn-danger.active {
  background: rgba(239, 68, 68, 0.22);
  border-color: rgba(239, 68, 68, 0.45);
  color: #fca5a5;
}
```

- [ ] **Step 2: Commit**

```bash
git add public/css/glass.css
git commit -m "feat: add glassmorphic button overrides"
```

---

## Task 3: Table & panel glass

**Files:**
- Modify: `public/css/glass.css`

- [ ] **Step 1: Append table and panel styles to `public/css/glass.css`**

```css
/* ── LAYOUT ── */
.container-fluid {
  padding-top: 1.5rem;
}

/* ── ENV VARS PANEL ── */
.form-group {
  background: rgba(255, 255, 255, 0.06);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 14px;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.2);
  padding: 1.25rem;
}

label {
  color: #94a3b8;
  font-weight: 500;
}

.form-control {
  background: rgba(0, 0, 0, 0.25);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  color: #e2e8f0;
}
.form-control:focus {
  background: rgba(0, 0, 0, 0.32);
  border-color: rgba(20, 184, 166, 0.4);
  box-shadow: 0 0 0 3px rgba(20, 184, 166, 0.1);
  color: #e2e8f0;
  outline: none;
}
.form-control::-webkit-input-placeholder { color: #475569; }
.form-control::placeholder { color: #475569; }

/* ── TABLE GLASS WRAPPER ── */
/* DataTables wraps #main_table in #main_table_wrapper */
#main_table_wrapper {
  background: rgba(255, 255, 255, 0.06);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 14px;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.2);
  padding: 1rem;
  overflow: hidden;
}

/* ── TABLE STYLES ── */
.table {
  color: #cbd5e1;
  margin-bottom: 0;
}

.table > thead > tr > th {
  color: #64748b;
  font-size: 0.72rem;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  background: transparent;
  font-weight: 600;
}

.table > tbody > tr > td {
  border-top: 1px solid rgba(255, 255, 255, 0.05);
  vertical-align: middle;
}

/* Remove Bootstrap striped background */
.table-striped > tbody > tr:nth-of-type(odd) {
  background: transparent;
}

/* Hover row */
.table-hover > tbody > tr:hover {
  background: rgba(255, 255, 255, 0.04);
}

/* Stopped row (class set in index.ejs) */
tr.row-stopped > td {
  opacity: 0.5;
}
```

- [ ] **Step 2: Commit**

```bash
git add public/css/glass.css
git commit -m "feat: add glass panel, form, and table overrides"
```

---

## Task 4: Modal & DataTables overrides

**Files:**
- Modify: `public/css/glass.css`

- [ ] **Step 1: Append modal and DataTables styles to `public/css/glass.css`**

```css
/* ── MODALS ── */
.modal-content {
  background: rgba(10, 22, 38, 0.88);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 14px;
  box-shadow: 0 8px 40px rgba(0, 0, 0, 0.5);
  color: #e2e8f0;
}

.modal-header {
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.modal-footer {
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}

.modal-title {
  color: #f1f5f9;
}

.modal-content .close {
  color: rgba(255, 255, 255, 0.6);
  text-shadow: none;
  opacity: 1;
  font-weight: 400;
}
.modal-content .close:hover {
  color: #f1f5f9;
  opacity: 1;
}

/* ── DATATABLES ── */
.dataTables_wrapper .dataTables_filter label,
.dataTables_wrapper .dataTables_length label,
.dataTables_wrapper .dataTables_info {
  color: #64748b;
}

.dataTables_wrapper .dataTables_filter input,
.dataTables_wrapper .dataTables_length select {
  background: rgba(0, 0, 0, 0.25);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  color: #e2e8f0;
  padding: 0.3rem 0.65rem;
}

.dataTables_wrapper .dataTables_paginate .paginate_button {
  color: #94a3b8 !important;
  border-radius: 6px !important;
  border: 1px solid transparent !important;
}
.dataTables_wrapper .dataTables_paginate .paginate_button:hover {
  background: rgba(255, 255, 255, 0.08) !important;
  border-color: rgba(255, 255, 255, 0.12) !important;
  color: #5eead4 !important;
}
.dataTables_wrapper .dataTables_paginate .paginate_button.current,
.dataTables_wrapper .dataTables_paginate .paginate_button.current:hover {
  background: rgba(20, 184, 166, 0.15) !important;
  border-color: rgba(20, 184, 166, 0.35) !important;
  color: #5eead4 !important;
}
.dataTables_wrapper .dataTables_paginate .paginate_button.disabled,
.dataTables_wrapper .dataTables_paginate .paginate_button.disabled:hover {
  color: #334155 !important;
}
```

- [ ] **Step 2: Commit**

```bash
git add public/css/glass.css
git commit -m "feat: add modal and DataTables glassmorphic overrides"
```

---

## Task 5: Wire up stylesheet & fix stopped-row

**Files:**
- Modify: `views/index.ejs`

- [ ] **Step 1: Add the glass.css link in `views/index.ejs`**

Find this block (around line 8):

```html
<link rel="stylesheet" href="css/bootstrap.min.css" />
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.10.12/css/dataTables.bootstrap.min.css"/>
```

Replace with:

```html
<link rel="stylesheet" href="css/bootstrap.min.css" />
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.10.12/css/dataTables.bootstrap.min.css"/>
<link rel="stylesheet" href="css/glass.css" />
```

- [ ] **Step 2: Replace the stopped-row inline style in `views/index.ejs`**

Find this block (around line 42):

```ejs
<% if (!crontab.stopped) { %>
    <tr>
<% } else { %>
    <tr style="background:#3A6DA6;color:#fff">
<% } %>
```

Replace with:

```ejs
<% if (!crontab.stopped) { %>
    <tr>
<% } else { %>
    <tr class="row-stopped">
<% } %>
```

- [ ] **Step 3: Start the app and verify the full UI**

```bash
npm start
```

Open `http://localhost:8000`.

Check each of these:
- Aurora gradient fills the full viewport background
- Navbar is glass/translucent with teal "Crontab UI" brand text
- Env vars textarea sits inside a glass panel
- Action buttons (New, Backup, Import, Export, Get, Save) all have correct colored glass variants
- Cron table is wrapped in a glass panel; rows have subtle separators
- Stopped jobs appear dimmed (opacity) instead of bright blue
- Click "New" — the modal should be dark glass, form inputs dark, buttons correct colors
- DataTables search input and pagination controls are styled

- [ ] **Step 4: Commit**

```bash
git add views/index.ejs
git commit -m "feat: link glass.css and replace stopped-row inline style with class"
```

---

## Task 6: Push to GitHub

- [ ] **Step 1: Push main branch**

```bash
git push -u origin main
```

Expected: all 5 commits pushed to `https://github.com/lubabs770/crontab-ui-gamify`.
