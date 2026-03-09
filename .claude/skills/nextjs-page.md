---
description: Create a new Next.js page or route with TypeScript and Tailwind CSS. Use when the user wants to add a new page, route, or layout to their Next.js app.
---

# Next.js Page/Route Generator

## Instructions

When creating a new Next.js page or route:

1. **Determine the routing structure** - Ask if not clear:
   - Is this an App Router page (`app/`) or Pages Router (`pages/`)?
   - Default to App Router (`app/` directory) unless the project uses Pages Router.

2. **File conventions** (App Router):
   - `page.tsx` for route pages
   - `layout.tsx` for shared layouts
   - `loading.tsx` for loading UI (use Skeleton from shadcn)
   - `error.tsx` for error boundaries
   - `not-found.tsx` for 404 pages
   - Route groups with `(groupName)/`
   - Dynamic routes with `[param]/`

3. **Template structure**:
   - Use `"use client"` directive only when the component needs interactivity (event handlers, hooks, browser APIs)
   - Default to Server Components
   - Use TypeScript with proper type annotations
   - Use Tailwind CSS for styling
   - Import shadcn/ui components when UI elements are needed

4. **Metadata** - Always include metadata for pages:
   ```tsx
   import type { Metadata } from "next";

   export const metadata: Metadata = {
     title: "Page Title",
     description: "Page description",
   };
   ```

5. **Data fetching** - Prefer:
   - Server Components with `async/await` for server-side data
   - `use` hook or React Query for client-side data
   - Server Actions for mutations

6. **Use shadcn/ui components** for common UI patterns:
   - `Card` for content containers
   - `Button` for actions
   - `Skeleton` for loading states
   - `Badge`, `Avatar`, etc. as appropriate
