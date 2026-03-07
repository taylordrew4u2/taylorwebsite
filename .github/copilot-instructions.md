# Copilot instructions for this project

This is an existing production-style website. Do not rebuild it from scratch unless explicitly requested.

Priorities:
- Preserve the current frontend design and behavior
- Prefer refactoring over replacement
- Make all major site content editable by a non-technical admin
- Avoid hardcoding content in components when it should be editable
- Favor clear admin UX over developer convenience

Admin UX standards:
- Use plain-English field labels
- Add helper text for non-obvious fields
- Group related fields into sections/tabs
- Support media upload and replacement
- Support repeatable collections where needed
- Add validation with understandable error messages
- Keep field names and content models intuitive
- Minimize required technical knowledge for editing
- Prefer predictable, maintainable content structures

When changing the codebase:
- First audit where content is hardcoded
- Reuse existing architecture where possible
- Keep changes incremental
- Explain which files changed and why
- State what content is editable after each implementation step
