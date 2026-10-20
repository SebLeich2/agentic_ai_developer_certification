---
name: update-github-info
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    max: 1
    allowed-files:
      - site/content/github-info.md
    draft: false
    fallback-as-issue: false
---

Read `notes/mona-notes.md` and the current `site/content/github-info.md`. Then use web fetch to read:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Update only `site/content/github-info.md` with concise, practical GitHub guidance based on useful, current information from those official sources. Focus on helping developers learn GitHub faster, avoid duplicating existing themes, and cite the source URL for each new item. Do not invent details or add an item unless the source supports it.

If the sources contain a worthwhile update, open one pull request with a clear title and description for Mona to review. Do not write directly to the default branch or change any other files. If there is no worthwhile update, leave the file unchanged and do not open a pull request.
