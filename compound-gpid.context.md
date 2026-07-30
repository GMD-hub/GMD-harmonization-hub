# Project Context

Additional context for Copilot and the Compound GPID plugin. Edit freely —
this file is committed to git and shared with the team.

## Data Sources
<!-- Where does data come from? File paths, databases, APIs, vintage conventions -->

## Domain Rules
<!-- Project-specific rules that Copilot should always follow -->

### Documentation validation

- For navigation or link-oriented documentation changes in this repository,
	run a lightweight smoke check even when there is no `tests/` harness.
- The minimum smoke check should verify the touched documentation files exist
	and that the newly introduced navigation anchor is present in `README.md`.
- For canonical Quarto document edits, pair the navigation smoke check with a
	render smoke check using the documented `quarto render` commands.

## Work in Progress
<!-- Modules, features, or migrations currently underway -->

## Workspace Notes
<!-- Related folders, dependencies on other projects in the VS Code workspace -->

## Wiki Configuration
<!-- folder: wiki -->
<!-- audience: developers | researchers | end-users -->
<!-- tone: technical | conversational | formal -->