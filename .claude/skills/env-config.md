---
description: Set up or manage environment variables and configuration in Next.js. Use when the user needs to add env vars, configure services, or manage different environments.
---

# Environment & Configuration

## Instructions

When managing environment variables:

1. **File hierarchy** (Next.js loads in order, later overrides earlier):
   - `.env` — all environments
   - `.env.local` — local overrides (gitignored)
   - `.env.development` — dev only
   - `.env.production` — production only

2. **Naming convention**:
   - Server-only: `DATABASE_URL`, `API_SECRET` (no prefix)
   - Client-exposed: `NEXT_PUBLIC_` prefix required (e.g., `NEXT_PUBLIC_API_URL`)
   - **Never expose secrets with `NEXT_PUBLIC_`**

3. **Type-safe env** — Create a validation file:
   ```tsx
   // env.ts
   import { z } from "zod";

   const envSchema = z.object({
     DATABASE_URL: z.string().url(),
     NEXT_PUBLIC_APP_URL: z.string().url(),
     API_KEY: z.string().min(1),
   });

   export const env = envSchema.parse(process.env);
   ```

4. **When adding new env vars**:
   - Add to `.env.example` (with placeholder values, never real secrets)
   - Add to the Zod validation schema
   - Document what the variable is for

5. **Security**:
   - Never commit `.env.local` or files with real secrets
   - Verify `.gitignore` includes `.env*.local`
   - For production: use platform env management (Vercel, etc.)
