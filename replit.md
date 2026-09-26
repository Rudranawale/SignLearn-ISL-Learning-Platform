# SignLearn

SignLearn is a warm, beginner-friendly Indian Sign Language learning platform with visual lessons, webcam practice, feedback states, and progress tracking.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/signlearn/src/App.tsx` — frontend routes, local demo data, auth flow, lesson/practice/progress screens
- `artifacts/signlearn/src/index.css` — SignLearn theme tokens, typography, motion, and shared utility styling
- `attached_assets/` — original product brief and visual reference supplied for the build

## Architecture decisions

- The first MVP is frontend-first and uses localStorage for demo identity and progress so every learning state is usable before the CV/API services are connected.
- Practice supports both real browser camera permission and a simulated preview path, keeping the product demonstrable in environments without camera access.
- The visual system uses a warm cream, deep green, apricot, and sage palette with display typography to keep the product approachable rather than dashboard-like.

## Product

- Landing page that explains the learning journey and introduces five starter signs.
- Login/register screens with demo access and guarded learning routes.
- Dashboard, lesson, practice, and progress views for Hello, Thank You, Water, Help, and Please.
- Local practice feedback includes hand detection stages, confidence, correct/retry states, XP, streak, and badges.

## User preferences

The product should stay friendly, accessible, warm, and focused on one obvious primary action per screen.

## Gotchas

- The standalone Vite build needs `PORT` and `BASE_PATH`; the managed workflow supplies them automatically.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
