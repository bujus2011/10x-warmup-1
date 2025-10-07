# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

10xDevs.pl warmup repository - a training environment for learning AI-assisted development workflows. The repository contains TypeScript exercises designed to practice collaboration with LLM tools like Claude, Cursor, and GitHub Copilot.

## Development Commands

```bash
npm install              # Install dependencies
npm test                 # Run Vitest test suite (all *.test.ts files)
npx vitest --watch      # Run tests in watch mode for development
```

## Code Architecture

### Core Exercise Structure

- **banking/**: Primary exercise implementing a banking system
  - `types.ts` - TypeScript interfaces for BankAccount, WithdrawalRequest, WithdrawalResult, WithdrawalError
  - `banking.ts` - Implementation of banking operations (createAccount, processWithdrawal)
  - `banking.test.ts` - Vitest test suite covering account creation and withdrawal validation
  - `banking-spec.md` - Business requirements in Polish, serving as source of truth for implementation
  - `prompts/` - LLM prompts for analysis and implementation tasks

### Supporting Directories

- **prompts/**: Template prompts for LLM collaboration
  - `decomposer.md` / `decomposer_pl.md` - Breaking down complex problems into LLM-friendly steps
  - `unblocker.md` / `unblocker_pl.md` - Unblocking strategies for development obstacles
- **agent-sandbox/**: Practice files for exercises
  - `Dashboard.tsx` - Intentionally broken React component for hooks validation practice
  - `example.js` - JavaScript examples
- **charts/**: Contains `request.md` with Mermaid sequence diagram examples for full-stack request flows

## Coding Standards

### TypeScript Guidelines
- Use TypeScript 5.8+ with strict mode enabled (see `tsconfig.json`)
- Prefer `const` over `let` and `var`
- Avoid `any` type - use explicit type annotations
- Follow two-space indentation, trailing commas, and double-quoted imports

### Testing Approach
- Vitest is the testing framework
- Test files follow pattern `<feature>.test.ts` alongside implementation
- Use `describe`/`it` nesting for test organization
- Explicitly assert error codes and messages (e.g., `INVALID_AMOUNT`, `INSUFFICIENT_FUNDS`)
- Spec-first development: `banking-spec.md` defines business rules, tests enforce them

### Commit Conventions
- Follow Conventional Commits pattern: `feat:`, `fix:`, `chore:`, `doc:`
- Example: `feat: add overdraft guard`, `chore: update prompts`
- Keep commits focused on single changes

## Special Features

### Cursor Integration
- **Custom Rules**: `.cursor/rules/hooks.mdc` defines React Hooks validation rules (Rules of Hooks enforcement)
- **Slash Commands** in `.cursor/commands/`:
  - `1-mock-data.md` - Generate mock JSON data
  - `4-hooks-verifier.md` - Validate React components against hooks.mdc rules
  - Additional commands for dependency checking, code review, and API exercises

### LLM Collaboration Patterns
- **Spec-Driven**: Banking exercise demonstrates spec → tests → implementation flow
- **Prompt Templates**: Use prompts/ directory for structured LLM interactions
- **Bilingual Support**: English and Polish versions (\_pl suffix) for international teams
- **Error Code Design**: Explicit error types (WithdrawalError) for predictable validation flows

## Exercise Workflow

1. **Banking System Implementation**: Start with `banking-spec.md`, read `banking.test.ts`, implement in `banking.ts`
2. **Test Analysis**: Use `banking/prompts/analysis.md` to evaluate which tests exceed spec requirements
3. **Mermaid Diagrams**: Practice creating sequence diagrams per `charts/request.md`
4. **Hooks Validation**: Apply `.cursor/rules/hooks.mdc` to fix `agent-sandbox/Dashboard.tsx`
