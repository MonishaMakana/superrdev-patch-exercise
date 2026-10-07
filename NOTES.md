# Notes

## Summary

- Grouped the text-match alternatives so archived tasks are excluded and status applies to both title and description matches in the Java query, H2 SQL reference, and Oracle reference.
- Fixed the task hook so a failed request exits loading state and a subsequent request clears the old error.

## Not changed

Pagination still loads and filters all matching tasks in memory before slicing. This is acceptable for the small seed dataset, but it will not scale; database-level paging and a matching count query should be the next backend improvement.

## Biggest remaining risk

Search requests have no cancellation or ordering protection, so a slower response for an older query can replace results for a newer query.

## Tools

I used GitHub Copilot to inspect the code and reason about the query behavior, then verified the filter issue against the running seeded API and checked the final behavior locally.