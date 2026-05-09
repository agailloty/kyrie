# kyrie

A clean, multilingual Hugo theme for **blog**, **documentation**, and **portfolio/projects** sites.

- 7 color schemes with light / dark / auto mode
- 3 interface sizes (m, l, xl)
- Bilingual out of the box (FR + EN i18n strings included)
- Blog list in cards or list layout
- Sticky TOC sidebar on article pages
- Reading progress bar
- Project cards with category filter
- Docs section with sidebar navigation

---

## Requirements

- Hugo **0.112.0** or later (extended version recommended)

---

## Installation

### Option 1 — Git submodule (recommended)

```bash
# From your Hugo site root:
git submodule add https://github.com/agailloty/kyrie themes/kyrie
```

Set in `hugo.toml`:

```toml
theme = "kyrie"
```

To update later:

```bash
git submodule update --remote --merge
```

### Option 2 — Hugo Modules

Prerequisites: Go installed, run `hugo mod init github.com/your-username/your-site` once.

```toml
# hugo.toml
[module]
[[module.imports]]
  path = "github.com/agailloty/kyrie"
```

```bash
hugo mod get github.com/agailloty/kyrie
hugo mod tidy
```

### Option 3 — Manual copy

Download/clone the repository and copy the `kyrie/` folder into your site's `themes/` directory.

---

## Quick-start

Copy `exampleSite/hugo.toml` into your site root as a starting point, then adjust as needed.

Minimal `hugo.toml`:

```toml
baseURL = "/"
title   = "My Site"
theme   = "kyrie"

[params]
colorScheme = "teal"   # teal | ocean | forest | sunset | lavender | slate | rose
colorMode   = "auto"   # auto | light | dark
size        = "m"      # m | l | xl

[params.brand]
name     = "My Site"
logoText = "My Site"

[[menu.main]]
name   = "Blog"
url    = "/blog/"
weight = 10

[[menu.main]]
name   = "About"
url    = "/about/"
weight = 30
```

---

## Parameters reference

### `[params]`

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `tagline` | string | `""` | Short tagline shown in hero |
| `description` | string | `""` | Site meta description |
| `size` | `"m"` \| `"l"` \| `"xl"` | `"m"` | Global interface size |
| `colorScheme` | string | `"teal"` | One of: `teal`, `ocean`, `forest`, `sunset`, `lavender`, `slate`, `rose` |
| `colorMode` | `"auto"` \| `"light"` \| `"dark"` | `"auto"` | Light/dark mode |
| `dateFormat` | string | `"02 Jan 2006"` | Go date format for post dates |

### `[params.brand]`

| Key | Description |
|-----|-------------|
| `name` | Site name in the navigation bar |
| `logoText` | Text used as the logo |

### `[params.home]`

| Key | Type | Description |
|-----|------|-------------|
| `showHero` | bool | Show the hero banner |
| `heroTitle` | string | Hero heading text |
| `heroSubtitle` | string | Hero sub-heading text |

#### `[[params.home.sections]]`

Each entry adds a section to the home page in declaration order.

| Key | Type | Description |
|-----|------|-------------|
| `type` | `"blog"` \| `"projects"` \| `"custom"` | Section type |
| `title` | string | Section heading |
| `count` | int | Number of items (blog only) |
| `layout` | `"cards"` \| `"list"` | Display style (blog only) |
| `moreUrl` | string | "See all" link URL (blog only) |
| `showFilter` | bool | Show category filter buttons (projects only) |
| `allLabel` | string | Label for the "All" filter (projects only) |

### `[params.blog]`

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `showAuthor` | bool | `true` | Display author in post meta |
| `showDate` | bool | `true` | Display publication date |
| `showReadingTime` | bool | `true` | Display estimated reading time |
| `showTags` | bool | `true` | Display tags |
| `listLayout` | `"cards"` \| `"list"` | `"cards"` | Default blog list view |

### `[params.docs]`

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `sidebar` | bool | `true` | Show docs navigation sidebar |
| `showBreadcrumbs` | bool | `true` | Show breadcrumb navigation |
| `showToc` | bool | `true` | Show table of contents |

### `[params.footer]`

| Key | Type | Description |
|-----|------|-------------|
| `showCopyright` | bool | Show "© Year Title" copyright notice |
| `customText` | string | Additional HTML/text shown in the footer |

---

## Content types & front matter

Create content with Hugo archetypes:

```bash
hugo new blog/my-post.md
hugo new docs/my-page.md
hugo new projects/my-project.md
hugo new about.md
```

### Blog post (`type: "blog"`)

```yaml
---
title: "My Post"
date: 2024-06-01
type: "blog"
author: "Your Name"
tags: ["tag1", "tag2"]
image: "/images/cover.jpg"
description: "Short summary."
draft: false
---
```

### Docs page (`type: "docs"`)

```yaml
---
title: "My Page"
date: 2024-06-01
type: "docs"
weight: 10
toc: true
description: "Short summary."
draft: false
---
```

### Project (`type: "projects"`)

```yaml
---
title: "My Project"
date: 2024-06-01
type: "projects"
weight: 1
categories: ["web", "open-source"]
image: "/images/project.jpg"
link: "https://github.com/you/project"
description: "One-line description."
featured: true
draft: false
---
```

### Static page (`type: "page"`)

```yaml
---
title: "About"
date: 2024-06-01
type: "page"
description: "About this site."
draft: false
---
```

---

## Multilingual setup

The theme ships with i18n strings for English (`i18n/en.toml`) and French (`i18n/fr.toml`). To add a language, create `i18n/{lang}.toml` with the same keys translated.

Example bilingual config (FR default, EN secondary):

```toml
defaultContentLanguage         = "fr"
defaultContentLanguageInSubdir = true

[languages.fr]
languageName = "Français"
weight       = 1
contentDir   = "content/fr"

[languages.en]
languageName = "English"
weight       = 2
contentDir   = "content/en"
```

---

## Customization

### Override layouts

Copy any file from `themes/kyrie/layouts/` into your site's `layouts/` directory — Hugo gives site layouts priority over theme layouts.

### Add a color scheme

Add `.theme-{name}` CSS selectors in `assets/css/main.css` following the existing scheme patterns (light and dark variants).

---

## Development

```bash
# Local dev server with drafts
hugo server -D

# Production build
hugo --minify
```

---

## License

[MIT](LICENSE)

## Archetypes

Le theme fournit:
- archetypes/blog.md
- archetypes/docs.md
- archetypes/page.md

Exemples:
- hugo new blog/mon-article.md
- hugo new docs/installation.md
- hugo new about.md

## Multilingue

Le site est configure en francais et anglais via:
- defaultContentLanguage
- defaultContentLanguageInSubdir
- languages.fr
- languages.en

Les traductions d'interface se trouvent dans:
- i18n/fr.toml
- i18n/en.toml
