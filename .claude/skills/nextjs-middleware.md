---
description: Create or modify Next.js middleware for auth, redirects, or request processing. Use when the user wants to add middleware, protect routes, handle redirects, or process requests before they reach the page.
---

# Next.js Middleware

## Instructions

When creating Next.js middleware:

1. **File location**: `middleware.ts` at the project root (same level as `app/`).

2. **Basic structure**:
   ```tsx
   import { NextRequest, NextResponse } from "next/server";

   export function middleware(request: NextRequest) {
     // Logic here
     return NextResponse.next();
   }

   export const config = {
     matcher: [
       // Match specific routes, exclude static files and API
       "/((?!_next/static|_next/image|favicon.ico).*)",
     ],
   };
   ```

3. **Common patterns**:

   **Auth protection**:
   ```tsx
   const token = request.cookies.get("session")?.value;
   if (!token && request.nextUrl.pathname.startsWith("/dashboard")) {
     return NextResponse.redirect(new URL("/login", request.url));
   }
   ```

   **Redirects**:
   ```tsx
   if (request.nextUrl.pathname === "/old-path") {
     return NextResponse.redirect(new URL("/new-path", request.url));
   }
   ```

   **Adding headers**:
   ```tsx
   const response = NextResponse.next();
   response.headers.set("x-custom-header", "value");
   return response;
   ```

4. **Performance**: Middleware runs on every matched request — keep it fast. Avoid heavy computation or external API calls.

5. **Matcher config**: Always define a `matcher` to avoid running middleware on static assets.
