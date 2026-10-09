# KNA
<img width="2322" height="1304" alt="image" src="https://github.com/user-attachments/assets/2de72525-58a5-4958-8310-233e6191ebc4" />
<img width="2052" height="1157" alt="image" src="https://github.com/user-attachments/assets/3e375497-c8a9-4afc-9939-d90546c6b3f6" />
<img width="2669" height="1484" alt="image" src="https://github.com/user-attachments/assets/b9d4cdbc-e06e-4ec0-94ce-a0155937f33d" />
<img width="2313" height="1291" alt="image" src="https://github.com/user-attachments/assets/6e12e200-22d0-47ff-a9bc-01f2b1b4fd7e" />
<img width="2254" height="1243" alt="image" src="https://github.com/user-attachments/assets/14142b7c-9893-4516-8e1e-c9914a899ae2" />
<img width="2322" height="1297" alt="image" src="https://github.com/user-attachments/assets/0789f630-dd75-49dd-9f42-9efa60bf892c" />
<img width="2314" height="1306" alt="image" src="https://github.com/user-attachments/assets/4f8e1335-a1b7-4140-80a1-8973404502e3" />
<img width="2326" height="1305" alt="image" src="https://github.com/user-attachments/assets/1048c293-8692-43f7-935a-f25a4103d80c" />
<img width="2322" height="1305" alt="image" src="https://github.com/user-attachments/assets/accbb3fd-5fd6-4d10-935e-77226d6748d6" />
<img width="2318" height="1299" alt="image" src="https://github.com/user-attachments/assets/663d8aa6-b195-470a-a156-be04a81e8145" />
<img width="2314" height="1296" alt="image" src="https://github.com/user-attachments/assets/c39a121d-1edb-420b-a237-f701dfe9cadb" />
<img width="2316" height="1299" alt="image" src="https://github.com/user-attachments/assets/d1e5f605-8369-4d84-8e25-bf30c60340de" />
Community-owned circular tourism ecosystem for the Ê Đê people of Đắk Lắk, Vietnam.
BKI 2026 · Team NEXUS.

This is a monorepo (npm workspaces):

```
apps/
  web/   React + Vite frontend (the original prototype, unchanged in spirit)
  api/   Express + TypeScript + Prisma backend
```

See [`docs/development-plan.md`](docs/development-plan.md) for the phased build
plan this repo follows (Phase 0 → Phase 3).

## Getting started

Requires **PostgreSQL** on `localhost:5432` — see
[`apps/api/README.md`](apps/api/README.md) for setup.

```bash
createdb kna_dev && createdb kna_test        # once

cp apps/api/.env.example apps/api/.env
npm install           # installs both workspaces
npm run db:generate   # generate the Prisma client
npm run db:migrate    # apply migrations
npm run db:seed       # load demo data (wipes kna_dev; refuses non-local targets)
npm run dev:api       # http://localhost:4000
npm run dev:web       # http://localhost:5173, in a second terminal
```

Demo accounts all use the password `changeme123` — `guest@example.kna`,
`ami.hbia@example.kna` (host and Committee chair),
`coordinator@example.kna`.

## Why this structure

The frontend (`apps/web`) is the existing prototype, moved as-is — same
components, same design system, no rewrite. `apps/api` is a small
Express + Prisma service that Phase 1 wired the frontend's mock arrays up to.

Development, CI and production all run on PostgreSQL (Neon in staging and
production), so they agree on constraint behaviour. Development previously
ran on SQLite and then SQL Server; the history and why it matters are in
the "One engine everywhere" section of `apps/api/README.md`.
