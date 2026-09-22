---
name: update-github-info
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    max: 1
    reviewers: [Mona]
    draft: true
---

# Update GitHub Information

Keep the repository's GitHub information page current for Mona to review.

## Instructions

1. Read `notes/mona-notes.md` with the file editing tools.
2. Use `web-fetch` to read `https://github.blog/latest/` and `https://github.blog/changelog/`.
3. Use `web-fetch` to read any relevant external public guidance linked from those pages. Do not use shell commands, CLI commands, or sandboxed commands for web access.
4. Use the GitHub repository API tools to read repository guidance or reference files. Do not use terminal, CLI, or sandboxed commands for those repository reads.
5. Update `site/content/github-info.md` with accurate, concise information based on the notes and fetched sources. Preserve the file's existing structure and style, and make no unrelated changes.
6. Review the resulting diff and only request a pull request when the file has a meaningful update.
7. Use the `create-pull-request` safe output to propose the changes for Mona to review. Do not write directly to the default branch. Include the sources consulted and a short summary of the update in the pull request body.