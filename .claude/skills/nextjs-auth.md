---
description: Implement authentication flows in Next.js. Use when the user wants to add login, signup, session management, or protected routes.
---

# Next.js Authentication

## Instructions

When implementing auth:

1. **Detect auth library**: Check for NextAuth.js / Auth.js (`auth.ts`, `next-auth`), Clerk, Supabase Auth, or custom JWT.

2. **Auth.js (NextAuth v5) pattern**:
   ```tsx
   // auth.ts
   import NextAuth from "next-auth";

   export const { handlers, signIn, signOut, auth } = NextAuth({
     providers: [...],
     callbacks: {
       authorized({ auth, request }) {
         return !!auth?.user;
       },
     },
   });
   ```

3. **Protected pages** (Server Component):
   ```tsx
   import { auth } from "@/auth";
   import { redirect } from "next/navigation";

   export default async function ProtectedPage() {
     const session = await auth();
     if (!session) redirect("/login");
     // ...
   }
   ```

4. **Protected API routes**:
   ```tsx
   import { auth } from "@/auth";

   export async function GET() {
     const session = await auth();
     if (!session) {
       return NextResponse.json({ error: "Unauthorized" }, { status: 401 });
     }
     // ...
   }
   ```

5. **Security checklist**:
   - Never expose tokens/secrets to the client
   - Validate sessions on every protected request
   - Use CSRF protection for mutations
   - Set secure cookie flags in production
   - Implement rate limiting on auth endpoints
