<!-- EduNexus Master Specification – Books 1, 2, 3 -->
<!-- Floating Search Bar + Dark/Light Mode + Animations + Icons + Typography -->

<style>
  /* ─── CSS VARIABLES (Light & Dark) ─── */
  :root {
    --bg-page: #F8FAFC;
    --bg-surface: #FFFFFF;
    --bg-subtle: #F1F5F9;
    --text-primary: #0F172A;
    --text-secondary: #475569;
    --text-tertiary: #94A3B8;
    --border-default: #E2E8F0;
    --brand-default: #2563EB;
    --brand-hover: #1D4ED8;
    --shadow-md: 0 4px 6px rgba(0,0,0,0.07);
    --shadow-lg: 0 10px 15px rgba(0,0,0,0.1);
    --radius-lg: 6px;
    --duration-normal: 200ms;
    --font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  }
  [data-theme="dark"] {
    --bg-page: #020617;
    --bg-surface: #1E293B;
    --bg-subtle: #0F172A;
    --text-primary: #F8FAFC;
    --text-secondary: #94A3B8;
    --text-tertiary: #64748B;
    --border-default: #334155;
    --brand-default: #60A5FA;
    --brand-hover: #3B82F6;
    --shadow-md: 0 4px 6px rgba(0,0,0,0.5);
    --shadow-lg: 0 10px 15px rgba(0,0,0,0.5);
  }

  /* ─── GLOBAL STYLES ─── */
  body {
    font-family: var(--font-family);
    background: var(--bg-page);
    color: var(--text-primary);
    transition: background var(--duration-normal) ease, color var(--duration-normal) ease;
    margin: 0;
    padding: 0;
    line-height: 1.6;
  }
  .container {
    max-width: 1024px;
    margin: 0 auto;
    padding: 2rem 1.5rem;
  }

  /* ─── FLOATING SEARCH BAR ─── */
  #search-wrapper {
    position: sticky;
    top: 1rem;
    z-index: 1000;
    display: flex;
    justify-content: center;
    pointer-events: none;
    margin-bottom: 2rem;
  }
  #search-bar {
    pointer-events: auto;
    width: 100%;
    max-width: 640px;
    background: var(--bg-surface);
    border: 1px solid var(--border-default);
    border-radius: 50px;
    padding: 0.6rem 1.2rem 0.6rem 2.8rem;
    font-size: 1rem;
    color: var(--text-primary);
    box-shadow: var(--shadow-lg);
    transition: all var(--duration-normal) ease;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 24 24' fill='none' stroke='%2394A3B8' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Ccircle cx='11' cy='11' r='8'/%3E%3Cline x1='21' y1='21' x2='16.65' y2='16.65'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: 1rem center;
    background-size: 1.2rem;
  }
  #search-bar:focus {
    outline: none;
    border-color: var(--brand-default);
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.2);
  }

  /* ─── THEME TOGGLE ─── */
  #theme-toggle {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    z-index: 999;
    width: 48px;
    height: 48px;
    border-radius: 50%;
    background: var(--bg-surface);
    border: 1px solid var(--border-default);
    box-shadow: var(--shadow-lg);
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.5rem;
    transition: transform var(--duration-normal) ease;
  }
  #theme-toggle:hover {
    transform: scale(1.05);
  }

  /* ─── TYPOGRAPHY ─── */
  h1, h2, h3, h4, h5, h6 {
    font-weight: 600;
    letter-spacing: -0.02em;
    margin-top: 2rem;
    margin-bottom: 0.8rem;
  }
  h1 { font-size: 2.5rem; }
  h2 { font-size: 2rem; border-bottom: 2px solid var(--border-default); padding-bottom: 0.3rem; }
  h3 { font-size: 1.5rem; color: var(--text-secondary); }
  p { margin: 1rem 0; }
  a { color: var(--brand-default); text-decoration: none; transition: color var(--duration-normal) ease; }
  a:hover { color: var(--brand-hover); text-decoration: underline; }

  /* ─── TABLES ─── */
  table {
    width: 100%;
    border-collapse: collapse;
    margin: 1.5rem 0;
    background: var(--bg-surface);
    border-radius: var(--radius-lg);
    overflow: hidden;
    box-shadow: var(--shadow-md);
  }
  th, td {
    padding: 0.75rem 1rem;
    text-align: left;
    border-bottom: 1px solid var(--border-default);
  }
  th {
    background: var(--bg-subtle);
    font-weight: 600;
    color: var(--text-secondary);
  }
  tr:hover { background: var(--bg-subtle); transition: background 100ms ease; }

  /* ─── CARDS ─── */
  .card {
    background: var(--bg-surface);
    border: 1px solid var(--border-default);
    border-radius: var(--radius-lg);
    padding: 1.5rem;
    margin: 1.5rem 0;
    box-shadow: var(--shadow-md);
    transition: box-shadow var(--duration-normal) ease, transform var(--duration-normal) ease;
  }
  .card:hover {
    box-shadow: var(--shadow-lg);
    transform: translateY(-2px);
  }

  /* ─── BADGES & LABELS ─── */
  .badge {
    display: inline-block;
    padding: 0.2rem 0.6rem;
    border-radius: 9999px;
    font-size: 0.75rem;
    font-weight: 500;
    background: var(--bg-subtle);
    color: var(--text-secondary);
    border: 1px solid var(--border-default);
  }
  .badge-blue { background: #DBEAFE; color: #1D4ED8; border-color: #93C5FD; }
  .badge-green { background: #DCFCE7; color: #15803D; border-color: #86EFAC; }
  .badge-red { background: #FECDD3; color: #BE123C; border-color: #FDA4AF; }
  .badge-amber { background: #FEF3C7; color: #B45309; border-color: #FCD34D; }
  .badge-purple { background: #F3E8FF; color: #7E22CE; border-color: #D8B4FE; }

  /* ─── CODE BLOCKS ─── */
  pre {
    background: var(--bg-subtle);
    padding: 1rem;
    border-radius: var(--radius-lg);
    overflow-x: auto;
    border: 1px solid var(--border-default);
  }
  code {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.9rem;
    background: var(--bg-subtle);
    padding: 0.1rem 0.4rem;
    border-radius: 4px;
  }

  /* ─── ICONS (inline) ─── */
  .icon { font-size: 1.2rem; vertical-align: middle; margin-right: 0.3rem; }

  /* ─── ANIMATIONS ─── */
  @keyframes fadeSlideIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .section-animate {
    animation: fadeSlideIn 0.4s ease-out both;
  }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 768px) {
    .container { padding: 1rem; }
    h1 { font-size: 2rem; }
    #search-bar { max-width: 100%; }
  }

  /* ─── PRINT STYLES ─── */
  @media print {
    #search-wrapper, #theme-toggle { display: none; }
    body { background: white !important; color: black !important; }
    .card { box-shadow: none; border: 1px solid #ddd; }
  }
</style>

<!-- ─── FLOATING SEARCH BAR ─── -->
<div id="search-wrapper">
  <input id="search-bar" type="text" placeholder="Search in EduNexus spec..." aria-label="Search documentation">
</div>

<!-- ─── THEME TOGGLE ─── -->
<button id="theme-toggle" aria-label="Toggle theme">🌙</button>

<!-- ─── CONTENT ─── -->
<div class="container">

# 🎓 EduNexus Master Specification  
## Books 1 · 2 · 3 – Product, Design System, UI Library

> **Status:** ✅ Complete | **Version:** v1.0 | **Last updated:** 2026‑07‑15

---

## 📖 Book 1: Product Requirements

### 🔹 Current Status

| ✅ Vision defined | ✅ Architecture planned |
| ✅ Tech stack chosen | ✅ Design philosophy agreed |
| ❌ Nothing actually built yet |

---

### 🔹 What We'll Build – In Order

| Phase | Book | Description |
|-------|------|-------------|
| 1 | Book 1 | Product Requirements |
| 2 | Book 2 | Design System |
| 3 | Book 3 | UI Kit (180+ components) |
| 4 | Book 4 | Master Templates |
| 5 | Book 5 | Screen Specifications |
| 6 | Book 6 | Entity Specifications |
| 7 | Book 7 | Database Design |
| 8 | Book 8 | API Specification |
| 9 | Book 9 | Backend Architecture |
| 10 | Book 10 | Frontend Architecture |

**The Rule:** We don't move to the next phase until the current one is complete.

---

### 🔹 Section 3: User Roles & Personas

#### 3.1 Default System Roles

| Role | Description |
|------|-------------|
| **Super Admin** | Platform owner. Full access. Manages all institutes. |
| **Admin** | Institute manager. Manages teachers, students, batches, content. |
| **Teacher** | Creates lessons, tests, assignments. Manages assigned batches. |
| **Batch Head** | Senior teacher leading a specific batch. |
| **Class Representative** | Student with limited management powers inside their batch. |
| **Student** | Learns, takes tests, submits assignments, tracks progress. |
| **Parent (v2)** | Views child's progress and attendance. |

#### 3.2 Multi‑Role System
One account, multiple roles. Clean switching.  
`Login → Role Selector → Dashboard changes based on active role`

---

### 🔹 Section 4: Core Modules
