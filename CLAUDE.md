# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The 6PS documentation site, built with Mintlify. `../CLAUDE.md` covers the wider 6PS working
directory and carries copy rules that apply here too: no em dashes or en dashes anywhere,
positive framing instead of contrastive "not X, but Y" phrasing, and never inventing product
capabilities, limits, or pricing.

## Editing

For any edit of .mdx files use skill `/mintlify`.

## Commands

There is no package manifest, no test suite, and no build step. The only tool is the global
Mintlify CLI:

```bash
npm i -g mint     # Node 20.17+; Node 25 is not supported
mint dev          # local preview, run from this directory
mint update       # update the CLI when the local build misbehaves
```

A 404 on every page means `mint dev` was started outside a directory containing a valid
`docs.json`. Validate `docs.json` against `https://mintlify.com/docs.json` before committing
navigation changes.

## Current state

Every page under `docs/` is an outline, not finished copy: frontmatter, H2 headings, a note per
section on what to cover, and a trailing comment listing the `Studio/` files that prove the
behavior. Fill a page in by reading those files first.

`docs.json` carries two intentionally empty groups, `Tutorials` and `Blog`, held as placeholders.
Mintlify accepts them. Leave them empty until there is content.

## Source of truth for product content

Never describe 6PS Studio behavior from memory or inference. The app is read-only at `../Studio/`:

- `../Studio/public/llms.txt` - marketing-accurate product summary, the best starting point for prose
- `../Studio/.claude/CLAUDE.md` - architecture and the full REST API reference
- `../Studio/app/locales/en.ts` - the exact UI labels users see, so docs match the interface
- Per-area notes: `../Studio/components/Editor/CLAUDE.md`, `../Studio/app/virtual-walkthrough/CALUDE.md`,
  `../Studio/components/virtual-walkthrough/imageProcessor/CLAUDE.md`, `../Studio/components/Settings/business.md`

Positioning and pricing decisions live in `../Design/brief.md`. Never modify anything under `../Studio/`.

## Scope decisions already made

These were settled deliberately. Raise them before reversing one.

- End-user guides only. No REST API reference and no developer or integrator section.
- Documentation is keyed to the tool, not to the audience. There is no architect or real estate split.
- The standalone `/ai-staging` page is not documented, because it is not surfaced in the app's
  navigation. AI features inside the 3D Editor and the Virtual Walkthrough are documented in place.
- No billing section, no prices, and no link to pricing. Plan names may appear inline where a user
  meets a gate: AI output is watermarked on the free plan, the downloadable package and code embed
  are Pro-only, and some library sections are locked by plan.
- Teams documentation covers seats and shared quota as concepts, without prices.
- English now. Slovenian is a later Mintlify localization, so keep slugs stable.

## Two details that must never appear in published copy

The product is built on Babylon.js, and image upscaling uses a specific named model. Refer to both
generically, for example "optional upscale".

## Honesty constraint

Do not describe the 3D Editor's output as replacing a final render. Position it as cutting
rendering time from about an hour to roughly ten seconds. Avoid "revolutionary" and "game-changing".

## Conventions

- Second person. Prerequisites first on procedural pages.
- Every page needs `title` and `description` frontmatter.
- Relative paths for internal links. Never absolute URLs to this site.
- Language tags on every code block, alt text on every image.
- Every new page must be added to `docs.json` navigation in the same change, or it is orphaned.
- Screenshots go in `images/`, mirroring the `docs/` folder structure.

## Git

- Never use `--no-verify`. Never skip or disable hooks.
- Create a branch when no clear branch exists for the change.
