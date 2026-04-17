# Glassmorphic UI Design — Crontab UI

**Date:** 2026-04-17
**Scope:** Visual reskin of the existing Bootstrap 3 / EJS frontend

---

## Overview

Apply a glassmorphic visual theme to the Crontab UI web interface. The background becomes a static Aurora gradient (teal-green-blue). All panels, the navbar, table, and modals become subtle glass surfaces. No structural changes to templates — implementation is a single CSS override file.

---

## Background

**Style:** Static linear gradient
**Colors:** `linear-gradient(135deg, #0d1b2a 0%, #1b4332 45%, #0a3255 100%)`
**Coverage:** Fixed full-viewport, no repeat
**Animation:** None

Applied to `body` via CSS override.

---

## Glass Surface

A single reusable glass treatment applied to all surface elements (navbar, panels, table, modals):

| Property | Value |
|---|---|
| `background` | `rgba(255,255,255,0.06)` |
| `backdrop-filter` | `blur(8px)` |
| `border` | `1px solid rgba(255,255,255,0.12)` |
| `border-radius` | `14px` |
| `box-shadow` | `0 2px 12px rgba(0,0,0,0.2)` |

---

## Components

### Navbar (`.navbar`)
- Glass surface treatment
- Brand text color: `#5eead4` (teal)
- Link colors: `rgba(255,255,255,0.6)` → `#5eead4` on hover
- Remove Bootstrap's grey background and border-bottom; replace with glass border

### Environment Variables Panel
- Wrap in glass surface (`.glass` class or target `.form-group` containing `#env_vars`)
- Textarea: `background: rgba(0,0,0,0.25)`, dark border, light text
- Focus ring: teal `rgba(20,184,166,0.4)`

### Action Buttons

Override Bootstrap `.btn-*` classes with glassmorphic variants:

| Class | Background | Border | Text |
|---|---|---|---|
| `.btn-primary` | `rgba(20,184,166,0.15)` | `rgba(20,184,166,0.35)` | `#5eead4` |
| `.btn-info` | `rgba(56,189,248,0.1)` | `rgba(56,189,248,0.3)` | `#7dd3fc` |
| `.btn-warning` | `rgba(251,191,36,0.1)` | `rgba(251,191,36,0.3)` | `#fde68a` |
| `.btn-success` | `rgba(52,211,153,0.1)` | `rgba(52,211,153,0.3)` | `#6ee7b7` |
| `.btn-danger` | `rgba(239,68,68,0.1)` | `rgba(239,68,68,0.3)` | `#fca5a5` |
| `.btn-default` | `rgba(255,255,255,0.08)` | `rgba(255,255,255,0.15)` | `#cbd5e1` |

All buttons: `border-radius: 8px`, transparent `background-image` (remove Bootstrap gradient).

### Table (`#main_table`)
- Container gets glass surface treatment
- Remove `.table-striped` zebra pattern; replace with `rgba(255,255,255,0.04)` on hover
- Header cells: `color: #64748b`, uppercase, `border-bottom: 1px solid rgba(255,255,255,0.08)`
- Row dividers: `border-bottom: 1px solid rgba(255,255,255,0.05)`
- Stopped-row highlight: replace `background:#3A6DA6;color:#fff` with `opacity: 0.5` (dimming)
- DataTables search/pagination controls: dark inputs matching the textarea style, text `#cbd5e1`

### Modals (`.modal-content`)
- Glass surface treatment
- `.modal-header`, `.modal-footer`: `border-color: rgba(255,255,255,0.08)`
- `.modal-title`: `color: #f1f5f9`
- Form inputs inside modals: same dark input style as env textarea

### Body Text & Labels
- `body`: `color: #e2e8f0`
- `h2`, `h3`: `color: #f8fafc`
- Labels: `color: #94a3b8`

---

## Implementation Approach

**Approach A — CSS override file only.**

1. Create `public/css/glass.css` with all overrides
2. Add `<link rel="stylesheet" href="css/glass.css" />` to `views/index.ejs` after the existing Bootstrap stylesheet links
3. No other file changes required

Bootstrap JS (modals, dropdowns, DataTables) remains fully intact. All existing HTML structure, IDs, and data attributes are preserved.

---

## Files Changed

| File | Change |
|---|---|
| `public/css/glass.css` | **New** — full override stylesheet |
| `views/index.ejs` | Add one `<link>` tag |

---

## Out of Scope

- `views/restore.ejs` — separate page, can be styled in a follow-up
- Animated backgrounds
- Dark/light mode toggle
- Any changes to `app.js`, `routes.js`, or server-side code
