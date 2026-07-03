# AI Agent Guidelines: mkk digital-playground

This file provides context and conventions for AI coding agents working in the `digital-playground` codebase. 
The project is built on **Nuxt 4**, **Vue 3**, **TypeScript**, **Tailwind CSS**, and **Nuxt UI**.

## 🏗️ Architecture & Project Structure

- **`app/`**: Contains the frontend Nuxt application (`components`, `pages`, `composables`, `layouts`, app-only utilities).
- **`shared/`**: Contains framework-agnostic code that is shared between the Nuxt app and Nitro server, such as common schemas, types, constants, and pure helpers. These follow a **barrel export pattern** at `shared/utils/types/index.ts`, `shared/utils/schemas/index.ts`, and `shared/utils/constants/index.ts`.
- **`server/`**: Responsible for Nitro backend API routes, handlers, and server-only utilities.

*Place utilities or schemas in `shared/` only when they are used by both app and server, or are intentionally safe for both runtimes. Use `app/` for frontend-only code and `server/` for backend-only code.*

## 🧩 Component & Coding Patterns

- **Vue Composition API**: Use `<script setup lang="ts">` at the top of the file, above the `<template>`.
- **Nuxt UI Integration**: The project heavily relies on Nuxt UI components (e.g., `<UHeader>`, `<UPageHero>`, `<UPageSection>`). Do not build custom UI elements from scratch if a Nuxt UI equivalent already exists.
- **Icons**: Utilize the `@iconify-json` bundles via UI components. Use `i-lucide-*` for general icons and `i-simple-icons-*` for brand logos.
- **Auto-imports**: Lean on Nuxt's auto-import feature for composables and utilities. Business logic inside `.vue` files should be extracted to local composables (e.g., `useNavItems`).

## ✍️ Code Style & Conventions

- **Formatting**: Governed by Prettier (`100` print width, single quotes, 2-space tabs, disabled trailing commas). Use single quotes for strings in TypeScript.
- **Linting**: `@nuxt/eslint` is used. We explicitly enforce `commaDangle: 'never'` and `braceStyle: '1tbs'`.
- **Dates & Locales**: When formatting dates or numbers, prefer the `de-DE` locale (e.g., `new Date().toLocaleString('de-DE')`). 

## 🛠️ Developer Workflow

The main commands you should know and use when verifying changes:

- **Start Dev Server**: `npm run dev`
- **Format Code**: `npm run format` (run this after introducing or modifying files).
- **Lint Code**: `npm run lint`
- **Type Checking**: `npm run type-check` (always verify there are no TypeScript errors).
- **Clean Environment**: `npm run clean` (nukes `.nuxt`, `node_modules`, and lockfiles if the build acts up).

## Deployment
The project is automatically deployed to Vercel on every push to the `main` branch.

