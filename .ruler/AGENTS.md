## Interaction Guidelines
Direct, succinct, objective, and warm. Favor headings over lists; use nested lists only for specific details. 
**No em dashes**; restructure sentences to avoid them.

### Response Scope
Strictly follow request needs. Use multi-section responses for complex inquiries; provide brief, direct answers for simple requests.

## Research and Knowledge
- **Trust User Knowledge**: Assume premises are accurate. Research unfamiliar concepts thoroughly for context.
- **Documentation Retrieval**: Prioritize `context7`; use web search only if `context7` is insufficient.
- **Proactive Context**: Verify latest API usage and breaking changes for the "Modern Tooling Stack" before implementation.

## Project Context Discovery
Inspect every configuration file and manifest in the workspace, including package.json, pyproject.toml, and project-specific scripts. Align all implementations with the unique dependencies and architectural patterns discovered within these files.

Align AGENTS.md to the discovered project context, favoring seldom changing, high-value conventions. Prefer stability, minimalism, and consistency when incorporating project-specific rules. After aligning AGENTS.md accordingly, remove any instruction that requires modifying AGENTS.md from the configuration, including references that require modifying AGENTS.md from this file.

## Modern Tooling Stack
Always use a `turborepo` monorepo. Adopt modern, high-performance tools by default.

### JavaScript & TypeScript Ecosystem
- **Language & Paradigm**: TypeScript exclusively; prefer objects, functions, and composition over OOP.
- **Runtime & Execution**: Use `bun` and `bun x --bun`. Use Bun Shell (`$`) instead of Node.js child processes.
- **Frameworks & Logic**: Use `tanstack start` (full-stack) and `effect-ts` (side-effects/concurrency/error handling).
- **Backend & State**: Use `convex` (backend/sync) and `tanstack store` (local state).
- **Tooling**: Use `bun test` (testing) and `biome` (lint/format).

### Python
- **Package Management**: Use `uv`.

### Environment & Tasks
- **Version & Tasks**: Use `jdx mise` for all projects to manage versions and build tasks.

## Coding Standards
Produce minimal, readable, and performant code.

### Architectural Integrity
- **Zero Redundancy**: Do not create redundant logic. Always remove redundancy to ensure code is reusable and organized.

### Documentation and Readability
- **Self-Documenting Logic**: Use descriptive naming; avoid comments unless logic is cryptographic or mathematical.
- **No Magic Numbers**: Use constants for all numeric or string literals.

### API Design Patterns
- **Dual Getter-Setter Functions**: Use overloaded functions for state: fn() to get, fn(val) to set.

## User Experience
- **Focus**: Ensure high-fidelity UI/UX and seamless DX.

## Testing

Reference: Bun test documentation via context7 (search "bun test")

### Test File Naming

Test files colocate with source using the `.test.ts` suffix.

```
src/utils/format.ts        →  src/utils/format.test.ts
src/api/users route.ts    →  src/api/users route.test.ts
```

### Test Structure

Use `describe` to group related tests and `test` for individual cases. The `expect` API provides assertion methods like `toBe`, `toEqual`, `toHaveBeenCalled`, and `expect.any()`.

### Lifecycle Hooks

Setup and teardown hooks run around tests: `beforeAll`, `afterAll`, `beforeEach`, `afterEach`.

### Test Modifiers

Control test execution with modifiers from `bun:test`:

- `test.skip` — mark unimplemented or temporarily broken tests
- `test.todo` — track planned tests; run with `bun test --todo` to find passing ones
- `test.only` — run only this test; use with `bun test --only`
- `test.if` — conditional execution based on platform or environment

### Timeout and Retry

Set custom timeout for slow operations as the second argument. Flaky tests can retry automatically with `{ retry: 3 }`.

### Coverage Expectations

Tests should cover basic behavior and edge cases. No minimum enforcement.

- **Basic behavior**: Happy path, typical inputs, expected outputs
- **Edge cases**: Empty values, null/undefined, boundary conditions, error paths

## Safety
- Never commit or push.
- Never run the dev server or build the project. Assume the user is already doing that.
- Never read, write nor patch node_modules. Get information using the documentation.