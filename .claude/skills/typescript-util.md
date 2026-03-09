---
description: Create TypeScript utility types, helpers, or shared functions. Use when the user wants to add utility functions, type helpers, or shared logic.
---

# TypeScript Utility Creator

## Instructions

When creating TypeScript utilities:

1. **Location**: Place in `lib/` or `utils/` directory based on project convention.

2. **Type-first approach**:
   - Define types/interfaces before implementation
   - Use generics for reusable utilities
   - Prefer `type` over `interface` for utility types; use `interface` for object shapes that may be extended
   - Export types alongside functions

3. **Common patterns**:

   **Zod schema + inferred type**:
   ```tsx
   import { z } from "zod";

   export const userSchema = z.object({
     id: z.string(),
     name: z.string(),
     email: z.string().email(),
   });

   export type User = z.infer<typeof userSchema>;
   ```

   **Type-safe fetch wrapper**:
   ```tsx
   export async function fetcher<T>(url: string, options?: RequestInit): Promise<T> {
     const res = await fetch(url, options);
     if (!res.ok) throw new Error(`HTTP ${res.status}`);
     return res.json() as Promise<T>;
   }
   ```

4. **Naming conventions**:
   - Files: `kebab-case.ts`
   - Types/interfaces: `PascalCase`
   - Functions/variables: `camelCase`
   - Constants: `UPPER_SNAKE_CASE` for true constants, `camelCase` for config objects

5. **Keep utilities pure** - avoid side effects, make them easily testable.

6. **Add JSDoc** only for exported public APIs that aren't self-documenting.
