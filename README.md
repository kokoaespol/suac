# SUAC – University Club Administration System

SUAC is a web platform for managing student clubs at ESPOL.
It is built with **SvelteKit**, **Drizzle ORM**, and **PostgreSQL**, with modern tooling for development, testing, and deployment.

## **Tech Stack**

- **Frontend:** [SvelteKit](https://kit.svelte.dev/), TailwindCSS
- **UI Components:** Bits UI, Lucide Svelte
- **Backend:** Node.js with [Drizzle ORM](https://orm.drizzle.team/)
- **Database:** PostgreSQL
- **Auth:** JWT / OAuth / BetterAuth (TBD)
- **Testing:** Vitest
- **Dev Tools:** ESLint, Prettier, TypeScript

## **Repository Scripts**

The main `package.json` scripts:

```bash
# Development
pnpm run dev          # Start local dev server (Vite + SvelteKit)
pnpm run build        # Build production bundle
pnpm run preview      # Preview production build

# Code quality
pnpm run check        # Type-check and Svelte-check
pnpm run format       # Format code with Prettier
pnpm run lint         # Run Prettier check + ESLint

# Tests
pnpm run test         # Run all unit tests (Vitest)
pnpm run test:unit    # Run unit tests in development
```

## **Database Setup**

This project uses **PostgreSQL** with Drizzle ORM.

1. Make sure Docker is installed and running.
2. Start the local database:

   ```bash
   pnpm db:start
   ```

3. Apply schema migrations:

   ```bash
   pnpm db:push
   ```

4. (Optional) Open **Drizzle Studio** to inspect the schema:

   ```bash
   pnpm db:studio
   ```
