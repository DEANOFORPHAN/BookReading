# Repository Guidelines

## Project Structure & Module Organization

This repository is an Obsidian reading vault rather than a software application. `.obsidian/` contains vault settings; avoid changing `workspace.json` unless the workspace layout is intentionally being updated. Each book has a top-level directory, currently `日本蜡烛图技术/`, with:

- `README.md` for the learning plan, progress index, and course rules.
- `每日笔记/` for dated lessons such as `2026-08-14.md`.
- `概念卡片/` for reusable topic summaries such as `K线基础.md`.
- `插图/` for self-contained SVG diagrams embedded in notes.

## Local Development & Validation Commands

There is no build step, package manager, or automated test suite. Work directly in Markdown and preview changes in Obsidian.

- `open -a Obsidian .` opens this vault on macOS.
- `find 日本蜡烛图技术 -type f | sort` lists book content and assets.
- `rg -n '\[\[|!\[\[' 日本蜡烛图技术` reviews internal links and embeds.
- `rg -n '^#{1,3} ' -g '*.md' .` checks heading structure.

## Content Style & Naming Conventions

Write concise Chinese instructional prose. Define technical terms in everyday language on first use; do not assume prior trading knowledge. Use one H1 per note, descriptive H2/H3 sections, short paragraphs, and Markdown tables only when they improve comparison. Daily notes use `YYYY-MM-DD.md`; concept cards use clear Chinese nouns. Keep Obsidian links relative, for example `[[../概念卡片/K线基础|K 线基础]]`.

Each lesson should take about 20 minutes and follow the 30-day roadmap. Use two dense 8-9 minute teaching blocks, each followed by one short 1-2 question interaction, then a 2-4 minute summary. Avoid stretching one concept across many conversational turns. Include at least one clear SVG structure or scenario diagram. Label trend context, key prices, confirmation, and invalidation conditions.

## Review & Testing Guidelines

Open every changed note in Obsidian reading view. Confirm links resolve, SVGs render without clipping or overlapping labels, frontmatter remains valid YAML, and the book README links to new lessons and cards. Technical-analysis explanations must distinguish observed prices from probabilistic interpretation and must not present personalized investment advice.

## Commit & Pull Request Guidelines

No Git history currently exists, so no established convention can be inferred. If version control is initialized, use focused imperative commits such as `docs: add hammer pattern lesson`. Pull requests should summarize the lesson or structural change, identify new notes and assets, and include screenshots for visual changes. Do not commit `.DS_Store`; avoid incidental Obsidian workspace-state churn. Cite sources when facts depend on an external reference, and do not reproduce substantial copyrighted book text.

## Daily Automatic Publishing

After the morning automation generates or updates reading-plan content, validate the changed Markdown, frontmatter, links, and SVG files, then automatically commit and push the new reading content without waiting for another confirmation. Include the dated lesson or review note, related concept cards and illustrations, and the affected book `README.md`.

- Fetch the remote before publishing and confirm the current branch is not behind or diverged.
- Stage only files that belong to the generated reading-plan update. Exclude unrelated untracked files, `.DS_Store`, and incidental `.obsidian/workspace.json` changes.
- Use a focused commit message such as `docs: add 2026-08-24 candlestick lesson` or `docs: update weekly reading review`.
- Push to the configured upstream branch, normally `origin/main`, and verify local `HEAD` matches the remote-tracking branch afterward.
- Never force-push. If fetching, committing, or pushing fails, leave the local work intact and report the exact blocker instead of rewriting history.
