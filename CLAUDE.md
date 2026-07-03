# Claude Code Instructions: mkk digital-playground

This repository uses Nuxt 4, Vue 3, TypeScript, Tailwind CSS, and Nuxt UI.

## Architecture

- `app/`: Nuxt frontend application code, including components, pages, composables, layouts, and frontend-only utilities.
- `shared/`: Framework-agnostic code shared between the Nuxt app and Nitro server, such as schemas, types, constants, and pure helpers. Use barrel exports at `shared/utils/types/index.ts`, `shared/utils/schemas/index.ts`, and `shared/utils/constants/index.ts`.
- `server/`: Nitro backend API routes, handlers, and server-only utilities.

Place utilities or schemas in `shared/` only when they are used by both app and server, or are intentionally safe for both runtimes. Use `app/` for frontend-only code and `server/` for backend-only code.

## Vue and Nuxt conventions

- Use `<script setup lang="ts">` at the top of Vue files, above the `<template>`.
- Prefer Nuxt UI components such as `UHeader`, `UPageHero`, and `UPageSection` before creating custom UI elements.
- Use Iconify icon classes through Nuxt UI components.
- Use `i-lucide-*` for general icons.
- Use `i-simple-icons-*` for brand icons.
- Use Nuxt auto-imports for composables and utilities.
- Extract business logic from `.vue` files into local composables where appropriate, for example `useNavItems`.

## Code style

- Prettier controls formatting.
- Use 100 character print width.
- Use single quotes in TypeScript.
- Use 2-space indentation.
- Do not use trailing commas.
- ESLint is configured through `@nuxt/eslint`.
- Respect `commaDangle: 'never'` and `braceStyle: '1tbs'`.
- Use `de-DE` when formatting dates or numbers unless a feature explicitly needs another locale.

## Verification workflow

After changing files, run:

```bash
npm run format     # Auto-format all files with Prettier
npm run lint       # Check for ESLint violations
npm run type-check # Check for TypeScript errors
```

## Deployment
The project is automatically deployed to Vercel on every push to the `main` branch.
