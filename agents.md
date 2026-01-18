# Agent Development Guidelines

This document provides instructions for AI coding agents (GitHub Copilot, Claude Code, Cursor, etc.) working on this repository.

## Purpose

This repository is a generic Supabase SaaS starter template designed for Next.js App Router applications.

**Technology Stack:**
- Next.js (App Router)
- Supabase (authentication, database, storage)
- Tailwind CSS (styling)
- shadcn/ui (UI components)
- Stripe (payment integration via Supabase)
- Cloudinary (media management)

**Intent:**
This is a foundation template for building SaaS applications. It is not a complete application. Agents should maintain its generic, reusable nature and avoid implementing specific business features.

## Guard Rails

AI agents must strictly follow these rules when making changes:

### Security
- Never commit secrets, API keys, tokens, or credentials to the repository
- Never access or modify production data
- Always use environment variables for sensitive configuration
- Validate and sanitize all user inputs

### Change Management
- No breaking changes without a documented migration plan
- All changes must be small, focused, and reviewable
- Each pull request should address a single concern
- Avoid refactoring unrelated code

### Dependencies
- Do not add new dependencies without explicit justification
- Document why each new dependency is necessary
- Prefer standard library solutions when possible
- Check for security vulnerabilities before adding packages

### UI and Styling
- Only use shadcn/ui components and Tailwind CSS for styling
- Do not introduce alternative UI libraries or CSS frameworks
- Maintain consistent design patterns across components

### Architecture
- Use Server Components by default in Next.js App Router
- Only use Client Components when necessary (interactivity, hooks, browser APIs)
- Follow existing patterns for data fetching and state management
- Maintain separation of concerns (UI, business logic, data access)

### Documentation
- Update documentation before making code changes
- Keep README.md current with setup instructions
- Document architectural decisions in `/docs/adr/`
- Explain complex logic with inline comments when necessary

## Agent Workflow

Follow this workflow for every task:

1. **Read Relevant Documentation**
   - Review `/docs/` for context
   - Check existing code patterns
   - Understand the current architecture

2. **Update Documentation First**
   - Create or update relevant documentation
   - Document architectural decisions if applicable
   - Update README.md if setup process changes

3. **Implement Minimal Code**
   - Make the smallest change that solves the problem
   - Follow existing code style and patterns
   - Write clear, self-documenting code

4. **Keep Changes Scoped**
   - Stay focused on the specific task
   - Avoid feature creep
   - Do not refactor unrelated code

5. **Summarize Changes**
   - Explain what was changed and why
   - Note any trade-offs or limitations
   - Highlight any follow-up work needed

## Project Structure

The repository follows this structure:

```
/app                    - Next.js App Router pages and layouts
/components             - React components
  /ui                   - shadcn/ui components
/lib                    - Utility functions and shared logic
  /supabase             - Supabase client configuration
/docs                   - Project documentation
  /adr                  - Architecture Decision Records
/public                 - Static assets
```

### Directory Guidelines

**`/app`**: Contains all Next.js routes, layouts, and server actions. Use Server Components by default.

**`/components`**: Reusable React components. Organize by feature or type. Keep UI components in `/components/ui`.

**`/lib`**: Shared utilities, helpers, and configurations. Keep Supabase-related code in `/lib/supabase`.

**`/docs`**: All project documentation. Use Markdown format. Keep ADRs in `/docs/adr`.

## Definition of Done

Before considering any task complete, verify:

- [ ] Code builds successfully (`npm run build`)
- [ ] Linting passes without errors (`npm run lint`)
- [ ] TypeScript type checking passes (`npx tsc --noEmit`)
- [ ] No secrets or sensitive data committed
- [ ] Documentation is updated and accurate
- [ ] Changes are minimal and focused
- [ ] Code follows existing patterns and conventions
- [ ] Commit message clearly describes the change

## Agent Skills

This repository uses Vercel Agent Skills to provide AI agents with best practices and guidelines.

**Installation:** Agent skills are installed per developer using:
```bash
npx add-skill vercel-labs/agent-skills
```

**Included Skills:**
- `vercel-react-best-practices` - React and Next.js performance optimization
- `web-design-guidelines` - Web design and UX principles

Agent skill directories (`.claude/`, `.cursor/`, `.github/skills/`, etc.) are local configurations and should not be committed to the repository.
