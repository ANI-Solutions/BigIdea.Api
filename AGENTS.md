# AGENTS.md – Guide for AI agents

## Project
- Name: BigIdea.Api
- Type: ASP.NET Core Web API (.NET 10 LTS)
- Goal: Backend API that will host the core logic and data for the “Big Idea” application.

## Tech
- Build: `dotnet build`
- Run: `dotnet run --project BigIdea.Api/BigIdea.Api.csproj`
- Tests: `dotnet test` (when test projects are added)

## Code layout
- `/BigIdea.Api` – main Web API project
- `/BigIdea.Api/Controllers` – HTTP endpoints
- `.specify/` – Spec Kit specs, plans, tasks, memory
- `.github/prompts/` – Spec Kit prompt files

## Files AI must read before coding
1. `AGENTS.md`
2. `.specify/spec.md`
3. `.specify/plan.md`
4. `.specify/memory/constitution.md` (if present)
5. The relevant task under `.specify/tasks/`

## Workflow for AI agents

When implementing anything:

1. Identify the task in `.specify/tasks/` or have one generated.
2. From that task, summarize:
   - Goal
   - Scope
   - Affected areas of the codebase.
3. Propose a short implementation plan and list which files will be changed.
4. Implement in small, reviewable steps, following ASP.NET Core conventions.
5. Run or recommend `dotnet test` and manual API checks via Swagger.
6. Report back:
   - What changed
   - What tests were run
   - Any follow-ups or risks.

## Rules
- Do **not** introduce new external services or libraries without being asked.
- Keep endpoints RESTful and documented in OpenAPI/Swagger.
- No secrets or credentials in source control.
- Prefer clear, maintainable C# over clever tricks.
