# Issue tracker

Issues and specs live in GitHub Issues for `hvnxdr/team-os`.
Use the `gh` CLI inside this repo, or pass `--repo hvnxdr/team-os`.

## Operations

- Create an issue with `gh issue create --title "..." --body-file <file>`.
- Read an issue with `gh issue view <number> --comments`.
- List issues with `gh issue list --state open --json number,title,body,labels,comments`.
- Comment with `gh issue comment <number> --body-file <file>`.
- Apply or remove labels with `gh issue edit <number> --add-label "..."` or `--remove-label "..."`.
- Close an issue with `gh issue close <number> --comment "..."`.

For multiline bodies, write the exact text to a temporary file and use
`--body-file`. Fetch labels as well as comments when evaluating an issue.

When a skill says "publish to the issue tracker", create a GitHub issue.
When it says "fetch the relevant ticket", read the issue and its comments.

## Pull requests and triage

PRs as a request surface: no.

If this flag changes to yes, triage external pull requests using the same
labels and states as issues. Use `gh pr view`, `gh pr diff`, `gh pr list`,
`gh pr comment`, `gh pr edit`, and `gh pr close`.

Include authors with association `CONTRIBUTOR`, `FIRST_TIME_CONTRIBUTOR`,
or `NONE`. Exclude `OWNER`, `MEMBER`, and `COLLABORATOR`.

GitHub shares issue and pull request numbers. For an ambiguous reference,
try `gh pr view <number>`, then `gh issue view <number>`.

## Wayfinding

Use one issue labelled `wayfinder:map` for the map. Its body contains
Notes, Decisions-so-far, and Fog.

Link child tickets as GitHub sub-issues. If sub-issues are unavailable,
add a task list to the map and `Part of #<map>` to each child.
Use `wayfinder:research`, `wayfinder:prototype`, `wayfinder:grilling`,
or `wayfinder:task` to identify the ticket type.

Record blockers with GitHub issue dependencies:

`gh api --method POST repos/hvnxdr/team-os/issues/<child>/dependencies/blocked_by -F issue_id=<blocker-db-id>`

Get the blocker's numeric database ID with:

`gh api repos/hvnxdr/team-os/issues/<number> --jq .id`

If dependencies are unavailable, add `Blocked by: #<number>` to the child.
A ticket is unblocked when all blockers are closed.

Select the first open, unassigned, unblocked child in map order.
Use `issue_dependencies_summary.blocked_by` to check open blockers,
or inspect the fallback references.

Claim a ticket with `gh issue edit <number> --add-assignee @me`.
To resolve it, comment with the answer, close it, and append a brief
answer and ticket link to the map's Decisions-so-far.
