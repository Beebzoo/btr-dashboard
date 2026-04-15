# BTR Projects — Maastricht Science Programme

The Bachelor Thesis Research project hub for the Maastricht Science Programme.

This repo is a small static website with three public pages and one data file:

| File | Purpose |
|---|---|
| `index.html` | Landing page with two big choice cards (Supervisors / Students) |
| `submit.html` | Supervisor submission form. Submissions go via Formspree → email |
| `projects.html` | Student-facing catalog with filters and modal popups |
| `projects-data.js` | **The only file you need to edit** to add new projects |
| `README.md` | This file — admin guide |

---

## How to add a new project to the catalog

When a supervisor submits a new project (you'll get an email from Formspree), follow these steps to add it to the student-facing catalog:

### Step 1 — Open `projects-data.js` on GitHub

Go to the repo on GitHub, click on `projects-data.js`, then click the pencil icon (✏️) in the top-right to edit it in the browser.

### Step 2 — Find the end of the projects list

Scroll to the bottom of the file. You'll see the closing `];` of the array. New projects go just **before** that closing bracket.

### Step 3 — Copy the template below and paste it in

Add a comma after the previous project's closing `}` and paste the template. Fill in the fields based on the supervisor's submission email.

### Step 4 — Commit the change

Scroll to the bottom of the GitHub edit page, write a short commit message like `Add project: [title]` and click **Commit changes**. The catalog updates immediately.

---

## Project template

Copy this and paste it as a new entry. Fields marked **required** must be filled in. Optional fields can be deleted if you don't have the info.

```js
  {
    title: "Project title here",                          // required
    supervisor: "Dr. First Last",                         // required
    institution: "Department / Institute name",           // required
    location: "Maastricht",                               // required (city or campus)
    email: "first.last@maastrichtuniversity.nl",          // required
    disciplines: ["Chemistry", "Biotechnology"],          // required - one or more, see list below
    types: ["Lab"],                                       // required - one or more, see list below
    description: "One or two sentences summarising the project.",  // required
    background: "Optional longer paragraph with context.",         // optional
    details: [                                            // optional - bullet points
      "First task or sub-topic",
      "Second task or sub-topic"
    ],
    methods: "Methods, techniques, software used",        // optional
    recommended: "Recommended background or courses",     // optional
    note: "Any extra note (e.g. interview required)",     // optional
    dateAdded: "2026-04"                                  // required - YYYY-MM format
  },
```

> **Important:** Don't forget the comma at the end of the closing `}` if there's another project after it. JavaScript will break if commas are missing or strings aren't closed properly. If something looks broken, check that all `"quotes"` are paired up and every line ends with a `,`.

---

## Allowed values

### Disciplines

Use one or more of these exact strings inside the `disciplines` array. The catalog filter shows them in this order. If you need a new one, add it to the `DISCIPLINES` list inside `projects.html` as well.

- `Bioinformatics`
- `Biomedical Sciences`
- `Biotechnology`
- `Chemistry`
- `Ecology & Fieldwork`
- `Materials Science`
- `Neuroscience`
- `Physics`
- `Sustainability`
- `Other`

### Project types

Use one or more of these exact strings inside the `types` array.

| Type | Use when… |
|---|---|
| `Lab` | Wet-lab work, fieldwork, sample collection, experimental protocols |
| `Data Analysis` | Analysing experimental, clinical, omics or literature-derived datasets |
| `Simulation` | Running simulations of systems (agent-based, MD, Petri nets, etc.) |
| `Modelling` | Building mathematical, computational or conceptual models |

---

## Field-by-field reference

| Field | What it is | Required? |
|---|---|---|
| `title` | Short project title shown on the card | Yes |
| `supervisor` | Full name(s). Multiple → separate with `&` or `,` | Yes |
| `institution` | Department, institute, or company | Yes |
| `location` | City or campus where the work happens | Yes |
| `email` | Contact email students should use | Yes |
| `disciplines` | Array of one or more disciplines from the list above | Yes |
| `types` | Array of one or more project types from the list above | Yes |
| `description` | 1–2 sentence summary shown on the card | Yes |
| `dateAdded` | Year-month in `YYYY-MM` format. Used to show project age | Yes |
| `background` | Longer paragraph with scientific context | No |
| `details` | Array of bullet points (sub-topics, tasks, etc.) | No |
| `methods` | Methods, techniques, equipment or software | No |
| `recommended` | Recommended background or prerequisite courses | No |
| `note` | Any extra note (e.g. "interview required") | No |

---

## Removing or updating an old project

- To **edit** a project, find its block in `projects-data.js` and change the values, then commit.
- To **remove** a project, delete the entire block from the opening `{` to the closing `},` and commit. Make sure no orphaned commas are left behind.

---

## Yearly refresh of supervisors

Once a year, send an email to all supervisors in the catalog asking whether their project is still on offer. Use the `email` field of every project as the recipient list. Remove any projects whose supervisors don't respond, or whose `dateAdded` is older than ~2 years.

---

## Where the supervisor form sends submissions

The form on `submit.html` POSTs to a Formspree endpoint (`mreoryay`) which forwards each submission as an email to `msp-btr@maastrichtuniversity.nl`. To change the destination email, log into the Formspree dashboard for that endpoint and update the recipient there — no code change needed.
