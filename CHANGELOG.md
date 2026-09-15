# Changelog

All notable changes to this repository are recorded here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [Unreleased]

### Added

- CODEOWNERS, SUPPORT.md, CODE_OF_CONDUCT.md, SECURITY.md, a CONTRIBUTING.md scoped to corrections only
- A YAML correction issue form, a config.yml and a pull request template
- `.markdownlint.json` and a markdown-lint CI workflow, with its own workflows README
- Full revision notes for Weeks 6 to 11, matching the depth and structure of the existing Weeks 1 to 5 notes
- Completed lab notebooks for Weeks 4, 7 and 8

### Changed

- "License" corrected to "Licence" throughout, except where naming the MIT Licence's own file
- Week folders renamed from `Week1`-`Week11` to zero-padded `Week_01`-`Week_11`, so they sort in the correct numeric order instead of alphabetically (`Week1`, `Week10`, `Week11`, `Week2`...)
- Top badge row rebuilt as flat, left-aligned badges matching the rest of the fleet, replacing the boxed `for-the-badge` style
- Added a Repository Structure section and a Contact and Support section with callouts, matching the README structure used across other repositories
- `.markdownlint.json` tailored further: `MD022` and `MD052` disabled to match this repository's own heading style and matrix notation, `MD037` disabled since "A*" and multiplication asterisks in maths notation are not emphasis markers
- Status badge updated from in progress to completed, now that every week has notes and every week with an available lab notebook has one
