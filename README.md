<div align="center">

<img src="logos/logo-horizontal-dark.svg" alt="Roadmap Hub" width="290">

# Interactive Learning Roadmaps

**Structured, step-by-step developer roadmaps. Pick a learning path, study real-world examples, complete interactive challenges, and build production-ready projects.**

[![Live Demo](https://img.shields.io/badge/demo-live-34d399?style=for-the-badge)](https://samikhan43.github.io/roadmap-hub/)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue?style=for-the-badge)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=for-the-badge)](CONTRIBUTING.md)
![Hosted on GitHub Pages](https://img.shields.io/badge/hosted%20on-GitHub%20Pages-24292e?style=for-the-badge&logo=github)

[Live Demo](https://samikhan43.github.io/roadmap-hub/) · [Explore Roadmaps](#available-roadmaps) · [Quick Start](#quick-start) · [Add a New Path](#adding-a-new-roadmap) · [Contributing](#contributing)

</div>

---

## Table of Contents

- [About the Project](#about-the-project)
- [Key Features](#key-features)
- [Available Roadmaps](#available-roadmaps)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Adding a New Roadmap](#adding-a-new-roadmap)
- [Deployment Guide](#deployment-guide)
- [Tech Stack](#tech-stack)
- [Contributing](#contributing)
- [Technical Notes](#technical-notes)
- [License](#license)

---

## About the Project

Traditional learning guides are often just overwhelming walls of links. This project reimagines documentation by transforming topics into an **interactive, guided learning timeline**. Every single level features:

- A dedicated, self-contained lesson primer.
- Real-world context and architectural blueprints.
- A hands-on practice challenge with integrated hints.
- A portfolio-ready mini-project to validate your skills.

**The best part?** It is a zero-dependency, plain static site. With **no frameworks and no backend complexity**, you can open it locally, host it anywhere for free, and extend it in minutes. Learners need nothing installed. Contributors write one small JSON file per topic, and a tiny Python script turns those files into the pages.

---

## Key Features

| Feature | Description |
| :--- | :--- |
| **Dynamic Roadmap Picker** | Filter and search through available paths directly from an intuitive dashboard card system. |
| **Interactive Lesson Drawer** | Access concept overviews, multi-language syntax blueprints, and concrete, real-world analogies. |
| **Targeted Practice Challenges** | Reinforce your learning with custom problems, progressive hints, and step-by-step solutions. |
| **Milestone Level Projects** | Cap off each learning level by building an independent, portfolio-grade practical application. |
| **Local Progress Tracking** | Automatically track completed topics and modules. Progress is safely saved inside your browser storage. |
| **Contextual Theme Accents** | Enjoy a cohesive, modern dark layout where each individual path carries its own custom accent branding. |
| **Power-User Shortcuts** | Fast keyboard navigation: press `/` to search, `←` `→` to traverse topics, and `Esc` to exit drawers. |
| **Fully Responsive Layout** | Clean, responsive UI optimized fluidly for mobile devices, tablets, and ultra-wide desktops. |
| **Contributor-Friendly** | One JSON file per topic, a ready-made template, and automatic validation on every pull request. |

---

## Available Roadmaps

| Learning Path | Levels | Total Topics | Release Status |
| :--- | :---: | :---: | :--- |
| [SQL Fundamentals](https://samikhan43.github.io/roadmap-hub/sql-roadmap/) | 5 | 32 | **Production Live** |
| [PostgreSQL Roadmap](https://samikhan43.github.io/roadmap-hub/postgres-roadmap/) | 5 | 39 | **Production Live** |
| [FastAPI Roadmap](https://samikhan43.github.io/roadmap-hub/fastapi-roadmap/) | 6 | 39 | **Production Live** |
| .[Auth Roadmap](https://samikhan43.github.io/roadmap-hub/Auth-roadmap/) | 6 | 26 | **Production Live** |

> The **SQL Roadmap** covers SQL fundamentals, joins, analytical queries, indexing, transactions, and security. The **PostgreSQL Roadmap** progresses from `psql` and database architecture through schema design, performance, replication, and production operations.

## Setup Guides

The [Setup Guides page](https://samikhan43.github.io/roadmap-hub/setup-guides/) is separate from the learning roadmaps and is featured on the homepage. Guide cards open dedicated pages that render the Markdown source, including tables, links, lists, and copyable, syntax-highlighted code examples. The PostgreSQL guide's source of truth is `POSTGRESQL_GUIDE.md`.

To add another guide, add its Markdown file and one metadata entry in `setup-guides/guides.js`. The guide catalog and shared reader use this registry; no generated page or rebuild is needed.

---

## Quick Start

Viewing the roadmaps requires no compilation, package installation, or environment configuration. To load Markdown setup guides locally, use the local development server below; browsers block local-file JavaScript from fetching Markdown files when the site is opened directly as `file://`.

### 1. Clone the Repository
```bash
git clone https://github.com/samikhan43/roadmap-hub.git
cd roadmap-hub
```

### 2. Launch Local Environment
You can double-click `index.html` to open it directly in your browser. Alternatively, run a lightweight local development server:

```bash
# Using Python 3
python3 -m http.server 8000
```
Once initialized, navigate to `http://localhost:8000`.

> [!NOTE]
> An active internet connection is required to dynamically fetch utilities like Tailwind CSS and Lucide Icons from their CDNs.

---

## Project Structure

The codebase is structured to maximize simplicity and modularity:

```text
roadmap-hub/
├── index.html            # Main dashboard and Roadmap Picker
├── README.md             # Repository documentation
├── logos/                # Project logo assets
│   ├── logo-horizontal.svg
│   ├── logo-horizontal-dark.svg
│   ├── logo-mark.svg
│   └── logo-mark-512.png
├── CONTRIBUTING.md       # How to add or fix a topic
├── CODE_OF_CONDUCT.md    # Community standards
├── LICENSE               # Open-source license terms
├── sql-roadmap/
│   └── index.html        # Self-contained single-page roadmap
├── postgres-roadmap/
│   └── index.html        # PostgreSQL roadmap (5 levels, 39 topics)
├── fastapi-roadmap/
│   └── index.html        # FastAPI roadmap (6 levels, 39 topics)
├── setup-guides/
│   ├── guides.js         # Shared metadata registry for setup guides
│   ├── index.html        # Setup guide catalog
│   └── guide.html        # Shared Markdown guide reader
├── POSTGRESQL_GUIDE.md   # PostgreSQL setup guide
├── content/              # Source files for community roadmaps
│   └── <roadmap>/
│       ├── roadmap.json  # Title, levels, projects, milestones
│       └── topics/       # One JSON file per topic
├── _template/            # Starter roadmap copied by --new
├── scripts/
│   ├── build.py          # Builds <roadmap>/index.html from content/
│   └── build_roadmap.py  # Page generator
├── assets/template.html  # Shared page layout
├── docs/                 # Example roadmap file
└── .github/              # Issue forms, PR template, validation workflow
```

Each published roadmap page is self-contained in its own directory, with its content embedded in a single HTML file.

The dashboard uses `logos/logo-horizontal-dark.svg`, while roadmap pages and the browser favicon use `logos/logo-mark.svg`. Use `logos/logo-horizontal.svg` on light backgrounds, such as this README.

---

## Adding a New Roadmap

Follow these steps to expand the platform with a custom learning path:

### Step 1: Create the Roadmap From the Template
```bash
python3 scripts/build.py --new fastapi
```
This creates `content/fastapi/` with a starter `roadmap.json` and four placeholder topics. Edit `roadmap.json` (title, levels, level projects, milestones, accent colour) and the files in `topics/`. A full roadmap usually has 4 to 5 levels and 20 to 35 topics. Add more levels by adding entries to `levels`, and use the matching `"l"` number in each topic file.

### Step 2: Build Your Roadmap Page
```bash
python3 scripts/build.py fastapi
```
This writes `fastapi/index.html` (with an "All roadmaps" link back to the hub). Fix any error the script prints, then open the page to check it.

### Step 3: Register Content on the Hub Dashboard
Open the root `index.html` file, locate the global `ROADMAPS` array definition, and append your project entry metadata:

```javascript
{
  slug: "fastapi",
  title: "FastAPI Architecture",
  icon: "zap",
  rgb: "34,211,238",
  status: "live",
  levels: 5,
  topics: 28,
  desc: "Design, secure, and deploy high-performance Python APIs.",
  tags: ["Backend", "Python"]
}
```
*   Ensure the `slug` exactly matches your subdirectory name.
*   Verify the `rgb` value matches your roadmap's accent color.
*   Update the row in the [Available Roadmaps](#available-roadmaps) table.

### Step 4: Push to Source Control
Commit your updates (including the generated `fastapi/index.html`) and push to your remote branch. GitHub Pages redeploys automatically, usually within a minute or two.

---

## Deployment Guide

Deploying to production takes less than two minutes using **GitHub Pages**:

1. Push your cloned fork or repository directly to your personal GitHub profile.
2. Navigate to your repository dashboard and select **Settings** ➔ **Pages**.
3. Under the **Build and deployment** section, configure the source dropdown to **Deploy from a branch**.
4. Set your target branch to `main` and the deployment folder to `/ (root)`, then click **Save**.
5. Your application will be live at `https://samikhan43.github.io/roadmap-hub/` momentarily.

---

## Tech Stack

- **Core Engine:** Vanilla HTML5, CSS3, and modern ECMAScript JavaScript (no compilation dependencies for learners)
- **Styling Architecture:** [Tailwind CSS](https://tailwindcss.com) (distributed via CDN)
- **Iconography:** [Lucide](https://lucide.dev) (distributed via CDN)
- **State Lifecycle:** Native Web `localStorage` API for progress caching (client-side only, no cookies)
- **Content Tooling:** A small Python 3 build script and GitHub Actions validation for contributors

---

## Contributing

We welcome community collaborations! Whether you are adding a completely new roadmap, a new topic, fixing a logical error, or updating examples:

1. Fork the project repository and isolate a working branch: `git checkout -b topic/my-new-topic`
2. Copy `_template/_TOPIC_TEMPLATE.json` to `content/<roadmap>/topics/NN-short-name.json` and fill in every field.
3. Run `python3 scripts/build.py <roadmap>` and preview the page locally.
4. Confirm code samples and outputs behave as expected, and that the practice question can be solved from the lesson alone.
5. Commit your topic file **and** the rebuilt `<roadmap>/index.html`, then submit a descriptive Pull Request.

A GitHub Action rebuilds every roadmap on each pull request and fails if a topic file is invalid or a generated page is out of date. Read [CONTRIBUTING.md](CONTRIBUTING.md) for the field guide and quality checklist.

Not ready to write a topic? Open a **Topic request** issue. If you spot an error in a live lesson, open a **Content error** issue containing the topic title.

> The SQL roadmap is currently a standalone page. Corrections to it are welcome through an issue or a pull request that edits `sql-roadmap/index.html` directly.

---

## Technical Notes

- **Code Execution:** Code blocks and results inside lessons are **pre-written and hand-verified**. Clicking "Run" reveals the expected output and does not execute any code on your machine.
- **Data Persistence:** Clearing browser data or using Incognito windows will reset your client-side progress back to default.
- **Generated Files:** Files named `index.html` inside roadmap folders built from `content/` are generated. Edit the JSON sources, then rebuild.

---

## License

This project is open-source software distributed under the terms of the [MIT License](LICENSE). You are free to modify, redistribute, and build on it as needed.

---

<div align="center">

If these roadmaps helped speed up your learning journey, consider giving the repository a star to support the project!

</div>
