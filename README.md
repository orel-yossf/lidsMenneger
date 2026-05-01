# lidsMenneger

Full-stack monorepo with Angular frontend, NestJS backend, and a shared types package.

## Structure

```
lidsMenneger/
  frontend/   Angular 21 app
  backend/    NestJS 11 API
  shared/     Shared TypeScript types (consumed by both)
```

## Quickstart

```bash
# install all workspace dependencies
npm install

# build shared types (needed once before first run, and after any change in shared/)
npm run build:shared

# run the apps (in two terminals)
npm run dev:backend     # NestJS on http://localhost:3000
npm run dev:frontend    # Angular on http://localhost:4200
```

## Sharing types between front and back

Both apps import from `@lidsmenneger/shared`:

```typescript
import { User, CreateUserDto } from '@lidsmenneger/shared';
```

The package is a real npm workspace, so it resolves through `node_modules/` — no path-mapping setup required.

When you change anything in `shared/src/`, rebuild it:

```bash
npm run build:shared
# or run a watcher in a separate terminal:
npm run dev:shared
```

## Scripts (run from repo root)

| Script | What it does |
|---|---|
| `npm install` | Install all workspace deps (hoisted to root `node_modules/`) |
| `npm run build:shared` | Build the shared types package |
| `npm run dev:shared` | Watch-build the shared package |
| `npm run dev:frontend` | Start Angular dev server |
| `npm run dev:backend` | Start NestJS dev server |
| `npm run build` | Production build of shared, backend, and frontend |
