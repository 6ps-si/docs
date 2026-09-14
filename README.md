# 6PS documentation

The documentation site for [6PS Studio](https://studio.6ps.si), built with [Mintlify](https://mintlify.com).

## Local preview

```bash
npm i -g mint      # Node 20.17+; Node 25 is not supported yet
mint dev           # run from this directory, the one holding docs.json
```

If every page 404s, `mint dev` was started outside a directory containing a valid `docs.json`.
If the local build misbehaves, run `mint update`.

## Layout

| Path | Contents |
| --- | --- |
| `docs.json` | Navigation, theme, and site config |
| `index.mdx`, `quickstart.mdx` | Site entry points |
| `docs/` | Product documentation, one folder per area |
| `blog/` | Long-form posts (empty for now) |
| `images/` | Screenshots, mirroring the `docs/` folder structure |
| `logo/`, `favicon.svg` | Brand assets |
| `Templates/` | Post template, excluded from the build |

## Status

Every page under `docs/` is currently an outline: frontmatter, section headings, notes on what
each section should cover, and a list of the `Studio/` source files that prove the behavior.
Screenshots are marked with `SCREENSHOT:` comments inside `<Frame>` blocks and have not been
captured yet.

Before filling in a page, read the source files listed at the bottom of it. Product facts come
from `../Studio/`, which is read-only, and from `../Design/brief.md`.
