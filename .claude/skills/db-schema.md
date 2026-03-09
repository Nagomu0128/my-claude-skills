---
description: Design or modify database schemas with Prisma or Drizzle ORM. Use when the user wants to create database models, relations, or migrations.
---

# Database Schema Design

## Instructions

When working with database schemas:

1. **Detect the ORM**: Check if the project uses Prisma (`prisma/schema.prisma`) or Drizzle (`drizzle.config.ts` / `db/schema.ts`).

2. **Prisma pattern**:
   ```prisma
   model User {
     id        String   @id @default(cuid())
     email     String   @unique
     name      String?
     posts     Post[]
     createdAt DateTime @default(now())
     updatedAt DateTime @updatedAt
   }
   ```
   - After schema changes: `npx prisma db push` (dev) or `npx prisma migrate dev` (with migration)
   - Generate client: `npx prisma generate`

3. **Drizzle pattern**:
   ```tsx
   import { pgTable, text, timestamp, uuid } from "drizzle-orm/pg-core";

   export const users = pgTable("users", {
     id: uuid("id").primaryKey().defaultRandom(),
     email: text("email").notNull().unique(),
     name: text("name"),
     createdAt: timestamp("created_at").defaultNow().notNull(),
   });
   ```
   - After changes: `npx drizzle-kit push` or `npx drizzle-kit generate`

4. **Schema design principles**:
   - Use `cuid()` or `uuid` for IDs (not auto-increment for distributed systems)
   - Always include `createdAt` and `updatedAt` timestamps
   - Define proper relations and foreign keys
   - Add indexes on frequently queried columns
   - Use `@unique` constraints where business logic requires it

5. **Naming**: Use `PascalCase` for Prisma models, `camelCase` for Drizzle table variables, `snake_case` for actual column/table names.
