---
description: Create Next.js API routes (Route Handlers). Use when the user wants to build API endpoints, webhooks, or server-side handlers.
---

# Next.js API Route Handler

## Instructions

When creating API route handlers:

1. **File location**: `app/api/[route]/route.ts`

2. **Use the Web API standard** (App Router Route Handlers):
   ```tsx
   import { NextRequest, NextResponse } from "next/server";

   export async function GET(request: NextRequest) {
     return NextResponse.json({ data });
   }

   export async function POST(request: NextRequest) {
     const body = await request.json();
     return NextResponse.json({ result }, { status: 201 });
   }
   ```

3. **Supported HTTP methods**: `GET`, `POST`, `PUT`, `PATCH`, `DELETE`, `HEAD`, `OPTIONS`

4. **Input validation**:
   - Validate all request body/params with Zod schemas
   - Return proper HTTP status codes (400 for validation errors, 401 for unauthorized, 404 for not found, 500 for server errors)

5. **Error handling pattern**:
   ```tsx
   try {
     // logic
   } catch (error) {
     console.error("Descriptive context:", error);
     return NextResponse.json(
       { error: "User-friendly message" },
       { status: 500 }
     );
   }
   ```

6. **Dynamic route params**:
   ```tsx
   export async function GET(
     request: NextRequest,
     { params }: { params: Promise<{ id: string }> }
   ) {
     const { id } = await params;
   }
   ```

7. **Type safety**: Define request/response types. Use Zod for runtime validation.
