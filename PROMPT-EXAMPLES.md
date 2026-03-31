# Prompt Examples

These examples make the agent system more useful in day-to-day VS Code work.

## First run
```text
@dev-expert Help me bootstrap this project for future work.
```

## Build a feature
```text
@dev-expert #codebase Add a password reset flow that matches existing API patterns.
```

## Fix a bug
```text
@bugfixer #problems #terminalLastCommand Fix the failing login timeout behavior.
```

## Review a diff
```text
@code-reviewer #changes Review today’s diff for correctness, test gaps, and naming issues.
```

## Security check
```text
@security #file Audit this endpoint for auth, injection, and secret handling.
```

## Test writing
```text
@test-writer #changes Add or update tests for the logic changed in this diff.
```

## Full implementation flow
```text
@dev-expert #changes #problems #terminalLastCommand Finish this task cleanly, then review security and missing tests.
```
