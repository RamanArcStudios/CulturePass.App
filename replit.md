# CulturePass

## Overview
CulturePass is a mobile-first community platform for the Kerala/Malayalee diaspora in Australia. It serves as an Express.js backend that provides:
- A landing page with QR code for Expo Go mobile app preview
- REST API endpoints for events, organisations, businesses, artists, perks, orders, memberships, and more
- PostgreSQL database with Drizzle ORM
- User authentication with bcrypt and express-session

## Architecture
- **Runtime**: Node.js 20 with TypeScript (tsx)
- **Backend**: Express.js server on port 5000
- **Database**: PostgreSQL with Drizzle ORM
- **Schema**: Defined in `shared/schema.ts`, imported via `@shared/schema` path alias
- **Frontend**: Landing page served from `server/templates/landing-page.html`; the actual mobile app uses Expo/React Native (not built on server)

## Project Structure
```
server/           - Express server code
  index.ts        - Main server entry point
  routes.ts       - API route definitions
  db.ts           - Database connection (Drizzle + pg)
  storage.ts      - Data access layer
  seed.ts         - Database seeder
  stripeClient.ts - Stripe integration (optional)
  templates/      - HTML templates (landing page)
shared/
  schema.ts       - Drizzle schema definitions
app/              - Expo/React Native app screens
components/       - React Native components
lib/              - Client-side utilities
scripts/          - Build scripts for Expo static builds
```

## Running
- Development: `NODE_ENV=development npx tsx --tsconfig tsconfig.json server/index.ts`
- The server binds to `0.0.0.0:5000`

## Database
- Uses Replit's built-in PostgreSQL
- Schema push: `npx drizzle-kit push`
- Seed: `npx tsx --tsconfig tsconfig.json server/seed.ts`

## Key Dependencies
- express, express-session, connect-pg-simple
- drizzle-orm, drizzle-kit, drizzle-zod
- bcryptjs, jsonwebtoken, stripe (optional)
- tsx (TypeScript execution)
