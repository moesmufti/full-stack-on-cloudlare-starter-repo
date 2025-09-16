# AGENTS.md - Development Guide

## Commands
- **Build packages**: `pnpm run build-package` (builds @repo/data-ops)
- **Dev frontend**: `pnpm run dev-frontend` (user-application on port 3000)
- **Dev data service**: `pnpm run dev-data-service` (Wrangler dev with remote bindings)
- **Test**: `pnpm --filter <workspace> run test` (e.g., `pnpm --filter user-application run test`)
- **Single test**: `pnpm --filter <workspace> run test -- <test-file>` (Vitest pattern matching)
- **Deploy staging**: `pnpm run stage:deploy-frontend` or `pnpm run stage:deploy-data-service`
- **Deploy production**: `pnpm run production:deploy-frontend` or `pnpm run production:deploy-data-service`

## Architecture
- **Monorepo**: PNPM workspace with `apps/` (user-application, data-service) and `packages/` (data-ops)
- **Frontend**: React + TanStack Router + Vite, Cloudflare Pages deployment
- **Backend**: Hono API on Cloudflare Workers with D1 database
- **Shared**: @repo/data-ops package provides database queries, auth, and Zod schemas
- **Testing**: Vitest with `@cloudflare/vitest-pool-workers` for Workers, React Testing Library for frontend

## Code Style
- **TypeScript**: Strict mode, use `type` imports when possible
- **React**: Functional components, hooks, TanStack Query for data fetching
- **Imports**: Relative paths for local files, absolute paths with tsconfig paths
- **Components**: kebab-case file names, PascalCase component names
- **Database**: Drizzle ORM with D1, schema exports from data-ops package
- **Auth**: Better-auth with Stripe integration
- **Styling**: Tailwind CSS v4, Radix UI components, shadcn/ui patterns
