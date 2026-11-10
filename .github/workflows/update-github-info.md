---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  copilot-requests: write
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    reviewers: [mona]
    draft: false
---

# Update GitHub Info

Read `notes/mona-notes.md` and `site/content/github-info.md` to understand the site's editorial guidance and current content.

Use the web-fetch tool to read all of the following sources:
- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Identify recent, verified updates that will help developers learn GitHub faster. Update only `site/content/github-info.md`. Keep summaries short and practical, preserve its existing themes, and link each item to its source on the GitHub Blog, Changelog, or Awesome Copilot workflows. Do not invent details or include an item unless its source supports the summary.

When there are meaningful updates, propose the content change as a non-draft pull request for Mona to review. Include a concise title and explain the changes with links to the sources. Do not commit changes directly or modify any other file. If there are no meaningful updates, leave the file unchanged and do not open a pull request.