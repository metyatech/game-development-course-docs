# game-development-course-docs

Course content repository for the game programming and game development course.

This repo is **content-only** (not a Next.js app). The shared site runtime lives in `metyatech/course-docs-site`.

The course materials are intentionally placeholders for now. Add actual lessons, examples, exercises, and exam preparation under `content/` when the curriculum is ready.

## Local preview

```sh
git clone https://github.com/metyatech/course-docs-site.git
cd course-docs-site
npm install
```

Then point `course-docs-site` at this repository through `.env.course.local`:

```sh
# In course-docs-site/.env.course.local
COURSE_CONTENT_SOURCE=../path-to-game-development-course-docs
```

Use any local path that is valid from the `course-docs-site` checkout. If the two repositories are siblings, that can be `../game-development-course-docs`.

## Verify

Run the canonical verification command from this repository:

```sh
node scripts/verify.mjs
```

What it does:

- runs Prettier in check-only mode for this repository
- verifies that fenced source-code examples are not reformatted by Prettier
- verifies that each `<Exercise>` block has a Markdown heading and no `title` prop
- verifies that code examples use four-space indentation
- runs `markdownlint` for this repository
- locates a local `course-docs-site` checkout automatically when the repos live in the same workspace
- runs `course-docs-site` lint and `build:verified` with `COURSE_CONTENT_SOURCE` set to this repository

If `course-docs-site` is not in the same workspace, set `COURSE_DOCS_SITE_DIR` in your shell or terminal session to that checkout before running `node scripts/verify.mjs`.

Automatic discovery looks for a local checkout named `course-docs-site` while walking up parent directories from this repository.

## Project files

- `content/`: course pages (MDX)
- `scripts/verify.mjs`: canonical verification entrypoint for local delivery checks
- `public/`: static files (for example, images under `public/img/**`)
- `site.config.ts`: per-course site configuration consumed by `course-docs-site`

## Release / deploy

This repository does not deploy by itself. If a public course site is needed later, configure deployment through the shared `metyatech/course-docs-site` workflow pattern.

## Related docs

- [SECURITY.md](SECURITY.md)
- [CONTRIBUTING.md](CONTRIBUTING.md)
- [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)
- [LICENSE](LICENSE)
- [CHANGELOG.md](CHANGELOG.md)

## Agent rules

Regenerate `AGENTS.md` after editing `agent-ruleset.json`:

```bash
compose-agentsmd
```
