# WordPress Theme Contribution Guide 📘

[![WordPress](https://img.shields.io/badge/WordPress-21759B?style=for-the-badge&logo=wordpress&logoColor=white)](https://wordpress.org/)
[![WordCamp](https://img.shields.io/badge/WordCamp_Sylhet-2026-blue?style=for-the-badge)](https://sylhet.wordcamp.org/)
[![License: GPL v2+](https://img.shields.io/badge/License-GPL%20v2%2B-green.svg?style=for-the-badge)](https://www.gnu.org/licenses/gpl-2.0.html)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](https://github.com/WordPress/ipsum/pulls)

> **Welcome to the official WordPress Theme Contribution Guide!**  
> This comprehensive guide was created for **WordCamp contributors**, theme developers, and reviewers. It covers everything you need to know about contributing to **WordPress core bundled themes**, reviewing **community themes on WordPress.org**, building **block themes from scratch**, and contributing to **Ipsum (the upcoming WordPress 7.2 core default theme)**.

---

### 📥 Download Offline Guides
* 📄 **[Download Official PDF Guide (10 Pages)](./WordPress-Theme-Contribution-Guide.pdf)**
* 📝 **[Download Editable Word Document (.docx)](./WordPress-Theme-Contribution-Guide.docx)**

---

## 📑 Table of Contents
1. [Theme Table Lead](#-theme-table-lead)
2. [Section A: Core Theme Contribution](#-section-a-core-theme-contribution)
   * [What Are Bundled Themes?](#what-are-bundled-themes)
   * [Ways to Contribute](#ways-to-contribute-to-the-default-theme)
   * [Step-by-Step Developer Workflow](#step-by-step-developer-workflow)
   * [Crucial for Props](#-crucial-for-props)
3. [Section B: Community Theme Reviews](#-section-b-community-theme-reviews)
   * [What is a Theme Reviewer?](#what-is-a-theme-reviewer)
   * [Testing Environment Setup](#set-up-your-testing-environment)
   * [13 Key Review Requirements](#key-review-requirements)
   * [Theme Review Workflow & Response Template](#the-theme-review-workflow-step-by-step)
4. [Section C: Block Theme Development & Ipsum](#-section-c-block-theme-development)
   * [Block Theme vs Classic Theme](#block-theme-vs-classic-theme)
   * [Required File Structure](#step-1-required-file-structure)
   * [theme.json, Templates & Patterns](#themejson-templates--block-patterns)
5. [Spotlight: Contributing to Ipsum (WordPress 7.2 Default Theme)](#-contributing-to-ipsum-wordpress-72-default-theme)
   * [Instant Test in Browser (Playground)](#1-instant-browser-testing-zero-install)
   * [Local Development with wp-env](#2-local-development-setup-wp-env)
   * [Creating Block Patterns](#3-creating-block-patterns-for-ipsum)
   * [Submitting a Pull Request](#4-submitting-a-pull-request)
6. [Key Resources & Quick Links](#-key-resources--quick-links)

---

## 👤 Theme Table Lead

Prepared and moderated for **WordCamp Sylhet 2026 • Contributor Day**:

| Table Lead | Profiles & Connect Links |
| :--- | :--- |
| **Noruzzaman** <br> *Theme Table Lead* | 🌐 **WordPress.org:** [profiles.wordpress.org/noruzzaman](https://profiles.wordpress.org/noruzzaman/) <br> 💻 **GitHub:** [@noruzzamans](https://github.com/noruzzamans) <br> 💼 **LinkedIn:** [linkedin.com/in/noruzzaman](https://www.linkedin.com/in/noruzzaman/) |

---

## 🏛️ Section A: Core Theme Contribution
*Contributing to WordPress Bundled Default Themes.*

### What Are Bundled Themes?
Bundled themes (e.g. *Twenty Twenty-Four*, *Twenty Twenty-Five*, *Ipsum*) are the default themes included when you install WordPress. A new default theme is included in the major release of the year. 

### Ways to Contribute to the Default Theme
1. **Suggest Features:** Submit feature ideas via GitHub issues or the `#themes` Slack channel.
2. **Test and Report Issues:** Prioritize accessibility testing and open tickets on Core Trac or GitHub.
3. **Contribute Code:** Develop features, audit code, and review pull requests.
4. **Write Copy and Documentation:** Help write theme descriptions and documentation using sentence casing.

### Step-by-Step Developer Workflow

#### 1. Find a Bug or Feature Ticket
* **Core Trac:** [core.trac.wordpress.org](https://core.trac.wordpress.org/)
* **Bundled Theme Component:** [core.trac.wordpress.org — Bundled Theme](https://core.trac.wordpress.org/query?status=!closed&component=Bundled+Theme)
* Search to ensure the bug is not already reported, then comment that you are working on it.

#### 2. Submit a Pull Request (PR) via Git
```bash
# Create a descriptive branch
git checkout -b fix/theme-issue-description

# Stage and commit your changes
git add .
git commit -m "Fix: describe your change clearly"

# Push to your fork
git push origin fix/theme-issue-description
```

### ⚠️ Crucial for Props
In your PR description, write `Fixes #TRAC_TICKET_NUMBER` or `Fixes #ISSUE_NUMBER`.  
**Always list the WordPress.org usernames of all contributors who should receive props/credit!**

> 🔗 **Important:** [Link your GitHub and WordPress.org profiles](https://make.wordpress.org/core/handbook/tutorials/linking-your-github-and-w-org-profiles/) to automatically receive official contributor badges on WordPress.org.

---

## 🔍 Section B: Community Theme Reviews
*How to Review and Approve Themes for the WordPress.org Theme Directory.*

### What is a Theme Reviewer?
A theme reviewer is a volunteer who helps theme authors add their theme to the official WordPress.org directory. Reviewers check for security, GPL license compliance, accessibility, and code quality. Anyone can become a reviewer!

### Set Up Your Testing Environment
1. **Local WordPress Site:** Install a local environment using [WordPress Studio](https://developer.wordpress.com/studio/), LocalWP, or Docker.
2. **Enable Debug Mode:** In `wp-config.php`, set:
   ```php
   define( 'WP_DEBUG', true );
   define( 'WP_DEBUG_LOG', true );
   ```
3. **Import Test Data:** Go to `Tools > Import > WordPress` and upload the [theme-xml-test-data.xml](https://github.com/WordPress/theme-test-data).
4. **Plugins to Install:**
   * **Required:** [Theme Check](https://wordpress.org/plugins/theme-check/)
   * **Recommended:** [Query Monitor](https://wordpress.org/plugins/query-monitor/), [Debug Bar](https://wordpress.org/plugins/debug-bar/), [Theme Sniffer](https://github.com/WPTT/theme-sniffer)

### Key Review Requirements
All submitted themes must follow the [Theme Review Requirements](https://make.wordpress.org/themes/handbook/review/required/):
1. **Licensing & Copyright:** 100% GPL-compatible. All code, images, and fonts must state license info.
2. **Privacy:** User tracking must be disabled by default and strictly opt-in.
3. **Accessibility:** Must include skip links, keyboard navigation, and visible focus states.
4. **Code Quality:** No PHP/JS errors or notices. All input must be sanitized and output escaped.
5. **Functionality:** No custom post types, shortcodes, or plugin-territory features.
6. **Plugins:** May only recommend plugins hosted on WordPress.org without auto-installing.
7. **Naming:** Theme names must not include "WordPress", "Theme", or "Twenty*".
8. **Internationalization:** All strings must use `gettext` with the theme slug as text-domain.
9. **Files:** No zip files, hidden files, or remote resource loading without user consent.
10. **Classic Themes:** Must include `wp_head()`, `body_class()`, `wp_footer()`, `wp_body_open()`, `post_class()`.
11. **Block Themes:** Must include `style.css`, `readme.txt`, `theme.json`, and `templates/index.html`.
12. **Settings:** Use `admin_notices` hook. No activation popups. No demo imports.
13. **Credits:** Only one front-facing credit link allowed. No obtrusive upselling.

### The Theme Review Workflow (Step-by-Step)
1. **Find a Theme Ticket:** Check the [New Themes Queue](https://themes.trac.wordpress.org/report/2) or ask in `#themes` Slack. Leave a comment saying you are starting the review.
2. **Run Review:** Run Theme Check, inspect responsive layouts, check Query Monitor for notices. *(Note: Do NOT review design taste—focus strictly on security, standards, and licensing).*
3. **Write Ticket Response:**
   * **Welcome:** Greet the author warmly.
   * **Outcome:** Clearly state `Approved` or `Changes Required`.
   * **Required Items:** List issues that must be fixed.
   * **Recommended Items:** Non-blocking suggestions.
   * **Next Steps:** Explain what the author needs to do next.
4. **Follow Up:** Do not close the ticket; allow the author to submit an updated zip.

---

## 🎨 Section C: Block Theme Development
*How to Develop a Block Theme from Scratch.*

### Block Theme vs Classic Theme

| Feature | Block Theme (WordPress 5.9+) | Classic Theme |
| :--- | :--- | :--- |
| **Templates** | HTML files in `/templates/` | PHP files (`index.php`, `page.php`) |
| **Styling** | `theme.json` + block styles | `style.css` + PHP hooks |
| **Editor** | Full Site Editor (FSE) | Customizer / widget areas |
| **Patterns** | Registered block patterns | Shortcodes / PHP widgets |
| **Required Files** | `style.css`, `readme.txt`, `theme.json`, `templates/index.html` | `style.css`, `index.php`, `functions.php` |

### Step 1: Required File Structure
```
my-block-theme/
├── style.css             # Theme header (Name, Author, Version, License)
├── readme.txt            # Changelog, license info, contributors
├── theme.json            # Global styles, color palettes, fonts, spacing
├── functions.php         # (Optional) Enqueue scripts, register patterns
├── templates/
│   ├── index.html        # (Required) Default fallback template
│   ├── single.html       # Single blog posts
│   ├── page.html         # Static pages
│   └── 404.html          # Not found page
├── parts/
│   ├── header.html       # Header template part
│   └── footer.html       # Footer template part
└── patterns/
    └── hero.php          # Block pattern files
```

### Required `style.css` Headers
```css
/*
Theme Name: My Custom Theme
Author: Your Name
Author URI: https://yourwebsite.com
Description: A clean, modern block theme built with full site editing.
Version: 1.0.0
Requires at least: 6.5
Tested up to: 7.2
Requires PHP: 7.4
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Text Domain: my-custom-theme
*/
```

---

## 🚀 Contributing to Ipsum (WordPress 7.2 Default Theme)

> 🆕 **What's New in WordPress 7.2:**  
> On September 16, 2026, WordPress officially announced **Ipsum** as the upcoming default theme for WordPress 7.2. Project lead Matt Mullenweg announced that WordPress is **moving away from year-based theme names** ("Twenty Twenty-X") to purposeful names.  
> * **Concept:** An intentionally minimal, "blank canvas" blog theme.  
> * **Design Team:** Henrique Iamarino ([@iamarinoh](https://profiles.wordpress.org/iamarinoh/) - Lead Designer), Carolina Nymark ([@poena](https://profiles.wordpress.org/poena/)), Maggie Cabrera ([@onemaggie](https://profiles.wordpress.org/onemaggie/)), Juanfra Aldasoro ([@juanfra](https://profiles.wordpress.org/juanfra/)).  
> * **Repository:** [github.com/WordPress/ipsum](https://github.com/WordPress/ipsum)

### 1. Instant Browser Testing (Zero Install!)
You can test Ipsum directly inside your browser without installing Node, Docker, or local servers:
👉 **[Open Ipsum in WordPress Playground](https://playground.wordpress.net/?blueprint-url=https://raw.githubusercontent.com/WordPress/ipsum/trunk/.github/blueprint.json)**  
*(Or browse the hosted demo at [ipsum.mystagingwebsite.com](https://ipsum.mystagingwebsite.com/))*

### 2. Local Development Setup (`wp-env`)
The official way to contribute code to Ipsum is via `wp-env`:
```bash
# 1. Clone the repository
git clone https://github.com/WordPress/ipsum.git
cd ipsum

# 2. Install dependencies & start Docker WordPress environment
npm install
npm run env:setup
```
* **Local Site:** [http://localhost:8899](http://localhost:8899)
* **WP Admin:** [http://localhost:8899/wp-admin/](http://localhost:8899/wp-admin/) (Username: `admin`, Password: `password`)
* Comes pre-configured with **Ipsum**, **Gutenberg**, and **Theme Check** plugins!

**Everyday Commands:**
```bash
npm run env:start    # Start existing container
npm run env:stop     # Stop container
npm run env:status   # Check status and ports
npm run env:reset    # Reset database (run env:setup after)
```

### 3. Creating Block Patterns for Ipsum
Ipsum ships with minimal CSS; styles are achieved via `theme.json` and block patterns in `/patterns/`.
```php
<?php
/**
 * Title: Minimalist Post Header
 * Slug: ipsum/minimal-header
 * Categories: banner, featured
 * Description: A quiet, editorial header for blog posts.
 */
?>
<!-- wp:group {"layout":{"type":"constrained"}} -->
<div class="wp-block-group">
    <!-- wp:post-title {"level":1} /-->
    <!-- wp:post-date /-->
</div>
<!-- /wp:group -->
```
*For hidden utility patterns (like 404), add `* Inserter: no` to the header and prefix the filename with `hidden-`.*

### 4. Submitting a Pull Request
1. Fork [WordPress/ipsum](https://github.com/WordPress/ipsum).
2. Create a branch: `git checkout -b fix/issue-123-title`
3. Commit and push:
   ```bash
   git add .
   git commit -m "Fix: improve mobile typography (#123)"
   git push origin fix/issue-123-title
   ```
4. Open a PR on [WordPress/ipsum/pulls](https://github.com/WordPress/ipsum/pulls) linking the issue (`Fixes #123`) and listing WordPress.org usernames for props.

---

## 🔗 Key Resources & Quick Links

| Resource | URL |
| :--- | :--- |
| 🌐 **Theme Review Handbook** | [make.wordpress.org/themes/handbook/](https://make.wordpress.org/themes/handbook/) |
| 💬 **Making WordPress Slack (#themes)** | [make.wordpress.org/chat/](https://make.wordpress.org/chat/) |
| 📚 **Theme Developer Handbook** | [developer.wordpress.org/themes/](https://developer.wordpress.org/themes/) |
| 🚀 **WordPress/ipsum Repository** | [github.com/WordPress/ipsum](https://github.com/WordPress/ipsum) |
| 📢 **Introducing Ipsum Announcement** | [make.wordpress.org/core/2026/09/16/introducing-ipsum-the-new-default-theme/](https://make.wordpress.org/core/2026/09/16/introducing-ipsum-the-new-default-theme/) |
| 🧪 **WordPress Playground Demo** | [Playground Blueprint](https://playground.wordpress.net/?blueprint-url=https://raw.githubusercontent.com/WordPress/ipsum/trunk/.github/blueprint.json) |
| 🐛 **Themes Trac Queue** | [themes.trac.wordpress.org/report/2](https://themes.trac.wordpress.org/report/2) |
| 🎓 **Low-Code Block Theme Course** | [learn.wordpress.org](https://learn.wordpress.org/course/develop-your-first-low-code-block-theme/) |

---

### Happy contributing to WordPress! 💙
*Created with love for WordCamp Sylhet 2026 Contributor Day.*
